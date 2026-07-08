## Descrição
Você recebeu uma imagem JPG aparentemente comum. Há algo escondido dentro do arquivo, fora de vista. Sua tarefa é descobrir a carga oculta (payload) e extrair a flag.

## Dicas
Baixe a imagem JPG e leia seus metadados.

## Resolução do Desafio
A primeira coisa a se fazer é baixar a imagem (disponível na pasta caso queira ver). Como a dica falava para ler metadados usei a ferramenta do exiftool: uma ferramenta que permite ler metadados da imagem que já tinha conhecimento de desafios de OSINT anteriores. Lendo a imagem, obtemos a seguinte informação: **"Comment : c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9"**.
A primeira vista, pode parecer que a flag é esse já que os códigos de alguns CTFs e até do próprio  Bandit são assim, mas é importante saber que isso é um código em Base64, que quando traduzido revela "steghide:cEF6endvcmQ=". Ele é dividido em duas partes: o "steghide" da primeira parte fala sobre a ferramentas que devemos usar para completar o desafio: steghide é uma ferramente que permite ler os metadados e arquivos encriptados em uma imagem. A segunda parte continua sendo um código em base64, que quando decodificado novamente fica "pAzzword", que é provavelmente a senha que iremos usar quando extrairmos o arquivo com o steghide. Usando o steghide e extraindo a imagem, ele nos da o arquivo "flag.txt", que quando aberto revela:
 **picoCTF{h1dd3n_1n_1m4g3_92f08d7c}**

## Conceitos Aprendidos
- Aprender a ler metadados em imagens usando ferramentas especializadas (steghide e exiftool)
- Relembrar conceitos de base64

## Dificuldades
Admito que minha maior dificuldade foi em usar as flags do steghide. Tive que errar algumas vezes até aprender que "steghide --info img.jpeg" não entregava muita coisa, e que "steghide --extract -sf img.jpeg" era o comando certo.
