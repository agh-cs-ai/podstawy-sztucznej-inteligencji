# Spis treści

* [Regresja liniowa i logistyczna](lab1)
* [Lasy decyzyjne i boosting](lab2)
* [Sieci neuronowe](lab3)
* [Rozpoznawanie obrazów](lab4)
* [Przetwarzanie języka naturalnego](lab5)
* [Algorytmy rekomendacyjne](lab6)
* [Podejmowanie decyzji](lab7)

# Ekstrakcja rozwiązań z notebooków

Służy do tego skrypt `extract_solutions.py`. Podajemy mu katalog, w którym w podkatalogach są rozwiązania studentów (może być to być rozpakowane archiwum ściągnięte z UPELa):

```
python ./extract_solutions.py --directory ../grupy/2024-25/lab-1/
```

![image](https://github.com/user-attachments/assets/d9af158f-ab70-41f0-99e6-e51d23d18476)

Dzięki temu obok każdego notebooka mamy dodatkowy plik `_solutions`, który zawiera same rozwiązania.

# Praca nad projektem

Synchronizacja `.py` z `.ipynb`:

1. Ustaw formaty dla notatnika:
  `uv run jupytext --set-formats ipynb,py:percent notebook.ipynb`
2. Zsynchronizuj zawartość notatnika i kod Pythona (jest to wykonywane automatycznie przy każdym zapisie, jeśli formaty są zsynchronizowane):
  `uv run jupytext --sync notebook.py`
3. Ponownie wygeneruj notatnik z kodu Pythona (np. po scaleniu z wieloma konfliktami):
  * `rm notebook.ipynb`
  * `uv run jupytext --to ipynb notebook.py`

Po ponownym wygenerowaniu notatnika wszystkie załączniki (np. obrazy) zostaną usunięte. Musisz je ponownie dodać do ipynb ręcznie.

# Aktualizacja za pomocą git (konflikty)

Przepis na rozwiązywanie konfliktów:

1. `git pull origin branch-x` (powiedzmy, że ktoś przesłał kilka commitów do gałęzi, nad którą pracujemy).
2. Teraz mamy konflikt w `.py` i `.ipynb`.
3. Rozwiązujemy konflikt ręcznie w `.py`.
4. Bierzemy ich (`theirs`) wersję ipynb:
  `git checkout --theirs lecture.ipynb`
5. Synchronizujemy pliki py i ipynb:
  `uv run jupytext --sync lecture.py`
