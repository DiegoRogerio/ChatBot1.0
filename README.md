# ChatBot1.0

import tkinter as tk
from tkinter import messagebox
import subprocess
import sys

# Dados de sintomas, doenças e níveis de urgência
sintomas_doencas = {
    'febre, dor de cabeça, dor no corpo': ('Gripe', 'Moderada'),
    'tosse seca, falta de ar': ('COVID-19', 'Alta'),
    'dor abdominal, náusea, vômito': ('Gastrite', 'Moderada'),
    'dor no peito, falta de ar': ('Infarto', 'Alta'),
    'febre, calafrios, dor no peito': ('Pneumonia', 'Alta'),
    'dificuldade para respirar, cansaço': ('Asma', 'Alta'),
    'dor no estômago, sensação de queimação': ('Úlcera', 'Moderada'),
    'dor nas articulações, febre': ('Dengue', 'Moderada'),
    'dificuldade para respirar, tosse': ('COVID-19', 'Alta'),
    'calafrios, febre alta, dor nas costas': ('Malária', 'Alta'),
    'cansaço extremo, perda de peso, suores noturnos': ('Tuberculose', 'Alta'),
    'falta de apetite, perda de peso, dor abdominal': ('Hepatite', 'Alta'),
    'tontura, visão turva, dor no peito': ('Acidente Vascular Cerebral (AVC)', 'Alta'),
    'febre, dor nas articulações, erupções na pele': ('Zika', 'Moderada'),
    'vomito, febre, dor abdominal severa': ('Apendicite', 'Alta'),
    'dor nas costas, febre, dificuldade para urinar': ('Infecção urinária', 'Moderada'),
    'fadiga, palidez, falta de apetite': ('Anemia', 'Moderada'),
    'dificuldade para respirar, pressão no peito': ('Pneumotórax', 'Alta'),
    'sangramento nasal, dificuldade de coagulação': ('Leucemia', 'Alta'),
    'tontura, visão embaçada, dor de cabeça': ('Hipoglicemia', 'Moderada'),
    'dor forte no estômago, náusea, fezes escuras': ('Úlcera péptica', 'Alta'),
    'erupções cutâneas, febre, dor muscular': ('Sarampo', 'Moderada')
}

# Função para diagnosticar sintomas
def diagnose():
    sintomas = symptoms_entry.get().lower()
    
    # Loop para comparar os sintomas inseridos com as listas de sintomas
    for sintomas_lista, (doenca, urgencia) in sintomas_doencas.items():
        if all(sintoma in sintomas for sintoma in sintomas_lista.split(', ')):
            result_label.config(text=f"Doença: {doenca}\nUrgência: {urgencia}", fg="#4CAF50")
            return

    # Se não encontrar uma correspondência
    result_label.config(text="Sintomas não reconhecidos. Consulte um médico.", fg="#F44336")

# Criação da janela principal
root = tk.Tk()
root.title("Diagnóstico de Sintomas")

# Tamanho da janela
root.geometry("375x550")
root.configure(bg="#121212")

# Título com fonte personalizada
title_label = tk.Label(root, text="Chatbot de Diagnóstico", font=("Helvetica", 18, "bold"), bg="#121212", fg="#fff")
title_label.pack(pady=20)

# Campo para inserção de sintomas
symptoms_label = tk.Label(root, text="Digite seus sintomas (separados por vírgula):", font=("Helvetica", 12), bg="#121212", fg="#fff")
symptoms_label.pack(pady=10)

# Diminuindo o campo de entrada dos sintomas
symptoms_entry = tk.Entry(root, width=30, font=("Helvetica", 12), borderwidth=2, relief="solid", bg="#fff", fg="#333")
symptoms_entry.pack(pady=10)

# Botão para diagnóstico
diagnose_button = tk.Button(root, text="Diagnosticar", font=("Helvetica", 14), bg="#4CAF50", fg="#fff", relief="flat", command=diagnose)
diagnose_button.pack(pady=15, ipadx=10, ipady=8)

# Label para mostrar o resultado do diagnóstico
result_label = tk.Label(root, text="", font=("Helvetica", 14), bg="#121212", fg="#fff")
result_label.pack(pady=20)

# Iniciar a interface gráfica
root.mainloop()
