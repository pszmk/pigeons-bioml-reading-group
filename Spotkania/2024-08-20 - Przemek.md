#### task: target identification
1. pierwsza modalność leki - targety w co celują (białka) ma wiącać si z białkeim (inhibitować)
binarnie określone

bierzemy leki i satamy sie przyweidzieć co on targetuje
przewidywanie nowych targetów dla znanego leku

szukanie targetu i potem tworzenie leku, który inhibituje target

2. druga modalnoścć
gene expression signatures - różne znaczeni w zal od kontekstu

L1000 - podobne do perturbacji na single cell

aplikujemy perturbację (chemiczna-lek, genetyczna - wyłączanie genu (crusper))
mierzeenie ekspresji genów - mierzymy ekspresję prezd i po
wektor określa zmianę ekspresji

cell lines
perturbation
info what happens with expression (tretment - control)

cell line (zlepek komórek)

#### Cel generation of molecules with desired properties
smiles string - representation of chemical structure
modele wyrzucają sekwencje smilesów (atomy, wiązania itd)
to generujemy tokeny smiles
cały problem to jest model generatywny do smiles
- problem to dużo modeli

#### conditional geneeration
ograniczone modele, brane są po uwage stricte chemiczne warunki
są modele, które tworzą leki, które wywołują daną sygnaturę (zmianę w ekspresji)

use case: model który tworzy na podstawie synaturu molekółę (chcemy lek, który powoduje tą zmianę w ekspresji)

sygnatury nie są idealne - ale mowią mniej więcej co się dzieje w komórkach

sygnatury mogą być użyte:
- wygenerowanie  leku wywołującego odwrotną sygnaturę co choroba
- molekuła, która ma taką samą sygnaturę jak dany target (ta sama smiana w ekspresji co jak lek targetujący coś)
- molekuła o takiej samej sygnaturze

#### Pierwotnie
Opisanie generalnego modelu warunkowego. Zbiór dowolnej liczby warunków i różnej formy: sygnatura -> wektor, chemiczna cecha -> liczba w konsekwencji generujemy molekułę, już istniejące molekuły


morpohological dignatures - sygnatoru = co się zmieniło  z danych obrazowych

activity profiles - do czego się lubi przywiązywać

#### KK - output modelu to lista genów, które mogą być targetami leków

generacja molekuł, które spełniają wearunki
inspirowane ESM3 - tam wchodzą rózne modalności dot. białek
- na białko można różnie patrzeć: funkcja, struktura 3d, sekwencja|jest 7 różnych traków
- częćś jest maskowana i iteracyjne unmaskowana wszystko ze wszystkiego iteracyjnie

wiele modalności:
- targety leku (co zmienia lek, binarnie)
- smiles
- LINCS
- sygnatury (zbioru targetów)
- drug sensitivity (jak lek działa na komórki)

BOTTOMLINE
- ogólna metoda sprawdzona na molecule generation

dużo źródeł danych i różnych danych
znalezienie sprytnych modeli do fuzji multimodal na poziomie warunków

generowanie łątwych danych an początek


często nie obserwujemy całych danych - cała modalności jest niewidoczna - flexible
model może inputować

---
modalności
- smiles - łatwo dostępne (łatwo dostęþne na hf)
- sygnatury links - gene expressions links
- 20 k leków - tyle jest wektorów zmian ekspresji
- sensitvites - jak działa lek na komórki rakow (5 k leków jak działają na cell lines)
- chemiczne cechy można wygenerować dla smiles - można policzyć ground truth
zazwyczaj dla jednego warunku są robione, nie wiadomo jak dla fuzji wielu się bedzie robiło

trzeba wtybrać konretne benchmarki

MM
pomysł z KK
ile leków per condition, 
z perspektywy leków - zbiór informacji, nigdy nie jest pełna, pierwotny zamysł był taki, aby wykorzystać niekomnpletne waruni jako na słownik, dwa modelel niezależne: smiles i encoding, drugi transformer z priorem, prior funkcją warunków które znamy

KK - przetestowanie, sztucznie wygenerowanie dane, na mnist wygenerować funkcje

w single cell, różne datasety, maskowanie danych tutaj, showcase metody

mnist wizualizacja jak działa -> wygeneorować 20 feauterów, grubość wysokość, skośność, cyferki + benchmark z cvae, warunków jest wiele 5 feuterów, pozycja na obrazjku, 5 zbiorów i je pomaskować

pierwotny model z dostępem do pełni wiedzy i sztucznie maskujemy

smiles są mniejsze

joint former - gpt2

transformer z warunkami

prior jest funkcją warunków

prior GM, trzymanie średie i odchylenia, funkcja zmienia wagi jedynie komponentów - zwraca nowe pi mieszanek

kolejny ciekwany problem to:
- jeżeli warunki istnieją a my ich nie znamy
- marginalizacja jak nie znamy warunku jednego 
	- zapewnianie własności marginalizacji
		- najpierw binarne
	- zobaczyć jak bez marginalizacji to potem przejść

może na prostym nie będzie działać
maskowanie częściowo

pełny ground truth

na sc też można generować tym samym sposobem, aby sprawdzić