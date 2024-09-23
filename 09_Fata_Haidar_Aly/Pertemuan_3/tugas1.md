import java.math.BigInteger;
import java.security.SecureRandom;

public class DiffieHellman {
    private BigInteger p; // bilangan prima
    private BigInteger g; // generator
    private BigInteger privateKeyA; // kunci pribadi Alice
    private BigInteger privateKeyB; // kunci pribadi Bob
    private BigInteger publicKeyA; // kunci publik Alice
    private BigInteger publicKeyB; // kunci publik Bob
    private BigInteger sharedSecretA; // kunci rahasia Alice
    private BigInteger sharedSecretB; // kunci rahasia Bob

    public DiffieHellman(int bitLength) {
        SecureRandom random = new SecureRandom();
        p = BigInteger.probablePrime(bitLength, random); // menghasilkan bilangan prima
        g = new BigInteger("2"); // memilih generator
        privateKeyA = new BigInteger(bitLength, random); // kunci pribadi Alice
        privateKeyB = new BigInteger(bitLength, random); // kunci pribadi Bob
        publicKeyA = g.modPow(privateKeyA, p); // kunci publik Alice
        publicKeyB = g.modPow(privateKeyB, p); // kunci publik Bob
        sharedSecretA = publicKeyB.modPow(privateKeyA, p); // kunci rahasia Alice
        sharedSecretB = publicKeyA.modPow(privateKeyB, p); // kunci rahasia Bob
    }

    public void displayKeys() {
        System.out.println("Bilangan Prima (p): " + p);
        System.out.println("Generator (g): " + g);
        System.out.println("Kunci Pribadi Alice: " + privateKeyA);
        System.out.println("Kunci Pribadi Bob: " + privateKeyB);
        System.out.println("Kunci Publik Alice: " + publicKeyA);
        System.out.println("Kunci Publik Bob: " + publicKeyB);
        System.out.println("Kunci Rahasia Alice: " + sharedSecretA);
        System.out.println("Kunci Rahasia Bob: " + sharedSecretB);
    }

    public static void main(String[] args) {
        DiffieHellman dh = new DiffieHellman(512); // panjang bit 512
        dh.displayKeys(); // menampilkan langkah-langkah
    }
}
