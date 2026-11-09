# Calculadora de média: disciplinas técnicas

Uma página web simples para descobrir **quanto você precisa tirar** nas disciplinas técnicas para fechar o semestre com a média desejada (por padrão, **6,0**).

Tudo roda no navegador, em um único arquivo. Não precisa instalar nada nem ter internet.

## O que ela faz

- **Calculadora do semestre:** você informa as notas que já tem e a página mostra quanto precisa tirar no que falta para atingir a média.
- **Possibilidades de notas:** você monta combinações de Integrada, Entrega e Prova e vê a nota da Continuada e se ela bate a meta.
- **Tabela de combinações:** para cada nota de Prova, mostra o mínimo necessário em Integrada e Entrega para fechar a meta.

## Como usar

1. Baixe o arquivo `calculadora-media.html`.
2. Abra no navegador (dois cliques já funcionam).
3. Preencha as notas que já saíram e deixe em branco o que ainda não foi lançado.
4. Se quiser outra média, altere o campo **Média desejada**.

Aceita vírgula ou ponto nas notas (`7,5` ou `7.5`), sempre de 0 a 10.

## Regras de cálculo

A página segue o sistema de notas das disciplinas técnicas.

**Média da disciplina**

| Continuada | Peso |
|---|---|
| AC1 | 25% |
| AC2 | 35% |
| AC3 | 40% |

A nota **Integrada** da disciplina repete a média das continuadas, então existe um único cálculo.

**Nota de cada Continuada**

| Componente | Peso |
|---|---|
| Entregas | 30% |
| Integrada (questionário no Moodle, sem consulta) | 30% |
| Prática (com ou sem consulta) | 40% |

**Fórmulas**

```
Nota da AC   = Entregas × 0,3 + Integrada × 0,3 + Prática × 0,4
Média final  = AC1 × 0,25 + AC2 × 0,35 + AC3 × 0,40
Nota necessária = (meta − pontos já garantidos) ÷ peso ainda em aberto
```

## Exemplo

Possibilidade com Integrada 6, Entrega 8 e Prova 5:

```
6 × 0,3 + 8 × 0,3 + 5 × 0,4 = 1,8 + 2,4 + 2,0 = 6,2
```

A nota da Continuada é **6,2**, então atinge a meta de 6,0.

## Como interpretar o resultado

- **0,00:** você já garantiu a média, mesmo tirando zero no resto.
- **Mais de 10:** não dá mais para atingir a meta. A página mostra o máximo possível.
- **Valor entre 0 e 10:** é a nota média que você precisa em todas as notas pendentes. Você pode tirar menos em uma e compensar em outra.

Dica: a Prova pesa mais (0,4 por ponto) que Entrega e Integrada (0,3 por ponto). Cada ponto a menos na Prova pede cerca de 1,33 ponto a mais em Entrega ou Integrada.

## Estrutura do projeto

```
calculadora-media.html   # HTML, CSS e JavaScript no mesmo arquivo
README.md
```

## Tecnologias

- HTML5
- CSS3 (layout responsivo e modo claro/escuro automático)
- JavaScript puro, sem bibliotecas

## Limitações

- Os pesos estão fixos no código, conforme a tabela de notas. Se a regra da sua disciplina mudar, ajuste `PESOS` e os atributos `data-w` no HTML.
- A página não aplica regras extras, como nota mínima por Continuada ou recuperação. Confira o regulamento da sua turma.
- Nada é salvo: ao fechar ou recarregar a página, as notas digitadas são perdidas.

## Ideias para evoluir

- Salvar as notas no navegador (`localStorage`)
- Permitir pesos diferentes por disciplina
- Exportar as possibilidades em PDF ou imagem