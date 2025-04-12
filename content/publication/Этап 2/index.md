---
title: "Этап 2. Алгоритмы"
authors:
- admin
- Коннова Татьяна
- Нефедова Наталья
- Уткина Алина
- Тарутина Кристина
date: "2025-04-01T00:00:00Z"

params:
  math: true
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2025-04-01T00:00:00Z"

# Publication type.
# Accepts a single type but formatted as a YAML list (for Hugo requirements).
# Enter a publication type from the CSL standard.
#publication_types: ["article"]

# Publication name and optional abbreviated publication name.
publication: ""
publication_short: ""

tags:
- Этапы
featured: false

links:
- name: Rutube
  url: https://rutube.ru/video/private/68968e0dacd41d58868657eaccf99efa/?p=ZAbQ22IaQNxHTecMGIFx8w
- name: Платформа
  url: https://plvideo.ru/watch?v=ZgYDECXtSDIk
#url_pdf: http://arxiv.org/pdf/1512.04133v1
#url_code: 'https://github.com/HugoBlox/hugo-blox-builder'
#url_dataset: '#'
#url_poster: '#'
#url_project: ''
#url_slides: ''
#url_source: '#'
#url_video: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
#image:
#  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/s9CC2SKySJM)'
#  focal_point: ""
#  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
#projects:
#- internal-project

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
#slides: example
---

# Цель работы

Дать теоретическое описание алгоритмам, которые будут использованы для моделирования задачи образования планетной системы

# Формулировка решаемой системы 

Моделируется образование планетной системы из межзвездного газа, который представляется как скопление частиц.
Так как число моделируемых частиц весьма ограничено, то можно сказать, что в этой модели планеты образуются из уже сформировавшихся газопылевых уплотнений, которыми и являются задаваемые частицы.

Движение частиц описывается с помощью Второго закона Ньютона:

$$
m_i \frac{d^2\mathbf{r}_i}{dt^2} = \mathbf{F}_i.
$$

То есть систему $N$ уравнений второго порядка, которую можно переписать как систему $2N# уравнений первого порядка:

$$
\frac{d\mathbf{r}_i}{dt} = \mathbf{v}_i,
$$

$$
\frac{d\mathbf{v}_i}{dt} = \mathbf{a}_i,
$$

где $\mathbf{a}_i = \frac{\mathbf{F}_i}{m_i}$ -- ускорение частиц, $\mathbf{v}_i$ - ее скорость.

Полученная система дополняется начальными условиями для формулировки задачи Коши, что уже позволяет искать решение системы:


\\[ \mathbf{r}\_{i}(t = 0) =\mathbf{r}\_{i0} \\]

$$
\mathbf{v}\_i(t = 0) = \mathbf{v}\_{i0}.
$$

# Алгоритм Верле

Наивный подход подразумевает расчет вычисление взаимодействия каждой частицы с каждой, что требует $N^2$ операций ($N$ - число частиц в системе). 

Численное решение полученной системы будем решать с помощью алгоритма Верле, имеющим следующий вид:

$$
\mathbf{r}\_{i}^{n+1} = \mathbf{r}\_{i}^{n} +\mathbf{v}\_{i}^{n} \cdot \Delta t+ \mathbf{a}\_{i}^{n} \cdot \frac{\Delta t^{2}}{2}, 
$$

$$
\mathbf{v}\_{i}^{n+1} = \mathbf{v}\_{i}^{n} + \frac{1}{2}( \mathbf{a}\_{i}^{n} + \mathbf{a}\_{i}^ {n+1}) \Delta t.
$$

Для оптимизации хранения промежуточных значений можно переписать схему, тогда отпадет необходимость хранить значения ускорений на двух шагах по времени одновременно:


$$
\mathbf{v}_ {i}^{n+1/2}  =  \mathbf{v}_ {i}^ {n}  +  \mathbf{a}_ {i}^ {n}  \cdot  \frac {\Delta t}{2} 
$$ 
$$
\mathbf{r}_ {i}^ {n+1}  =  \mathbf{r}_ {i}^ {n}  +  \mathbf{v}_ {i}^ {n+1/2}  \Delta t
$$
$$
\mathbf{v}_ {i}^ {n+1} =  \mathbf{v}_ {i}^ {n+1} + \mathbf{a}_i^{n+1} \frac {\Delta t}{2} 
$$

Ускорение частицы будет складываться их нескольких явлений:

  * Гравитационное притяжение: $F = \frac{\gamma m_i m_j}{r^2_{ij}}$
  * Сила отталкивания: $F^r(b) = k\left(\left(\frac{a}{b}\right)^8-1\right)$, 
  
  где $a = R_i + R_j$ -- сумма радиусов частиц $i$ и $j$, $b$ -- модуль радиус-вектора взаимодействия $\mathbf{b} = \mathbf{r}_{i,j} = \mathbf{r}_i − \mathbf{r}_j$

# Выводы

Дано описание алгоритмам, которые будут использоваться для численной реализации моделирования задачи образования планетной 
системы.


