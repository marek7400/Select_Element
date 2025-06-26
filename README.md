# Select Element - Chrome extension. (STILL IN PROGRESS)
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

# Element Picker & Selector Generator

This Chrome extension is an advanced tool for developers, testers, and power-users, designed to inspect web pages, select elements (even within iframes and shadow DOMs), and generate precise CSS selectors. It provides powerful modes for handling dynamic content and complex element structures.

---

## English

### Features

- **Interactive Element Selection:** Simply click the extension icon to activate the picker and hover over elements on the page.
- **Iframe & Shadow DOM Support:** Seamlessly works across frames and can inspect elements inside open Shadow DOMs.
- **Advanced Selector Generation:** Fine-tune selectors with intuitive sliders.
- **Powerful Modes:**
    - **Similar Mode:** Find a common selector for multiple similar elements.
    - **Inside Mode:** Traverse the DOM *inside* a selected container to pick a specific child.
    - **Freeze Mode:** "Freeze" dynamic elements like hover-activated menus to make them selectable.
- **Multiple Copy Options:** Copy the generated selector in various formats (ad-blocker filter, JavaScript, XPath, outerHTML, styles).
- **Customizable Highlighting:** Change the colors for hover and selection highlighting.

### How to Use

1.  Click the extension icon in your Chrome toolbar. The page will enter "picker mode," indicated by a crosshair cursor.
2.  Move your mouse over the page. Elements will be highlighted as you hover.
3.  Click on the element you want to select.
4.  The picker will pause, and the control panel will appear, showing a generated selector for the clicked element.
5.  Use the panel's controls to refine the selector, then copy it in your desired format.

### Key Modes Explained

#### Similar Mode

This is the default mode after you select an element. It's designed to help you find a selector that matches not just the element you clicked, but also other elements that are structurally similar.

-   **Path Slider:** Moves up the DOM tree from the selected element. Dragging the slider changes the selection from the specific element you clicked to its parent, grandparent, and so on. This is useful for broadening the scope of your selector.
-   **Attribute Slider:** Controls the specificity of the selector for the currently targeted element in the path. You can cycle through levels like:
    -   Tag only (e.g., `div`)
    -   Tag + ID (e.g., `div#main-content`)
    -   Tag + Classes (e.g., `div.item.active`)
    -   Tag + ID or Classes
-   **Short Checkbox:** When checked, it generates a selector for only the last element in the path, rather than the full, more specific path from a higher-level parent.

#### Inside Mode

This mode is for situations where you've selected a larger container element (like a product card) but want to target a specific item *inside* it (like the price or an "Add to Cart" button).

1.  Click an element to select it.
2.  In the control panel, check the **"Inside"** checkbox.
3.  The initially selected element is now treated as a container.
4.  The **Path Slider** now lets you walk through every single node (including text nodes) inside that container. This allows for extremely precise selection of child elements that might be hard to click directly.

#### Freeze Mode

Web pages often have dynamic elements, like dropdown menus that only appear on hover and disappear as soon as you move your mouse away. Freeze Mode helps you capture these elusive elements.

-   **JS Freeze (❄️ Button):** This is the powerful, site-wide option. Clicking the snowflake icon (❄️) in the panel's title bar blocks common JavaScript events like `mouseout` and `mouseleave` for the entire page. This forces menus and tooltips to stay open, allowing you to move your mouse and select them with the picker. Click the button again to disable it.
-   **CSS Freeze ('z' Key):** This is a more targeted approach.
    1.  Hover over an element (e.g., a "File" menu) to make its dropdown appear.
    2.  While the dropdown is visible, press the `z` key.
    3.  The extension captures the dropdown's current CSS styles (like `display: block`, `opacity: 1`) and applies them as inline styles. A striped overlay appears over the element to indicate it's "frozen."
    4.  You can now move your mouse away to interact with the picker panel, and the dropdown will remain visible.
    5.  Press `z` again to unfreeze it.

#### Copy Options

The control panel allows you to copy your findings in several useful formats:

-   **##:** Standard cosmetic filter syntax used by ad-blockers like uBlock Origin (`domain.com##selector`).
-   **JS:** A JavaScript snippet to select the element: `document.querySelector("selector")`.
-   **o.HTML:** The complete `outerHTML` of the selected element, including special handling for rendering the contents of a Shadow Root.
-   **Element:** Copies the full HTML of the element (same as o.HTML).
-   **Styles:** A formatted string of all matched CSS rules applied to the element, mimicking the "Styles" tab in browser DevTools.
-   **XPath:** A relative XPath expression for the element.
-   **F.XPath:** The full, absolute XPath from the root of the document.

---

## Polski

### Funkcje

-   **Interaktywne Wybieranie Elementów:** Po prostu kliknij ikonę rozszerzenia, aby aktywować tryb próbnika i najeżdżaj na elementy na stronie.
-   **Wsparcie dla Iframe i Shadow DOM:** Działa płynnie wewnątrz ramek (iframe) i potrafi inspekcjonować elementy w otwartym Shadow DOM.
-   **Zaawansowane Generowanie Selektorów:** Precyzyjnie dostosuj selektory za pomocą intuicyjnych suwaków.
-   **Potężne Tryby Pracy:**
    -   **Tryb Similar (Podobne):** Znajduje wspólny selektor dla wielu podobnych elementów.
    -   **Tryb Inside (Wewnętrzny):** Umożliwia nawigację wewnątrz wybranego kontenera, aby wybrać konkretny element podrzędny.
    -   **Tryb Freeze (Zamrażanie):** "Zamraża" dynamiczne elementy, takie jak menu aktywowane najechaniem myszy, aby umożliwić ich wybranie.
-   **Wiele Opcji Kopiowania:** Skopiuj wygenerowany selektor w różnych formatach (filtr dla ad-blockerów, JavaScript, XPath, outerHTML, style).
-   **Konfigurowalne Podświetlenie:** Zmień kolory podświetlenia dla najechania myszą i zaznaczenia.

### Jak Używać

1.  Kliknij ikonę rozszerzenia na pasku narzędzi Chrome. Strona przejdzie w "tryb próbnika", co zasygnalizuje kursor w kształcie krzyżyka.
2.  Przesuwaj mysz po stronie. Elementy będą podświetlane, gdy na nie najedziesz.
3.  Kliknij element, który chcesz wybrać.
4.  Próbnik zostanie wstrzymany, a na ekranie pojawi się panel kontrolny, pokazujący wygenerowany selektor dla klikniętego elementu.
5.  Użyj narzędzi w panelu, aby dopracować selektor, a następnie skopiuj go w wybranym formacie.

### Wyjaśnienie Kluczowych Trybów

#### Tryb Similar (Podobne)

To domyślny tryb po wybraniu elementu. Został zaprojektowany, aby pomóc Ci znaleźć selektor pasujący nie tylko do klikniętego elementu, ale także do innych, które są strukturalnie podobne.

-   **Suwak Ścieżki (Path Slider):** Porusza się w górę drzewa DOM od wybranego elementu. Przesunięcie suwaka zmienia zaznaczenie z konkretnego klikniętego elementu na jego rodzica, dziadka itd. Jest to przydatne do rozszerzania zasięgu selektora.
-   **Suwak Atrybutów (Attribute Slider):** Kontroluje specyficzność selektora dla aktualnie wskazywanego elementu w ścieżce. Możesz przełączać się między poziomami, takimi jak:
    -   Tylko tag (np. `div`)
    -   Tag + ID (np. `div#main-content`)
    -   Tag + Klasy (np. `div.item.active`)
    -   Tag + ID lub Klasy
-   **Checkbox "Short":** Gdy jest zaznaczony, generuje selektor tylko dla ostatniego elementu w ścieżce, zamiast pełnej, bardziej szczegółowej ścieżki od elementu nadrzędnego.

#### Tryb Inside (Wewnętrzny)

Ten tryb jest przeznaczony do sytuacji, w których wybrałeś większy kontener (np. kartę produktu), ale chcesz wskazać konkretny element *w jego wnętrzu* (np. cenę lub przycisk "Dodaj do koszyka").

1.  Kliknij element, aby go wybrać.
2.  W panelu kontrolnym zaznacz checkbox **"Inside"**.
3.  Początkowo wybrany element jest teraz traktowany jako kontener.
4.  **Suwak Ścieżki** pozwala teraz przechodzić przez każdy pojedynczy węzeł (w tym węzły tekstowe) wewnątrz tego kontenera. Umożliwia to niezwykle precyzyjne wybranie elementów podrzędnych, które mogłyby być trudne do kliknięcia bezpośrednio.

#### Tryb Freeze (Zamrażanie)

Strony internetowe często zawierają dynamiczne elementy, takie jak rozwijane menu, które pojawiają się tylko po najechaniu myszą i znikają, gdy tylko ją odsuniesz. Tryb Zamrażania pomaga uchwycić te ulotne elementy.

-   **Zamrażanie JS (Przycisk ❄️):** Jest to potężna opcja działająca na całą stronę. Kliknięcie ikony płatka śniegu (❄️) na pasku tytułowym panelu blokuje powszechne zdarzenia JavaScript, takie jak `mouseout` i `mouseleave` dla całej strony. Zmusza to menu i podpowiedzi do pozostania otwartymi, umożliwiając Ci przesunięcie myszy i wybranie ich za pomocą próbnika. Kliknij przycisk ponownie, aby go wyłączyć.
-   **Zamrażanie CSS (Klawisz 'z'):** Jest to bardziej ukierunkowane podejście.
    1.  Najedź na element (np. menu "Plik"), aby pojawiło się jego rozwijane menu.
    2.  Gdy menu jest widoczne, naciśnij klawisz `z`.
    3.  Rozszerzenie przechwytuje aktualne style CSS menu (takie jak `display: block`, `opacity: 1`) i stosuje je jako style inline. Na elemencie pojawi się pasiasta nakładka, aby zasygnalizować, że jest "zamrożony".
    4.  Możesz teraz odsunąć mysz, aby wejść w interakcję z panelem próbnika, a menu pozostanie widoczne.
    5.  Naciśnij `z` ponownie, aby je odblokować.

#### Opcje Kopiowania

Panel kontrolny pozwala skopiować wyniki w kilku przydatnych formatach:

-   **##:** Standardowa składnia filtrów kosmetycznych używana przez ad-blockery, takie jak uBlock Origin (`domena.com##selektor`).
-   **JS:** Fragment kodu JavaScript do wybrania elementu: `document.querySelector("selektor")`.
-   **o.HTML:** Kompletny `outerHTML` wybranego elementu, w tym specjalna obsługa renderowania zawartości Shadow Root.
-   **Element:** Kopiuje pełny kod HTML elementu (to samo co o.HTML).
-   **Styles:** Sformatowany ciąg wszystkich dopasowanych reguł CSS zastosowanych do elementu, naśladujący zakładkę "Style" w narzędziach deweloperskich przeglądarki.
-   **XPath:** Względne wyrażenie XPath dla elementu.
-   **F.XPath:** Pełne, bezwzględne wyrażenie XPath od korzenia dokumentu.
