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

SASS

Jest ppreprocesorem CSS, dodaje dodatkowe funkcjonalności.
SASS oferuje zmienne, zagnieżdzenia, operatory, import, mixins, funkcje, rozszerzenia, dyrektywy kontrolne

Syntax sass i scss - pierwsza bez nawiasów, druga podobna do klasycznego css. 

1. Variables

$primary-color: #fdsads

@mixin clearfix{
    &::after{
    content: "";
    clear: both;
    display: table
}
}

nav{
    color: $primary-color;
    //Dodatek: Naprawa zwiniętego elementu w przypadku ustawienia float 
    @include clearfix
}

2. Nested

nav{
    color: $primary-color;
    ul{
        list-style: none;
        li{
            margin: 30px;
            &:first-child{
                margin: 15px;
            }
        }
    }
    &:hover{
        color: dark(&primary-color, 15%)
    }
}

3. Mixin

    @mixin name{

    }

    @include name


Do mixin możemy przekazać argument.  
@mixin name($col){
    color: $col
}
a następnie odwołać się do niego 
@include name($primary-color)

4. Funkcje 

Możemy tworzyć unckej
@function margin($a, $b){
    @return $a / $b
}

wykorzystanie

nav{
    margin: margin(60, 2) * 1px;
}

lub używać wbudownych dark($primary-color, 15%)

5. Rozszerzenia

%btn-placeholder{

}

wykorzystanie 

@extend %btn-placeholder

WIERSZ POLECEŃ 

- npm init
- instalujemy sass npm install node-sass --save-dev
- "scripts": {
    "compile:sass": "node-sass sass/main.scss css/style.css"
  },
- npm run compile:sass

PLIKI CZĘŚCIOWE 
1. Base > _base.scss

PROJEKTOWANIE RESPONSYWNE 
- Fluid Grids and Layouts - używamy %
- Responsnywne i elastyczne obrazy
- Media Query

LAYOUT TYPES 
- Float Layouts
- FlexBox
- CSS Grid

CENTROWANIE BLOKU WEWNĄTRZ INNEGO BLOKU
margin: 0 auto;

STANDARD SZEROKOŚCI > 1140PX

 [class^="col-"] - wybieramy tylko te klasy kt ore zaczynają się od...
 [class*="col-"] - wybieramy wszystkie...
 [class$="col-"] - wszystkie kończą się...

 GRADIENT NA LITERACH
 
.heading-secondary{
    font-size: 3.5rem;
    text-transform: uppercase;
    font-weight: 700;
    // Aby zmniejszyć kolor nie zajmował całej przestrzeni
    display: inline-block;
    // Aby uzyskać gradient liter ustawiamy kolor nagłówka
    background-image: linear-gradient(to right, $color-primary-light, $color-primary-dark);
    //Kolor zostaje ograniczony do liter 
    -webkit-background-clip: text;
    color: transparent;
    letter-spacing: .2rem;
    transition: all .2s;

POCHYLENIE

&:hover{
        transform: skewY(2deg) skewX(15deg) scale(1.1);
        text-shadow: .5rem 1rem 2rem rgba($color-black, .2);
    }

KLASY UTILITY 

Są to klasy które mają jeden cel np.: wyśrodkować

RESPONSYWNOŚĆ

Wymiary procentów podajemy w %.

OBRAMOWANIE

Aby zrobić ładne obramowanie właściwość outline aby oddalić obramowanie outline-offset

SELEKTOR 

& > * {
        transform: skewY(7deg)
    }

PERSPEKTYWA

Perspektywa musi być zdefiniowana na elemencie rodzica. 

BACKFACE
- stosowane przy kartach 

backface-visibility: hidden;

MIESZANIE OBRAZU Z GRADIENTEM



RESPONSYWNOŚĆ

Dwa podejście:
1. First Desktop - w pierwszej koeljności projektujemy stronę na desktop a następnie mobile. Aby zmniejszyć stronę używamy zapytań o media.
2. First Mobile - piszemy stronę dla mniejszych ekranów w pierwszej kolejności a następnie za pomocą zapytań o media dostospowujemy stronę do ekranu monitora. Zapytania o media (min-width).

Punkty przerwania:
- 0px - 600px
- 600px - 900px
- 900px - 1200px
- 1200px - ...

DESKTOP-FIRST
max-width: 600px i max-width: 900 - ekran ma 500px będą obowiązywać dwa zapytania o 

MOBILE-FIRST
min-width: 600px

PUNKTY PRZERWANIA:
BAD: dostosowanie punktów przerwania do urządzeń typowych np. iphone
GOOD: dostosować punkty przerwania do grup urządzeń
PERFECT: ignorowanie urządzeń i patrzenie tylko i wyłącznie na content

W ciekawy sposób szerokość ekranu pokazuje stat counter.
Punkty przerwania dla: telefonów 0-600, tabletów portretowych 600 - 900/ krajobrazowych 900 - 1200, komputerów stacjonarnych 1200 -..., większych monitorów 1800 - ....

###################

@mixin respond($breakpoint) {
    @if $breakpoint == phone {
        @media (max-width: 37.5em){
            @content
        }
    }
    @if $breakpoint == tab-port {
        @media (max-width: 56.25em){
            @content
        }
    }
    @if $breakpoint == tab-land {
        @media (max-width: 75em){
            @content
        }
    }
    @if $breakpoint == tab-desktop {
        @media (min-width: 112.5em){
            @content
        }
    }
}

###################

###################

html{
    font-size: 62.5%;

    @include respond(tab-land) {
        font-size: 56.25%
    }
    
    @include respond(tab-port) {
        font-size: 50%
    }
    
    @include respond(tab-desktop) {
        font-size: 75%
    }
}

###################

Responsywny obraz

Ważne aby wielkość obrazu dostosować do urządzenia - komputera stacjonarnego lub laptopa.

Trzy przypadki - użycie obrazów responsywnych:
- przełączanie rozdzielczości

<img srcset="img/nat-1.jpg 300w, img/nat-1-large.jpg 1000w"
     sizes="(max-width: 900px) 20vw, (max-width: 600px) 30vw, 300px"
     alt="Photo 1"
     class="composition__photo composition__photo--1"
     src="img/nat-1-large.jpg">

- przełączanie gęstości pikseli

Dodajemy atrybut srcset do znacznika img oraz deskryptor gęstości.

- kierunek sztuki

Obrazy są dostosowane do szerokości ekranu. Stosujemy znaczniki 

<picture>
    <source srcset="img/logo-green-small-1x.png 1x, img/logo-green-small-2x.png 2x" 
            media="(max-width: 37.5em)">
    <img srcset="img/logo-green-1x.png 1x, img/logo-green-2x.png 2x" alt="Full logo" class="footer__logo">
</picture>