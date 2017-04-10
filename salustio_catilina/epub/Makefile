# ARQUIVOS
PADRAO = EBOOK
PDF = LIVRO.pdf
PAGINADECREDITOS = 2
TITULOEPUB = SALUSTIO
EXTENSAO = png
INTERNET = a-conjuracao-de-catilina
BISAC = HIS002020	
BISAC2= HIS002000	
WGS = 567
WGS2 = 553
THEMA = 1QBAR
THEMA2 = 1QBA
IDIOMAORIGINAL = Latim

##### METADATA
#--author-sort
#String to be used when sorting by author.

#--title
#Set the title.
TITLE = "A conjuração de Catilina"
TITLESORT = "conjuração de Catilina, A"

#--authors
#Set the authors. Multiple authors should be separated by ampersands.
AUTORS = "SALUSTIO"
AUTORSSORT = "SALUSTIO"
ORGANIZADOR = "Adriano Scatolin"
TRADUTOR = "Adriano Scatolin"

#--book-producer
#Set the book producer.
PRODUCER = "Editora Hedra"

#--comments
#Set the ebook description.
COMMENTS = "A «Conjuração de Catilina» relata o conjunto de eventos que constituíram o malogrado plano de Lúcio Sérgio Catilina (108--62) para se assenhorear do poder em Roma, no ano do consulado de Cícero, 63. Catilina, de família patrícia romana, provavelmente pretor  em 68, governador da província da África no intervalo de 67 a 66, tentara por duas vezes eleger-se cônsul, sem sucesso (64-63). Candidato ao consulado para o ano de 63, fora vencido por Cícero e Caio Antônio. Ao final desse ano, apoiado pela facção dos populares, candidata-se novamente ao mesmo cargo para o ano de 62, mas sofre outra derrota, desta vez para Lúcio Licínio Murena e Décimo Júnio Silano."

#--cover
#Set the cover to the specified file or URL
COVER = capa.png

#--isbn
#Set the ISBN of the book.
ISBN = 9788577154371
ISBN_IMPRESSO = 9788577153619

#--language
#Set the language.
LANGUAGE = "pt-BR"

#--pubdate
#Set the publication date.
DATE = 2015

#--publisher
#Set the ebook publisher.
PUBLISHER = Hedra

#--rating
#Set the rating. Should be a number between 1 and 5.
#
#--read-metadata-from-opf, -m
#Read metadata from the specified OPF file. Metadata read from this file will override any metadata in the source file.
#
#--series
#Set the series this ebook belongs to.
#SERIES = "Livros de Bolso"

#--series-index
#Set the index of the book in this series.
#
#--tags
#Set the tags for the book. Should be a comma separated list.
#TAGS = "História da imprensa, imprensa, Paulo Henrique Amorim, Conversa afiada, Vargas, Lacerda, Jucelino Kubitschek, mídia, Globo, Veja, Ditadura militar, repressão, 1964, golpe militar, Jornal do Brasil, TV brasileira, Tevê brasileira, Manual de redação, Manual de televisão, Fantástico"


all:
	-sh texrepair.sh
	hevea $(PADRAO).tex -o $(PADRAO).html
	sed -i 's/\<img src="CREDITOS\.png\>/\<img alt="Créditos" src="CREDITOS.png"\>/' EBOOK.html
#	ebook-convert $(PADRAO).html $(PADRAO).mobi --page-breaks-before / --toc-threshold 0 --level1-toc //h:h2 --level2-toc //h:h3 --level3-toc //h:h4 --cover ../capa.png 
	ebook-convert $(PADRAO).html $(PADRAO).mobi --title $(TITLE) --authors $(AUTORS) --comments $(COMMENTS) --publisher $(PUBLISHER) --rating 4 --book-producer $(PRODUCER) --language $(LANGUAGE) --author-sort $(AUTORSSORT) --title-sort $(TITLESORT) --isbn $(ISBN) --pubdate $(DATE) --series $(SERIES) --tags $(TAGS) --page-breaks-before / --toc-threshold 0 --level2-toc //h:h1 --level2-toc //h:h2 --level3-toc //h:h3 --cover $(COVER) 
	ebook-convert $(PADRAO).html $(PADRAO).epub --title $(TITLE) --authors $(AUTORS) --comments $(COMMENTS) --publisher $(PUBLISHER) --rating 4 --book-producer $(PRODUCER) --language $(LANGUAGE) --author-sort $(AUTORSSORT) --title-sort $(TITLESORT) --isbn $(ISBN) --pubdate $(DATE) --series $(SERIES) --tags $(TAGS) --page-breaks-before / --toc-threshold 0 --level2-toc //h:h1 --level2-toc //h:h2 --level3-toc //h:h3 --cover $(COVER) 

viewer:
	ebook-viewer EBOOK.epub

credits:
	pdftk $(PDF) cat $(PAGINADECREDITOS) output CREDITOS.pdf
	mogrify -format png CREDITOS.pdf
#	mogrify -shave 190x120 -gravity south -chop x200 -frame 30 CREDITOS.png	
#	mogrify -shave 190x120 -gravity south CREDITOS.png	
	mogrify -resize 601 CREDITOS.png

rename:
	cp $(PADRAO).epub $(TITULOEPUB).epub
	cp $(PADRAO).mobi $(TITULOEPUB).mobi
	cp $(PDF) $(TITULOEPUB).pdf
	zip $(TITULOEPUB).zip $(TITULOEPUB).*	
hifens:
	sed -i 's/"-/-/g' *.tex	
copy:
	cp ~/LATEX/git/ebook/EBOOK.tex .
	cp ~/LATEX/git/ebook/.gitignore .
	cp ~/LATEX/git/ebook/english.hva .
	cp ~/LATEX/git/ebook/repair.sh .
	cp ~/LATEX/git/ebook/texrepair.sh .
	cp ~/LATEX/git/ebook/README.markdown .
check:
	epubcheck $(PADRAO).epub
sigil:
	sigil $(PADRAO).epub
capa:
	#mogrify -type Grayscale $(COVER)
	mogrify -resize 601 $(COVER)
	cp $(COVER) $(TITULOEPUB).${EXTENSAO}
	mogrify -resize x2550 $(TITULOEPUB).${EXTENSAO}
	mogrify -format jpg $(TITULOEPUB).${EXTENSAO}
entrega:
	cp $(TITULOEPUB).epub /home/hipatia/Dropbox/EBOOKS/
	cp $(TITULOEPUB).mobi /home/hipatia/Dropbox/EBOOKS/
	cp $(TITULOEPUB).zip /home/hipatia/Dropbox/EBOOKS/
	cp $(TITULOEPUB).pdf /home/hipatia/Dropbox/EBOOKS/
	cp $(TITULOEPUB).txt /home/hipatia/Dropbox/EBOOKS/
	cp $(TITULOEPUB).jpg /home/hipatia/Dropbox/EBOOKS/
metadados:
	echo "TÍTULO:\t\t\t" $(TITLE) >  $(TITULOEPUB).txt
	echo "-----------------------------------------------------------" >>  $(TITULOEPUB).txt	
	echo "AUTOR:\t\t\t" $(AUTORS) >>  $(TITULOEPUB).txt	
	echo "-----------------------------------------------------------" >>  $(TITULOEPUB).txt	
	echo "ORGANIZADOR:" $(ORGANIZADOR) >>  $(TITULOEPUB).txt	
	echo "-----------------------------------------------------------" >>  $(TITULOEPUB).txt	
	echo "TRADUTOR:\t\t" $(TRADUTOR) >>  $(TITULOEPUB).txt	
	echo "-----------------------------------------------------------" >>  $(TITULOEPUB).txt	
	echo "ISBN:\t\t\t\t" $(ISBN) >>  $(TITULOEPUB).txt	
	echo "-----------------------------------------------------------" >>  $(TITULOEPUB).txt	
	echo "ISBN IMPRESSO:" $(ISBN_IMPRESSO) >>  $(TITULOEPUB).txt	
	echo "-----------------------------------------------------------" >>  $(TITULOEPUB).txt	
	echo "ANO:\t\t\t\t" $(DATE) >>  $(TITULOEPUB).txt	
	echo "-----------------------------------------------------------" >>  $(TITULOEPUB).txt	
	echo "TEXTO: " $(COMMENTS) >>  $(TITULOEPUB).txt	
	echo "-----------------------------------------------------------" >>  $(TITULOEPUB).txt	
	pdftk LIVRO.pdf dump_data | grep NumberOfPages >> $(TITULOEPUB).txt 
	echo "-----------------------------------------------------------" >>  $(TITULOEPUB).txt	
	echo "BISAC =" $(BISAC) >> $(TITULOEPUB).txt 
	echo "-----------------------------------------------------------" >>  $(TITULOEPUB).txt	
	echo "BISAC2 =" $(BISAC2) >> $(TITULOEPUB).txt 
	echo "-----------------------------------------------------------" >>  $(TITULOEPUB).txt	
	echo "WGS =" $(WGS) >> $(TITULOEPUB).txt 
	echo "-----------------------------------------------------------" >>  $(TITULOEPUB).txt	
	echo "WGS2 =" $(WGS2) >> $(TITULOEPUB).txt 
	echo "-----------------------------------------------------------" >>  $(TITULOEPUB).txt	
	echo "THEMA =" $(THEMA) >> $(TITULOEPUB).txt 
	echo "-----------------------------------------------------------" >>  $(TITULOEPUB).txt	
	echo "THEMA2 =" $(THEMA2) >> $(TITULOEPUB).txt 
	echo "-----------------------------------------------------------" >>  $(TITULOEPUB).txt	
	echo "IDIOMA ORIGINAL: " $(IDIOMAORIGINAL) >> $(TITULOEPUB).txt 
	echo "-----------------------------------------------------------" >>  $(TITULOEPUB).txt	

capa-internet:
	wget https://hedra.com.br/uploads/book/cover/$(INTERNET).${EXTENSAO}
	mv $(INTERNET).${EXTENSAO} $(COVER)
	mogrify -format png $(COVER)
atualiza:
	-cp Makefile ../ebook/
	-cp *.sh ../ebook/
	-cp EBOOK.tex ../ebook/	
clean:
	rm *.html *.htoc *.haux
matriz:
	-cp Makefile ~/LATEX/git/ebook	
	-cp repair.sh ~/LATEX/git/ebook	
	-cp EBOOK.tex ~/LATEX/git/ebook	
	-cp texrepair.sh ~/LATEX/git/ebook	
	-cp README.markdown ~/LATEX/git/ebook	
wgs:	
	evince /home/hipatia/Dropbox/EBOOKS/CLASSIFICACOES/WGS.pdf
thema:
	evince /home/hipatia/Dropbox/EBOOKS/CLASSIFICACOES/Thema.pdf
bisac:
	google-chrome https://www.bisg.org/complete-bisac-subject-headings-2014-edition
