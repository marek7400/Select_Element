# Select Element - Chrome extension.
Select element on page, show info class ID root, hide element, copy selector to clipboard.

(not work on some pages ex. Google Maps)
<br>
<br>
<br>
![select](images/select2.png)

v2.1 add "Short" option.


![2.1](images/2.1.png)

v2.2 More precise selection. Option to select individual or similar elements, multi-level undo hiding, moving through the element tree with sliders. Option to freeze the menu.
![2.2](images/2.2.png)

# The “Freeze” feature 
was designed to solve one specific problem: maintaining the visibility of elements that are dynamically hidden by JavaScript in response to a change in the mouse cursor position or loss of focus by the element.
What elements and behaviors can “Freeze” freeze?
The main target is interactive interface elements that appear only briefly. “Freeze” will effectively block the mechanisms that hide them.
1. Dropdown/flyout menus:
Scenario: You hover over the “Products” menu item, and a list of categories appears. As soon as you move the cursor away from “Products” or the expanded list, the menu disappears.
How “Freeze” works: After enabling “Freeze” and expanding the menu, you can freely move your cursor away from it, and it will remain visible, allowing you to select any link from the list using the pipette.
2. Tooltips:
Scenario: You hover over the icon (?) to see a tooltip, which disappears when you move the cursor away.
“Freeze” action: “Freezes” the tooltip in a visible state, allowing you to analyze its content or structure.
3. Dynamic suggestion lists in search fields:
Scenario: You click on the search field and a list of popular phrases or search history appears. The list disappears as soon as you click anywhere else on the page (which causes a blur event on the search field).
Freeze action: Blocks the blur event so that the list of suggestions remains visible even after clicking outside the search field.
4. Any element whose disappearance is associated with mouseout, mouseleave, blur, or focusout events:
This is a technical generalization of the above points. If a website uses JavaScript to listen for these specific events in order to hide an element (e.g., by changing its display style to none or adding a hiding class), “Freeze” will effectively block it.
What can “Freeze” NOT freeze?
It is important to understand the limitations of this feature. It is not a universal tool for stopping all dynamic changes on a page.
1. Elements hidden by the click event:
Scenario: You have an accordion-type menu. Clicking on the header expands the content, and clicking again collapses it.
Limitation: “Freeze” intentionally does not block click events, as this would prevent any interaction with the page, including the expansion of the menu itself.
2. Elements closed by a timer (setTimeout):
Scenario: A “toast” message appears on the page (e.g., “Product added to cart”) and automatically disappears after 3 seconds.
Limitation: The “Freeze” function does not pause or block JavaScript timers. The message will disappear according to the programmed time.
3. Elements hidden by events other than those blocked:
Scenario: A modal window (pop-up) closes when the user starts scrolling the page (scroll event).
Limitation: “Freeze” only blocks 4 specific events. If the page uses others, such as scroll, resize, or keydown, to hide elements, they will not be blocked.
4. Visual effects based solely on CSS (:hover):
Scenario: The color of a button changes when you hover over it with the mouse, thanks to the CSS rule: button:hover { background-color: red; }.
Limitation: :hover effects are handled directly by the browser's rendering engine, not by JavaScript. “Freeze” works at the JavaScript event level, so it has no effect on pure CSS pseudo-classes. The button color will still return to normal when you move the cursor away from it.
Technical summary: How does it work?
“Freeze” works by adding global event listeners in the capture phase (capture: true). This means that it intercepts mouseout, mouseleave, blur, and focusout events at the very top of the DOM tree before they reach their target elements. It then immediately calls the event.stopPropagation() method on them, which effectively prevents them from being further processed by the page's scripts.
Golden rule: If something on the page disappears when you move the mouse away from it or click next to it, “Freeze” has a good chance of “freezing” it.

*********
# Funkcja "Freeze" 
została zaprojektowana, aby rozwiązać jeden, konkretny problem: utrzymanie widoczności elementów, które są dynamicznie ukrywane przez JavaScript w odpowiedzi na zmianę pozycji kursora myszy lub utratę fokusu przez element.
Jakie elementy i zachowania "Freeze" może zamrozić?
Głównym celem są interaktywne elementy interfejsu, które pojawiają się tylko na chwilę. "Freeze" skutecznie zablokuje mechanizmy ich ukrywania.
1. Rozwijane menu nawigacyjne (Dropdown / Flyout Menus):
Scenariusz: Najeżdżasz kursorem na pozycję menu "Produkty", pojawia się lista kategorii. Gdy tylko zjedziesz kursorem z "Produktów" lub z rozwiniętej listy, menu znika.
Działanie "Freeze": Po włączeniu "Freeze" i rozwinięciu menu, możesz swobodnie zjechać z niego kursorem, a ono pozostanie widoczne, pozwalając na wybranie dowolnego linku z listy za pomocą pipety.
2. Dymki z podpowiedziami (Tooltips):
Scenariusz: Najeżdżasz na ikonę (?), aby zobaczyć podpowiedź, która znika, gdy odsuniesz kursor.
Działanie "Freeze": "Zamrozi" dymek w stanie widocznym, umożliwiając analizę jego treści lub struktury.
3. Dynamiczne listy sugestii w polach wyszukiwania:
Scenariusz: Klikasz w pole wyszukiwania i pojawia się lista popularnych fraz lub historii wyszukiwania. Lista znika, gdy tylko klikniesz gdziekolwiek indziej na stronie (co powoduje zdarzenie blur na polu wyszukiwania).
Działanie "Freeze": Zablokuje zdarzenie blur, dzięki czemu lista sugestii pozostanie widoczna nawet po kliknięciu poza polem wyszukiwania.
4. Dowolny element, którego zniknięcie jest powiązane ze zdarzeniami mouseout, mouseleave, blur lub focusout:
Jest to techniczne uogólnienie powyższych punktów. Jeśli strona internetowa używa JavaScriptu do nasłuchiwania na te konkretne zdarzenia w celu ukrycia jakiegoś elementu (np. poprzez zmianę jego stylu display na none lub dodanie klasy ukrywającej), "Freeze" skutecznie to zablokuje.
Czego "Freeze" NIE może zamrozić?
Ważne jest, aby rozumieć ograniczenia tej funkcji. Nie jest to uniwersalne narzędzie do zatrzymywania wszystkich dynamicznych zmian na stronie.
1. Elementy ukrywane przez zdarzenie click:
Scenariusz: Masz menu typu akordeon. Kliknięcie na nagłówek rozwija treść, a ponowne kliknięcie ją zwija.
Ograniczenie: "Freeze" celowo nie blokuje zdarzeń click, ponieważ uniemożliwiłoby to jakąkolwiek interakcję ze stroną, w tym samo rozwinięcie menu.
2. Elementy zamykane przez timer (setTimeout):
Scenariusz: Na stronie pojawia się komunikat "toast" (np. "Produkt dodany do koszyka"), który automatycznie znika po 3 sekundach.
Ograniczenie: Funkcja "Freeze" nie wstrzymuje ani nie blokuje działania timerów JavaScript. Komunikat zniknie zgodnie z zaprogramowanym czasem.
3. Elementy ukrywane przez zdarzenia inne niż te blokowane:
Scenariusz: Okno modalne (pop-up) zamyka się, gdy użytkownik zaczyna przewijać stronę (zdarzenie scroll).
Ograniczenie: "Freeze" blokuje tylko 4 konkretne zdarzenia. Jeśli strona używa innych, np. scroll, resize czy keydown, do ukrywania elementów, nie zostaną one zablokowane.
4. Efekty wizualne oparte wyłącznie na CSS (:hover):
Scenariusz: Kolor przycisku zmienia się, gdy najedziesz na niego myszą, dzięki regule CSS: button:hover { background-color: red; }.
Ograniczenie: Efekty :hover są obsługiwane bezpośrednio przez silnik renderujący przeglądarki, a nie przez JavaScript. "Freeze" działa na poziomie zdarzeń JavaScript, więc nie ma wpływu na czyste pseudoklasy CSS. Kolor przycisku nadal wróci do normy po zjechaniu z niego kursorem.
Podsumowanie techniczne: Jak to działa?
"Freeze" działa poprzez dodanie globalnych nasłuchiwaczy zdarzeń w fazie przechwytywania (capture: true). Oznacza to, że przechwytuje zdarzenia mouseout, mouseleave, blur i focusout na samym szczycie drzewa DOM, zanim dotrą one do docelowych elementów. Następnie natychmiast wywołuje na nich metodę event.stopPropagation(), co skutecznie uniemożliwia ich dalsze przetwarzanie przez skrypty strony.
Złota zasada: Jeśli coś na stronie znika, gdy zjeżdżasz z tego myszą lub klikasz obok, "Freeze" ma dużą szansę to "zamrozić".
