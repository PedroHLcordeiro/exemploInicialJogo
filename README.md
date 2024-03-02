# exemploInicialJogo
jogo de enigmas
import random

def criptografar_mensagem(mensagem, chave):
    mensagem_criptografada = ""
    for char in mensagem:
        if char.isalpha():
            char_criptografado = chr((ord(char) + chave - ord('A')) % 26 + ord('A'))
            mensagem_criptografada += char_criptografado
        else:
            mensagem_criptografada += char
    return mensagem_criptografada

def descriptografar_mensagem(mensagem_criptografada, chave):
    return criptografar_mensagem(mensagem_criptografada, -chave)

def iniciar_jogo():
    print("Bem-vindo ao jogo de resolução de enigmas!")
    mensagem_original = "DESVENDE A PISTA SECRETA"
    chave = random.randint(1, 25)
    mensagem_criptografada = criptografar_mensagem(mensagem_original, chave)

    print("Você encontrou uma mensagem criptografada:")
    print(mensagem_criptografada)

    tentativas = 3
    while tentativas > 0:
        palpite = input("Digite sua tentativa de descriptografia: ").upper()

        if palpite == descriptografar_mensagem(mensagem_criptografada, chave):
            print("Parabéns! Você desvendou a mensagem secreta.")
            break
        else:
            tentativas -= 1
            print(f"Tentativa incorreta. Você tem {tentativas} tentativas restantes.")

    if tentativas == 0:
        print("Você não conseguiu desvendar a mensagem. O jogo acabou.")

if __name__ == "__main__":
    iniciar_jogo()

