# Natours

TRZY FILARY HTML&CSS

1. Responsive design
- media queries, fluid layouts, responsive images, correct units, desktop-first vs mobile-first
2. Maintainable and scalable code (możliw do utrzymania i skalowalny kod)
- clean, easy to understand, growth, reusable, organize files, name classes, structire HTML
3. Web performance (wydajność sieci)
- less code, less HTTP requests, compress code, use a CSS preprocessor, less images, compress images

WEBPAGE
1. Load HTML
    a)Parse HTML --> Document Object Model 
    b)Load CSS --> rozwiązywanie koflików (kaskada), process final CSS values --> CSS Object Model
2. Render Tree
3. Website rendering the visual formatting model
4. Final rendered website

STRUKTURA
.my-class{
    color: blue,
    text-align: center
}

selektor, blok deklaracji, deklaracja, właściwość, wartość

kaskada to proces łączenia różnych arkuszy stylów i rozwiązywanie konfliktów między różnymi regułami CSS i deklaracjami gdy wiecej niz jedna reguła dotyczy pewnego elementu. Według importance (user important / author important / author / user / przeglądarka)> specificity (inline styles / id / class, pseudo-classes, attribute / elements, pseudo-elements) > source order. 

DEKLARACJE:
- programisty, 
- użytkownika,
- przeglądarki

Przetwarzanie w fazie analizy CSS

font-size: 16px 
font-size: (16px * 1.5 = 24px)

Istnieje rozróżnienie dla czcionek lub pomiarów długości lub odległości. 
- czcionka 150 % = 24px (ponieważ podstawowa rozmiar czionki określany przez przeglądakę to 16px)
- długość lub odległość - określana względem elementu ndarzędnego

- em - element parent 3 em x 24px = 72px
- em - element parent 2 em x 24px = 48px
- rem - root jako referencja 10rem x 16px = 160px

em od rozmiaru elementu nadrzednego rem od rozmiaru trzcionki. Stosowanie rem ułatwia pisanie zapytań o media - wystarczy działanie na font-size.

Czionkę główną ustawiamy na 62,5%. Ten rozmiar jest równy 10px ponieważ domyślny rozmiar czionki to 16px;

Przy rozmarach 0.5rem - skracamy i piszemy .5rem

Możemy zbudować więcej responsywnych układów. Ponieważ wraz ze wzrostem czionki rosną iine wartości ponieważ ulegają pomnożeniu. 

- vh
- vw

Dziedziczenie - propagowanie właściwości od rodziców do dzieci.

inherit - wymusza dziedziczenie

Resetowanie dla wszystkich elementów również pseudoelementów. 

*,
*::after,
*::before{
    margin: 0;
    padding: 0;
    box-sizing: inherit;
}

MODEL PUDEŁKOWY
- margin
- border
- padding
- content
- width
- height

total width i total height obejmują wszystko oprócz marginesów.

użycie box-sizing: border-box sktkuje wykorzystaniem tylko specified width: border, pading nie jest dodawany do wymiarów pudełka !!!

BOX TYPES

- Block-level boxes - display: block - 100% szerokości rodzica - jedna po drugiej
- Inline boxes - display: inline - zajmują tyle przestrzeni ile potrzebują - możemy określać tylko poziomy pading i margin
- Inline-block boxes - display: inline-block - wykorzystują swoją przestrzeń treści -

POSITIONING

- Normal flow - position: relative - default - ułożenie w naturalnym porządku kodu
- Floats - float: left/right - element jest usuniety z naturalnego porządku i przesunięty w prawo lub lewo jak najdalej to mozliwe az dotknie krawędzi jego pudełka zawierającego lub innego elementu pływającego
- Absolute positioning - position: absolute/fixed - element usuniety z porządku kodu - brak wpływu na otaczającą zawartość - może nakładać się na element zajmując tę samą przestrzeń

KONTEKST STOSU

- z-index - określa kolejność elementów w stosie, stosowany razem z position: relative/absolute.

Zasady CSS: Clean, Modular, Reasable, Ready for growth

Proces CSS:

THINK -> BUILD -> ARCHITECT

Staramy się dzielić naszą stronę na komponenty elementy modułowe. Komponenty powinny być wielokrotnego użytku tagże pomiędzy różnymi projektami. Komponenty muszą być nie zależne.

BEM - Block Element Modifier

Block to samodzielny komponent który można wykorzystać w dowolnym miejscu w projekcie.
.block{}
Element nie ma charakteru samodzielnego
.block__element{}
Modyfikator służy do stworzenia nowej wersji. Uszczegółowienie elementu.
.block__element--modifier{}

Architektura - The 7-1 Pattern
7 różnych folderów, 1 główny Sass w którym importujemy wszystkie nasze częsci
base, components, layout, pages, themes, abstract, vendors



