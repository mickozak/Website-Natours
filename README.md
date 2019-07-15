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

Możemy zbudować więcej responsywnych układów. Ponieważ wraz ze wzrostem czionki rosną iine wartości ponieważ ulegają pomnożeniu. 

- vh
- vw

Dziedziczenie - propagowanie właściwości od rodziców do dzieci. 