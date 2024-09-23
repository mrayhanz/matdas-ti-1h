# Algoritma Diffie-Hellman

def power_mod(base, exponent, modulus):
    """Fungsi untuk menghitung (base^exponent) mod modulus dengan metode eksponensial cepat."""
    result = 1
    base = base % modulus
    while exponent > 0:
        if (exponent % 2) == 1:  # Jika exponent ganjil
            result = (result * base) % modulus
        exponent = exponent >> 1  # Membagi exponent dengan 2
        base = (base * base) % modulus
    return result

def diffie_hellman():
    # Inisialisasi parameter
    p = 97  # Bilangan prima
    g = 5   # Basis

    # Pemilihan kunci pribadi
    x = 36  # Kunci pribadi Alice
    y = 58  # Kunci pribadi Bob

    # Menghitung kunci publik
    X = power_mod(g, x, p)  # Kunci publik Alice
    Y = power_mod(g, y, p)  # Kunci publik Bob

    print(f"Kunci Publik Alice (X): {X}")
    print(f"Kunci Publik Bob (Y): {Y}")

    # Menghitung kunci rahasia bersama
    K_Alice = power_mod(Y, x, p)  # Kunci rahasia Alice
    K_Bob = power_mod(X, y, p)     # Kunci rahasia Bob

    print(f"Kunci Rahasia Bersama Alice (K): {K_Alice}")
    print(f"Kunci Rahasia Bersama Bob (K): {K_Bob}")

# Menjalankan fungsi
if __name__ == "__main__":
    diffie_hellman()
