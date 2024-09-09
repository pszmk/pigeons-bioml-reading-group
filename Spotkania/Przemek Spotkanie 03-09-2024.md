datasety
- pubchem cid - intigers
	- cid smiles - unsupervised
- prism - sensitivity, mierzymy po aplikacji leku ile komurek umarło
	- tabela: pubchem cid row, col - cell line, wartości jak lek działał, drug sensitivity
- cmap - najbardziej skomplikowany to samo co LINCS
	- links - zmiany w ekspresji pod wpływem leku
	- dla każdej linii komórkowej jest wektor wzdłóż genów
	- dla każdego tripleta: lek komórka gen jak się zmieniła wartość ekspresji
	- perturbacja to dawka leku - może być różna, trz jest naiwnie agregowane średnią dla leku - po sygnaturach po celllineasach 

pobrać dataset = 

problem z importowaniem datasetów