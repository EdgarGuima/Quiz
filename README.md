# Quiz
import tkinter as tk
from tkinter import messagebox

perguntas = [
    "Qual seleção venceu a Copa do Mundo de 2018?",
    "Quem é o maior artilheiro da história das Copas do Mundo?",
    "Qual jogador é conhecido como 'O Fenômeno'?",
    "Qual time venceu a Champions League em 2020?",
    "Quantas vezes o Brasil venceu a Copa do Mundo?",
    "Quem é considerado o 'Rei do Futebol'?",
    "Em que ano o Brasil sediou a Copa do Mundo?",
    "Quem foi o capitão da França na Copa do Mundo de 1998?",
    "Qual jogador é famoso pela 'mão de Deus'?",
    "Quantos times disputam a Premier League?"
]

opcoes = [
    ["França", "Croácia", "Brasil", "Alemanha"],
    ["Pelé", "Maradona", "Ronaldo", "Miroslav Klose"],
    ["Messi", "Cristiano Ronaldo", "Ronaldo", "Ronaldinho"],
    ["Liverpool", "Bayern de Munique", "PSG", "Barcelona"],
    ["3", "4", "5", "6"],
    ["Pelé", "Zico", "Romário", "Ronaldo"],
    ["2006", "2014", "2018", "2002"],
    ["Zidane", "Deschamps", "Henry", "Platini"],
    ["Pelé", "Maradona", "Zico", "Ronaldinho"],
    ["18", "20", "22", "24"]
]

respostas = ["França", "Miroslav Klose", "Ronaldo", "Bayern de Munique", "5", "Pelé", "2014", "Deschamps", "Maradona", "20"]

indice_atual = 0
pontos = 0

def proxima_pergunta():
    global indice_atual, pontos
    if variavel_resposta.get() == respostas[indice_atual]:
        messagebox.showinfo("Resultado", "Você acertou!")
        pontos += 1
    else:
        messagebox.showinfo("Resultado", "Você errou!")
    
    indice_atual += 1
    if indice_atual < len(perguntas):
        exibir_pergunta()
    else:
        messagebox.showinfo("Resultado Final", f"Você acertou {pontos} de {len(perguntas)} perguntas!")
        janela.quit()

def exibir_pergunta():
    pergunta_label.config(text=perguntas[indice_atual])
    for i in range(4):
        botoes_resposta[i].config(text=opcoes[indice_atual][i], value=opcoes[indice_atual][i])
    variavel_resposta.set(None)

janela = tk.Tk()
janela.title("Quiz de Futebol")

pergunta_label = tk.Label(janela, text=perguntas[indice_atual], font=("Arial", 14))
pergunta_label.pack(pady=20)

variavel_resposta = tk.StringVar()

botoes_resposta = []
for i in range(4):
    botao = tk.Radiobutton(janela, text="", variable=variavel_resposta, value="", font=("Arial", 12))
    botao.pack(anchor="w")
    botoes_resposta.append(botao)

botao_proximo = tk.Button(janela, text="Próxima", command=proxima_pergunta, font=("Arial", 12))
botao_proximo.pack(pady=20)

exibir_pergunta()

janela.mainloop()
