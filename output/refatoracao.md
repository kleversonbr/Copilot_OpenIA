# Refatoração de código fonte

## 💻 Objetivo
Testar a refatoração de código fonte em pyton, sugerindo melhorias.

## 📄 Prompt
Atue como um desenvolvedor de software pyton senior, e refatore o código abaixo considerando desempenho, velocidade de processamento e facilidade na leitura. Código disponível em input/codigo.md.

## 🛠️ Resultado

Claro, posso ajudar a refatorar o código para melhorar o desempenho, a velocidade de processamento e a facilidade de leitura. Aqui está o código refatorado:

```
class ModeloIA:
    def __init__(self, nome, desempenho, velocidade, custo, capacidades):
        self.nome = nome
        self.desempenho = desempenho
        self.velocidade = velocidade
        self.custo = custo
        self.capacidades = set(capacidade.lower() for capacidade in capacidades)
    
    def __str__(self):
        return self.nome

modelos = [
    ModeloIA('Claude 3 Opus', 10, 10, 10, ['automatizar tarefas', 'pesquisa e desenvolvimento']),
    ModeloIA('Claude 3 Haiku', 10, 10, 10, ['resposta rápida e capacidade de resposta quase instantânea', 'motores de chatbots de lojas', 'moderação de conteúdo', 'processamento de tarefas mais básicas', 'velocidade', 'resumo de dados não estruturados']),
    ModeloIA('Claude 3 Sonnet', 10, 10, 10, ['raciocínio cuidadoso', 'processamento de dados', 'aplicações de vendas', 'extração de texto de imagens', 'equilíbrio ideal entre inteligência e velocidade', 'codificação', 'recuperação de informações']),
]

def recomendar_modelo(caracteristicas): 
    capacidades_usuario = set(capacidade.lower() for capacidade in caracteristicas['Capacidades'])
    modelos_candidatos = [modelo for modelo in modelos if capacidades_usuario & modelo.capacidades]
    modelo_recomendado = max(modelos_candidatos, key=lambda modelo: modelo.desempenho, default=None)
    return modelo_recomendado if modelo_recomendado else "Nenhum modelo encontrado."

def gerar_explicacao(modelo):
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
explicacao = gerar_explicacao(melhor_modelo)

print(explicacao)

```
Aqui estão as principais mudanças que fiz:

- Converti as listas de capacidades em conjuntos para melhorar a velocidade de pesquisa durante a comparação de capacidades.
- Usei a função max com um argumento key para encontrar o modelo com o maior desempenho em uma única passagem, em vez de iterar várias vezes.
- Removi a necessidade de passar as características para a função gerar_explicacao, pois essa função não as usa.
