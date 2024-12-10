#### Co się działo
- Na razie zostawiamy single cell w spokoju.

### Target Identification
- **Cel identyfikacji targetów**:
    - Możemy wykorzystać różne bazy danych do identyfikacji targetów leków (czyli białek, w które celuje lek). Choć te dane nie są idealne, mogą być przydatne.
    - Jednym z podejść jest wykorzystanie istniejących leków i przewidywanie, jakie mają cele.
    - W ten sposób możemy wyszukiwać nowe wskazania dla leków.
    - Zwykle na początku identyfikuje się targety, a następnie generuje się odpowiednie molekuły.
- **Modalności identyfikacji**:
    - **Gene Expression Signatures**:
        - Sygnatury ekspresji genów, np. L1000, mogą być wykorzystywane do identyfikacji targetów.
        - Przeprowadzamy perturbacje, np. wyłączając gen i mierząc ekspresję przed i po.
        - Możemy obserwować, który podzbiór genów był najbardziej podatny na zmiany, a nie wszystkie geny na raz.

### Generowanie Leków
- **SMILES "notacja"**:
    - Notacja SMILES opisuje strukturę chemiczną poprzez atomy, wiązania itp.
- **Modele generatywne**:
    - Istnieje wiele modeli generatywnych.
    - **Conditional generation**  często nie działa dobrze, ponieważ jest zbyt zawężone, np. warunkuje tylko kwestię rozpuszczalności w tłuszczach.
    - Rzadko spotyka się modele uwzględniające, że lek wywołuje określoną sygnaturę ekspresji genów.
    - Idealnie byłoby mieć model generatywny, który uwzględnia sygnatury ekspresji genów, np. zmiany w ekspresji lub wyłączenie genu.
    - W przypadku chorób takich jak Alzheimer, można by próbować znaleźć molekułę, która odwraca lub naśladuje sygnaturę choroby albo targetu.
    - Celem jest uzyskanie molekuły podobnej do istniejącej, ale lepiej dopasowanej do celu.

### Projekty KK
- **Ogólna metoda**:
    - KK pracował nad ogólną metodą, którą można zastosować do konkretnego przypadku.
    - Przykładowo: chcemy stworzyć generatywny model, który będzie mógł pracować na nieograniczonej liczbie warunków. Model ten generowałby molekuły zgodne z danymi.
- **Profile aktywności**:
    - KK badał profile aktywności leków, które mogą być wykorzystywane do oceny ich skuteczności.

### Inspiracje z ESM-3
- **Modelowanie białek**:
    - ESM-3 przyjmuje białko jako dane wejściowe.
    - Część danych jest maskowana i iteracyjnie remaskowana, co pozwala na przewidywanie brakujących danych.
    - Kluczowe jest to, że nie obserwujemy pewnych danych i staramy się przewidywać jak najwięcej informacji z niepełnych danych.

### Zbiory danych
- **Dane SMILES**:
    - Istnieją dane dotyczące SMILES dla różnych leków.
- **Perturbacje**:
    - Dla 20 000 leków mamy zbiory danych z perturbacjami (ale mamy miliony nieoznaczonych danych).
- **Sensitivities**:
    - Mamy dane dotyczące tego, jak 5 000 leków wpływa na komórki rakowe (sensitivities).
- **Różnorodność danych**:
    - Posiadamy różne zbiory danych, z dużą ilością metadanych.
    - Można działać na jednym warunku, ale przy wielu warunkach może być problem.
    - Nie zawsze mamy pełną informację, ale zawsze jest coś, na czym można pracować.

### Pomysły i możliwości
- **Podejście słownikowe**:
    - Można spojrzeć na warunki jak na zbiór (słownik).
    - Jeden model encoduje SMILES, drugi warunkuje na priorze (który może być dowolny, np. Gaussian mixture).
    - Prior może być Gaussian mixture, gdzie funkcja zmienia jedynie wagi.
- **Testowanie**:
    - Można przetestować model na danych z MNIST, generując funkcje takie jak grubość czy skosność cyfr.
    - Ważne jest mieć pełny dostęp do wiedzy, a następnie maskować dane.
    - SMILES są mniejsze, co ułatwia analizę.
    - Należy zapewnić właściwości marginalizacji.
- **Baseline**:
    - Zaczynamy od baseline, wybierając losowe właściwości, a następnie przystępujemy do analizy danych leków.

### Potencjalna komercjalizacja
- **Dane z peptydów**:
    - Bardzo blisko mamy dane związane z peptydami, co może być użyteczne komercyjnie.

### Zbiory danych "with confitions"
- **Użycie datasetów "with conditions"**:
    - Możemy rozważyć użycie zbiorów danych, które uwzględniają określone warunki, co może pomóc w lepszej predykcji i analizie.
    - MIMIC-III https://physionet.org/content/mimiciii/1.4/