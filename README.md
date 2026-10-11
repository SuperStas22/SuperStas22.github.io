# Сайт-визитка — Станислав Малашкеевич

Статический сайт, готовый к бесплатному хостингу на GitHub Pages.

```
index.html        визитка (RU/EN)
metalcrow/        лендинг проекта MetalCrow (распакован из standalone-бандла)
  index.html
  assets/         картинки, видео, шрифты, рантайм
metalcrow-nogh/   тот же лендинг без ссылок на GitHub-репозиторий
  index.html      (ассеты берёт из ../metalcrow/assets/)
resume.pdf        резюме
favicon.svg
.nojekyll         отключает обработку Jekyll на GitHub Pages
```

Ссылка «MetalCrow» в списке проектов ведёт на `metalcrow-nogh/` — лендинг лежит рядом,
внутри того же сайта, отдельный хостинг не нужен.

## Публикация на GitHub Pages

1. Создать пустой репозиторий на GitHub.
   * Хочется адрес `https://<логин>.github.io/` — назвать репозиторий `<логин>.github.io`.
   * Иначе адрес будет `https://<логин>.github.io/<репозиторий>/`.
2. Из этой папки:

```bash
git init                       # уже сделано
git remote add origin https://github.com/<логин>/<репозиторий>.git
git branch -M main
git push -u origin main
```

3. В репозитории: **Settings → Pages → Build and deployment → Deploy from a branch**,
   ветка `main`, папка `/ (root)`. Через минуту сайт откроется по адресу выше.

## Свой домен

В **Settings → Pages → Custom domain** вписать домен, у регистратора добавить записи:

* apex-домен (`example.com`): четыре A-записи на `185.199.108.153`, `185.199.109.153`,
  `185.199.110.153`, `185.199.111.153`;
* поддомен (`www.example.com`): CNAME на `<логин>.github.io`.

Дальше включить **Enforce HTTPS**.

## Правки

* Тексты, проекты, контакты — прямо в `index.html`, RU и EN лежат рядом
  в парах `<span class="ru">` / `<span class="en">`.
* Палитра — переменные в `:root` в начале `index.html`.
* После правок: `git add -A && git commit -m "..." && git push`.

## Про лендинг MetalCrow

Исходный `MetalCrow Landing Final (standalone).html` (30 МБ) — самораспаковывающийся
бандл: все ассеты лежали внутри в base64 и разворачивались в blob-ссылки скриптом.
Для Pages он распакован в обычные файлы (`metalcrow/index.html` + `metalcrow/assets/`),
поэтому страница грузится сразу, а браузер кэширует видео и шрифты по отдельности.
