import tkinter as tk
from tkinter import messagebox

inventario = []

def forjar_heroi():
    nome = campo_nome.get()
    if nome:
        nome_personagem.set(nome)
        status_label.config(text=f"⚔ {nome} está pronto para a jornada!")
        btn_adicionar.config(state="normal")
        btn_usar.config(state="normal")
        btn_ver.config(state="normal")
        label_heroi.config(text=f"⚔ Herói: {nome}")
    else:
        messagebox.showwarning("Aviso", "Digite um nome para seu herói.")

def adicionar_item():
    item = campo_item.get()
    tipo = tipo_item.get()
    if item and tipo:
        inventario.append({"nome": item, "tipo": tipo})
        status_label.config(text=f"🎒 Item '{item}' ({tipo}) adicionado ao inventário.")
        campo_item.delete(0, tk.END)
    else:
        messagebox.showwarning("Aviso", "Preencha o nome e tipo do item.")

def ver_inventario():
    if not inventario:
        status_label.config(text="📭 Inventário vazio.")
        return
    texto = "\n".join([f"{i+1}. {item['nome']} ({item['tipo']})" for i, item in enumerate(inventario)])
    messagebox.showinfo("Inventário", texto)

def usar_item():
    if not inventario:
        status_label.config(text="🕳️ Nenhum item disponível.")
        return
    item_usado = inventario.pop(0)
    status_label.config(text=f"✨ {item_usado['nome']} ({item_usado['tipo']}) foi usado!")

# Cores em tons de marrom claro
cor_fundo = "#C7AF98"
cor_texto = "#4B423B"
cor_botao = "#9E826D"
cor_texto_botao = "#2e1f10"
cor_destaque = "#745848"

# Janela principal
janela = tk.Tk()
janela.title("⚔︎ Relíquias de Valderia")
janela.geometry("500x530")
janela.configure(bg=cor_fundo)

# Estilo
fonte_titulo = ("Georgia", 22, "bold italic")
fonte_texto = ("Georgia", 13, "bold italic")

nome_personagem = tk.StringVar(value="Desconhecido")

# Título
tk.Label(janela, text="📜 Relíquias de Valderia ⚔", font=fonte_titulo, fg=cor_destaque, bg=cor_fundo).pack(pady=15)

# Nome do personagem
tk.Label(janela, text="Nome do Herói:", font=fonte_texto, fg=cor_texto, bg=cor_fundo).pack()
campo_nome = tk.Entry(janela, font=("Georgia", 12))
campo_nome.pack(pady=5)
tk.Button(janela, text="Forjar Herói", command=forjar_heroi,
          font=fonte_texto, bg=cor_botao, fg=cor_texto_botao).pack(pady=5)

label_heroi = tk.Label(janela, text="⚔ Herói: N/A", font=fonte_texto, fg=cor_texto, bg=cor_fundo)
label_heroi.pack(pady=10)

# Entrada de itens
tk.Label(janela, text="Nome do Item:", font=fonte_texto, fg=cor_texto, bg=cor_fundo).pack()
campo_item = tk.Entry(janela, font=("Georgia", 12))
campo_item.pack(pady=5)

tk.Label(janela, text="Tipo de Item:", font=fonte_texto, fg=cor_texto, bg=cor_fundo).pack()

# Criando o Menu suspenso para as opções
tipo_item = tk.StringVar(value="Espada")

# Função para selecionar o tipo de item
def selecionar_tipo(tipo):
    tipo_item.set(tipo)

# Criando o menu suspenso com as opções
menu = tk.Menu(janela, tearoff=0, bg=cor_fundo, fg=cor_texto)
tipos = ["Espada", "Poção", "Armadura", "Amuleto", "Pergaminho"]
for tipo in tipos:
    menu.add_command(label=tipo, command=lambda t=tipo: selecionar_tipo(t))

# Função para mostrar o menu ao clicar no botão
def mostrar_menu(event):
    menu.post(event.x_root, event.y_root)

# Botão que exibe o menu com as opções
btn_tipo_item = tk.Button(janela, text="Itens", font=fonte_texto, 
                          bg=cor_botao, fg=cor_texto_botao, width=20,
                          activebackground=cor_botao)  # Aqui definimos a cor quando pressionado
btn_tipo_item.pack(pady=5)
btn_tipo_item.bind("<Button-1>", mostrar_menu)

# Exibindo o valor selecionado
tk.Label(janela, text="Tipo de Item Selecionado:", font=fonte_texto, fg=cor_texto, bg=cor_fundo).pack()
tk.Label(janela, textvariable=tipo_item, font=fonte_titulo, fg=cor_texto, bg=cor_fundo).pack(pady=5)

# Botões
btn_adicionar = tk.Button(janela, text=" 📜 Adicionar ao Inventário", command=adicionar_item,
                          font=fonte_texto, bg=cor_botao, fg=cor_texto_botao, state="disabled")
btn_adicionar.pack(pady=5)

btn_ver = tk.Button(janela, text="📜 Ver Inventário", command=ver_inventario,
                    font=fonte_texto, bg=cor_botao, fg=cor_texto_botao, state="disabled")
btn_ver.pack(pady=5)

btn_usar = tk.Button(janela, text="⚔ Usar Item", command=usar_item,
                     font=fonte_texto, bg=cor_botao, fg=cor_texto_botao, state="disabled")
btn_usar.pack(pady=5)

# Status e feedback
status_label = tk.Label(janela, text="", wraplength=460,
                        font=fonte_texto, fg=cor_texto, bg=cor_fundo)
status_label.pack(pady=20)

janela.mainloop()
