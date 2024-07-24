
```
class ModeloIA:
    def __init__(self, nome, desempenho, velocidade, custo, capacidades):
        self.nome = nome
        self.desempenho = desempenho
        self.velocidade = velocidade
        self.custo = custo
        self.capacidades = capacidades
    
    def __str__(self):
        return self.nome

modelos = [
    ModeloIA('Claude 3 Opus', 10, 10, 10, ['automatizar tarefas', 'pesquisa e desenvolvimento']),
    ModeloIA('Claude 3 Haiku', 10, 10, 10, ['resposta rápida e capacidade de resposta quase instantânea', 'motores de chatbots de lojas', 'moderação de conteúdo', 'processamento de tarefas mais básicas', 'velocidade', 'resumo de dados não estruturados']),
    ModeloIA('Claude 3 Sonnet', 10, 10, 10, ['raciocínio cuidadoso', 'processamento de dados', 'aplicações de vendas', 'extração de texto de imagens', 'equilíbrio ideal entre inteligência e velocidade', 'codificação', 'recuperação de informações']),
]

def recomendar_modelo(caracteristicas): 
    modelo_recomendado = None
    capacidades_usuario = [capacidade.lower() for capacidade in caracteristicas['Capacidades']]

    for modelo in modelos:
        capacidades_modelo = [capacidade.lower() for capacidade in modelo.capacidades]
        
        if any(capacidade in capacidades_modelo for capacidade in capacidades_usuario):
            if modelo_recomendado is None or modelo.desempenho > modelo_recomendado.desempenho:
                modelo_recomendado = modelo

    return modelo_recomendado if modelo_recomendado else "Nenhum modelo encontrado."

def gerar_explicacao(modelo, caracteristicas):
    if isinstance(modelo, ModeloIA):
        explicacao = f"O {modelo.nome} é o modelo recomendado."
        return explicacao
    else:
        return modelo

def obter_caracteristicas():
    caracteristicas = {}
    caracteristicas['Desempenho'] = int(input("Digite o desempenho desejado (0-10): "))
    caracteristicas['Velocidade'] = int(input("Digite a velocidade desejada (0-10): "))
    caracteristicas['Custo'] = int(input("Digite o custo máximo permitido (0-10): "))
    capacidades = input("Digite as capacidades desejadas separadas por vírgula: ").split(',')
    caracteristicas['Capacidades'] = [capacidade.strip() for capacidade in capacidades]
    return caracteristicas

caracteristicas_entrada = obter_caracteristicas()
melhor_modelo = recomendar_modelo(caracteristicas_entrada)
explicacao = gerar_explicacao(melhor_modelo, caracteristicas_entrada)

print(explicacao)
```
