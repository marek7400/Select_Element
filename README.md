# Select Element - Chrome extension.
Select element on page, show info class ID root, hide element, copy selector to clipboard.
<br>
<br>
<br>

![select](images/select2.png)

### v2.1 

add "Short" option.


![2.1](images/2.1.png)

### v2.2 

-more precise selection. 

-option to select individual or similar elements

-multi-level undo hiding

-moving through the element tree with sliders

-option to freeze the menu

# v2.3

### FIX working on some pages. (ex. Google Maps)

![2.2](images/2.2.png)

# 2.4 change in the method of operation/selection of sliders

2 method block menu: JS (default) and CSS menu.

fix on some pages with wrong html menu (non-standard)

# 2.5 Another change to the selection method, added mode for searching within an element and copying properties

![2.5](images/2.5.png)

***********

# Element Picker Extension

An advanced Chrome extension for selecting elements, generating robust CSS selectors, and interacting with complex web pages, including those with iframes and dynamic, JavaScript-driven menus.

## Key Features

-   **Interactive Selector Generator:** Click on any element to generate a precise CSS selector.
-   **Full Iframe Support:** Works seamlessly across all `<iframe>` elements on a page.
-   **Interactive Controls:** Fine-tune selectors using intuitive sliders and checkboxes.
-   **Multiple Selector Modes:**
    -   **Similar Mode:** Generates flexible selectors based on tags, classes, and IDs.
    -   **Short Mode:** Creates a concise selector for only the last element in the path.
    -   **Single Mode:** Generates precise, index-based selectors (`:nth-of-type`) for navigating lists and complex structures.
-   **Advanced Freeze Functionality:** Two distinct modes to handle dynamic elements.
-   **Color Customization:** Change the highlight and selection colors to your preference.
-   **Element Hiding:** Temporarily hide elements on the page to refine your view.

---

## How to Use

1.  Click the extension icon in the Chrome toolbar to activate the picker. Your cursor will change to a crosshair.
2.  Move your mouse over the page. Elements under the cursor will be highlighted.
3.  Click on the desired element to select it.
4.  The control panel will appear. Use the sliders and checkboxes to adjust the generated selector.
5.  Use the action buttons (`COPY`, `HIDE`, etc.) to perform the desired operation.
6.  Click `SELECT` to re-enter picking mode or `QUIT` (or press `Esc`) to close the extension.

---

## Panel and Modes Explained

### Top Bar

-   **Color Swatches:** The first (blue) swatch changes the hover color, while the second (red) changes the selection color.
-   **❄️ Freeze Button:** Toggles the **JS Freeze** mode.
-   **Minimize/Quit:** Minimizes the panel or closes the extension.

### Selector Display

-   Shows the currently generated filter-ready selector (e.g., `##selector`).
-   This field is `contenteditable`, so you can manually type or paste a selector to see it highlighted on the page.

### Sliders

-   **Top Slider (Path Slider):** Controls the selector's depth. Moving it to the left goes up the DOM tree (selects parent elements).
-   **Bottom Slider (Attribute/Index Slider):** Its function changes depending on the mode:
    -   In **Similar Mode**, it adjusts the specificity of the selector parts (e.g., from just `tag` to `tag.class` or `#id`).
    -   In **Single Mode**, it directly changes the `:nth-of-type(n)` index of the element currently targeted by the Path Slider.

### Checkboxes and Modes

-   **`Similar` (checkbox):**
    -   When **checked**, it generates flexible, attribute-based selectors. This mode is great for finding multiple elements that share similar characteristics.
-   **`Short` (checkbox):**
    -   Only works when `Similar` is checked.
    -   When **checked**, it simplifies the selector to only target the last element in the current path, instead of the full parent-child chain.
-   **`Single Mode` (`Similar` checkbox unchecked):**
    -   This mode generates highly specific, index-based selectors (`tag:nth-of-type(n)`).
    -   It is designed for precision, especially when dealing with lists or sibling elements that lack unique classes or IDs (or have duplicated IDs).
    -   The sliders allow you to navigate the DOM tree precisely, level by level and index by index.

---

## The Freeze Function Explained

The extension offers two distinct "freeze" modes to handle dynamic elements that appear or disappear on user interaction. Only one mode can be active at a time.

### 1. CSS Freeze (via 'z' key)

-   **Purpose:** To lock the visual state of elements that appear on CSS `:hover`, such as dropdown menus.
-   **How it works:** When you hover over an element that triggers a menu to appear (e.g., an `<li>` that shows a `<ul>`), pressing the **'z'** key will "freeze" that menu. The extension does this by getting the menu's `computedStyle` (its exact size, position, and display properties at that moment) and applying it as an inline style. This keeps the menu visible even after you move your cursor away.
-   **How to use:**
    1.  Hover over the element that makes the menu appear.
    2.  Once the menu is visible, press the **'z'** key.
    3.  The menu is now frozen, and you can interact with its items.
    4.  Pressing **'z'** again will unfreeze the menu and clear the current selection.
-   **Limitations:** This method is most effective for menus controlled by CSS. It may not correctly freeze elements animated by very complex JavaScript that continuously alters transform or position properties, as it only captures a single snapshot of the element's style.

### 2. JS Freeze (via ❄️ icon)

-   **Purpose:** To block JavaScript events that cause elements to disappear, such as `mouseout` or `mouseleave` listeners.
-   **How it works:** When activated, this mode adds global event listeners that capture and stop the propagation of key mouse events (`mouseout`, `mouseleave`, `blur`, etc.). This prevents the page's scripts from detecting that you have moved the mouse away, thus keeping the dynamic element visible.
-   **How to use:**
    1.  Click the **❄️** icon on the panel. The icon will become active.
    2.  Hover over the element to make the dynamic menu/element appear. It should now remain visible.
    3.  Click the **❄️** icon again to disable the event listeners and clear the current selection.
-   **Limitations:** This mode is powerful but can be disruptive. By blocking events globally, it may interfere with other functionalities on the page while active. Use it when the CSS freeze ('z' key) is not sufficient.

---
---

# Rozszerzenie Element Picker

Zaawansowane rozszerzenie do przeglądarki Chrome służące do zaznaczania elementów, generowania solidnych selektorów CSS i interakcji ze złożonymi stronami internetowymi, w tym z elementami `<iframe>` oraz dynamicznymi menu opartymi na JavaScript.

## Główne Funkcje

-   **Interaktywny Generator Selektorów:** Kliknij dowolny element, aby wygenerować precyzyjny selektor CSS.
-   **Pełne Wsparcie dla Iframe:** Działa płynnie we wszystkich elementach `<iframe>` na stronie.
-   **Interaktywne Kontrolki:** Dostosuj selektory za pomocą intuicyjnych suwaków i pól wyboru.
-   **Wiele Trybów Selektorów:**
    -   **Tryb Similar:** Generuje elastyczne selektory oparte na tagach, klasach i ID.
    -   **Tryb Short:** Tworzy zwięzły selektor tylko dla ostatniego elementu w ścieżce.
    -   **Tryb Single:** Generuje precyzyjne, oparte na indeksach selektory (`:nth-of-type`) do nawigacji po listach i złożonych strukturach.
-   **Zaawansowana Funkcja Zamrażania (Freeze):** Dwa odrębne tryby do obsługi dynamicznych elementów.
-   **Personalizacja Kolorów:** Zmień kolory podświetlenia i zaznaczenia według własnych preferencji.
-   **Ukrywanie Elementów:** Tymczasowo ukrywaj elementy na stronie, aby oczyścić widok.

---

## Jak Używać

1.  Kliknij ikonę rozszerzenia na pasku narzędzi Chrome, aby aktywować picker. Kursor zmieni się na celownik.
2.  Przesuwaj mysz po stronie. Elementy pod kursorem będą podświetlane.
3.  Kliknij wybrany element, aby go zaznaczyć.
4.  Pojawi się panel kontrolny. Użyj suwaków i pól wyboru, aby dostosować wygenerowany selektor.
5.  Użyj przycisków akcji (`KOPIUJ`, `UKRYJ` itp.), aby wykonać pożądaną operację.
6.  Kliknij `SELECT`, aby ponownie wejść w tryb wybierania, lub `QUIT` (albo naciśnij `Esc`), aby zamknąć rozszerzenie.

---

## Opis Panelu i Trybów

### Górny Pasek

-   **Próbniki Kolorów:** Pierwszy (niebieski) próbnik zmienia kolor podświetlenia (hover), a drugi (czerwony) zmienia kolor zaznaczenia.
-   **Przycisk ❄️ (Freeze):** Przełącza tryb **Zamrażania JS**.
-   **Minimalizuj/Zamknij:** Minimalizuje panel lub zamyka rozszerzenie.

### Wyświetlacz Selektora

-   Pokazuje aktualnie wygenerowany selektor gotowy do użycia w filtrach (np. `##selektor`).
-   Pole to jest edytowalne (`contenteditable`), więc możesz ręcznie wpisać lub wkleić selektor, aby zobaczyć jego podświetlenie na stronie.

### Suwaki

-   **Górny Suwak (Suwak Ścieżki):** Kontroluje głębokość selektora. Przesunięcie w lewo przesuwa się w górę drzewa DOM (zaznacza elementy nadrzędne).
-   **Dolny Suwak (Suwak Atrybutów/Indeksu):** Jego funkcja zależy od trybu:
    -   W **Trybie Similar**, dostosowuje specyficzność części selektora (np. od samego `tagu` do `tag.klasa` lub `#id`).
    -   W **Trybie Single**, bezpośrednio zmienia indeks `:nth-of-type(n)` elementu aktualnie wskazywanego przez Suwak Ścieżki.

### Pola Wyboru i Tryby

-   **`Similar` (pole wyboru):**
    -   Gdy **zaznaczone**, generuje elastyczne selektory oparte na atrybutach. Ten tryb świetnie nadaje się do znajdowania wielu elementów o podobnych cechach.
-   **`Short` (pole wyboru):**
    -   Działa tylko, gdy `Similar` jest zaznaczone.
    -   Gdy **zaznaczone**, upraszcza selektor, aby celował tylko w ostatni element w bieżącej ścieżce, zamiast w cały łańcuch rodzic-dziecko.
-   **`Tryb Single` (pole `Similar` odznaczone):**
    -   Ten tryb generuje bardzo specyficzne, oparte na indeksach selektory (`tag:nth-of-type(n)`).
    -   Został zaprojektowany z myślą o precyzji, zwłaszcza przy pracy z listami lub elementami-rodzeństwem, które nie mają unikalnych klas lub ID (lub mają zduplikowane ID).
    -   Suwaki pozwalają na precyzyjną nawigację po drzewie DOM, poziom po poziomie i indeks po indeksie.

---

## Wyjaśnienie Funkcji Zamrażania (Freeze)

Rozszerzenie oferuje dwa odrębne tryby „zamrażania” do obsługi dynamicznych elementów, które pojawiają się lub znikają w wyniku interakcji użytkownika. Tylko jeden tryb może być aktywny w danym momencie.

### 1. Zamrażanie CSS (za pomocą klawisza 'z')

-   **Cel:** Zablokowanie stanu wizualnego elementów, które pojawiają się przy użyciu CSS `:hover`, takich jak rozwijane menu.
-   **Jak to działa:** Gdy najedziesz kursorem na element, który powoduje pojawienie się menu (np. `<li>`, które pokazuje `<ul>`), naciśnięcie klawisza **'z'** „zamrozi” to menu. Rozszerzenie robi to, pobierając `computedStyle` menu (jego dokładny rozmiar, pozycję i właściwości wyświetlania w danym momencie) i stosując go jako styl inline. Dzięki temu menu pozostaje widoczne nawet po odsunięciu kursora.
-   **Jak używać:**
    1.  Najedź kursorem na element, który powoduje pojawienie się menu.
    2.  Gdy menu będzie widoczne, naciśnij klawisz **'z'**.
    3.  Menu jest teraz zamrożone i możesz wchodzić w interakcję z jego elementami.
    4.  Ponowne naciśnięcie **'z'** odmrozi menu i wyczyści bieżące zaznaczenie.
-   **Ograniczenia:** Ta metoda jest najskuteczniejsza w przypadku menu kontrolowanych przez CSS. Może nie zamrozić poprawnie elementów animowanych przez bardzo złożony JavaScript, który ciągle zmienia właściwości `transform` lub `position`, ponieważ przechwytuje tylko pojedynczą migawkę stylu elementu.

### 2. Zamrażanie JS (za pomocą ikony ❄️)

-   **Cel:** Zablokowanie zdarzeń JavaScript, które powodują znikanie elementów, takich jak listenery `mouseout` czy `mouseleave`.
-   **Jak to działa:** Po aktywacji ten tryb dodaje globalne listenery zdarzeń, które przechwytują i zatrzymują propagację kluczowych zdarzeń myszy (`mouseout`, `mouseleave`, `blur` itp.). Zapobiega to wykryciu przez skrypty strony, że odsunąłeś mysz, dzięki czemu dynamiczny element pozostaje widoczny.
-   **Jak używać:**
    1.  Kliknij ikonę **❄️** na panelu. Ikona stanie się aktywna.
    2.  Najedź na element, aby pojawiło się dynamiczne menu/element. Powinno ono teraz pozostać widoczne.
    3.  Kliknij ponownie ikonę **❄️**, aby wyłączyć listenery zdarzeń i wyczyścić bieżące zaznaczenie.
-   **Ograniczenia:** Ten tryb jest potężny, ale może być inwazyjny. Blokując zdarzenia globalnie, może zakłócać inne funkcjonalności na stronie, gdy jest aktywny. Używaj go, gdy zamrażanie CSS (klawisz 'z') nie jest wystarczające.
