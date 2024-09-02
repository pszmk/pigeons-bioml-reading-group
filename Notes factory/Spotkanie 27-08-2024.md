 - mnist
 - maskowanie smilesów w llmie, jeden atom - token np.
 - jak istniejący smiles to chcemy conditionować
 - czasem znam smiles i chcę go poprawić, albo de novo

- smiles unsupervised + dwa rodzaje warunków

dane z hydramp kilkanaście tys, ewentualnie - molekuły hydramp, też dane stringowe, mały alfabet 26 aminokwasów, alfabet smiles kilkadziesiąt kilkaset

zapisać abstrakt pracy bez submitu

ja zewaluować conditional model na mnist?
- ewaluacja w latencie
	- czy klastry się pokrywają
	- mnist działa nawet na dwóch wymiarach
	- w teorii można policzyć przy założeniu priora można policzyć nll
		- w iwae dokładna aproksymacja likeliihoodu
		- eksplicite zbiega do prawdziwego likelihoodu
		- NIEKONIECZNIE ale raczej i guesss - powinno być tak, że jak znamy więcej warunków to większy likelihood - prior powinien się zwężać
			- duży prior może zmniejszyć likelihood na wszystkim po rozmazuje na latencie
- FID - Frechet Inception Distance
- funkcje modelu:
	- vizualana ewaluacja
		- czy latent jest ustrykturyzowany
	- strukturyzowanie latentu
	- conditional generation
- hiper prior: bayesowski drugiego rzędu
	- tutaj rozumiemy jako tranable prior

- pokazać że model oparty na transformerze jest zanurzony w ustrukturyzowanym warunkowaniu i ograny probabilistycznie
- standardowy hiper prior
- warunki do wizualnej inspekcji
- porównanie rozkładów, nowych i starych danych

- model warunkowego prioru
	- warunek binarny
	- model coś zwraca: GM - wyznacza ostateczny prior przez marginalizację
	- jak przyjmiemy, że bazą jest model oparty o GM - wtedy marginalizacji modelu
		- brakuje prawdopodobieństw tych warunków potrzebnych do wyznaczenia głównego prioru
		- jak pojawiają się dwa warunki -> problemy ze spójnością
			- np. model tylko jak znamy warunki (zmienne) binarne c1 i c2
			- model moze przyjąć warunek, że c1 wysokie
				- jak to co zwróci ma sięd o tego co się stanie gdy podamy c1 wysokie z oboma możliwościami c2
				- warunek spójności dla ic50 powinien być  marginalizacjią tych pozostałych
				- drugorzędowy warunek wariacyjny potrzeby do tego
				- tak zaprojektować ten transformer, aby było to spełnione
				- trenowanie dużej mikstury i tylko logity komponentów wyznaczać -> wtedy warunki spójności mogą być łatwiejsze do ogarnięcia

- zacząć od trenowania deterministycznego encodera
	- aproksymacja posterioru
- gauss z zerową wariancją
- sukces VAE
	- generuje upchane latenty, rozsmarowane
	- rządamy lokalnej stałości
- stochastyczność IWAE
	- problem, że są zbyt mocno rozsmarowane, bo tylko któryś może być dobrze zrekonstruowany
- kernel liczy na batchu
	- łamie iid
	- w VAE
	- złamana jest regułą WAE - zakłada, że dekoder też jest deterministyczny
	- zął, że dekoder jest determisistyczny
- deterministyczny


RUDY - jest docker, ruthless docker - dobra praktyk, ale upierdliwe, problem z gpu
- mim
	- musi być ze students
	- ssh login@rudy.mimuw.edu.pl
	- home 33
	
- Host rudy.mimuw.edu.pl
- HostName rudy.mimuw.edu.pl
- IdentityFile ~/.ssh/id_ed25519
- User kkoras
- LocalForward 5000 localhost:5000
- ProxyJump duch.mimuw.edu.pl


- triplet loss