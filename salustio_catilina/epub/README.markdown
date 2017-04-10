Criando ebooks
==============

* Atualizar arquivos do livro (papel)
* Rodar livro .tex
* Mudar pdf para LIVRO.pdf
* Criar ou revisar INPUTS.tex
* Criar branch 
  * git checkout -b ebook
* Copiar arquivos do template \git\ebook em \ebook (prisória)
  * cp ../../ebook/Makefile . 
* make copy
* Criar novo ISBN * Preencher Makefile * Comandos
* [verificar se capa está colorida e com o nome e formato _capa.png_]
* make capa-internet
* make capa
* make credits 
* Acertar na mão o credit (marcas de corte)
* make hifens 
* make 
* sh repair.sh 
* [abrir com sigil e verificar]
* make check
* make metadados
* make rename 
* make entrega
* Git "pronto!" 
* make matriz (Se houve muita alteração nos arquivos, copiar arquivos para ebook original)
