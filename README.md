# Jankenpo em container

> [!WARNING]
> A ordem dos passos importa: nao pule a preparacao do ambiente.


Projeto simples: uma imagem de servidor web servindo arquivos estáticos, com toda a lógica do jogo rodando no navegador, em JavaScript.

Passos:

A receita da imagem está no arquivo de build na raiz do repositório.

Para gerar a imagem a partir da receita (no Linux, o comando precisa de privilégio):

```
docker build . -t jankenpo-imagem
```

A receita parte de uma imagem enxuta de servidor web:

```
from nginx
```

Depois copia os arquivos da pasta `files` para dentro do diretório servido:

```
copy files/* /usr/share/nginx/html/
copy files/assets /usr/share/nginx/html/assets/
```

Para subir a imagem criada:

```
sudo docker run -p 8000:80 jankenpo-imagem
```

O que acontece ali:
- usamos a imagem marcada no passo de build
- mapeamos a porta 8000 da máquina para a 80 dentro do container

Abrindo o endereço local na porta mapeada, a página do jogo aparece:

![tela do jogo](demo.png)

# Vídeo com a execução

Há uma gravação mostrando o container subindo e o jogo sendo usado.