# Dijkstra Алгоритмын Бодлогууд

## 1. 743. Network Delay Time

- **Өгүүлбэр:**
  N ширхэг node болон `times[i] = (uᵢ, vᵢ, wᵢ)` хэлбэрийн directed edge өгөгдөнө. Эх үүсвэр K–оос дохио илгээхэд бүх node хүрэхэд хамгийн бага хугацаа хэд вэ? Хэрвээ зарим node хүрэх боломжгүй бол -1 буцаа.
- **Оролт:**
  `times = [[2,1,1],[2,3,1],[3,4,1]], N = 4, K = 2`
- **Гаралт:**
  `2`
- [LeetCode холбоос](https://leetcode.com/problems/network-delay-time/?utm_source=chatgpt.com)

---

## 2. 1631. Path With Minimum Effort

- **Өгүүлбэр:**
  m×n хэмжээтэй `heights` хүснэгт өгөгдөнө. `(0,0)`-оос `(m‑1,n‑1)` хүртэл дээш, доош, зүүн, баруун чиглэлд шилжиж болно (диагональгүй). Замын “effort” нь adjacent хоёр нүдний өндөрний абсолют зөрүүний хамгийн их утга. Бүх боломжит замын дундаас энэ “effort”-ийг хамгийн бага болго.
- **Оролт:**
  `heights = [[1,2,2],[3,8,2],[5,3,5]]`
- **Гаралт:**
  `2`
- [LeetCode холбоос](https://leetcode.com/problems/path-with-minimum-effort/?utm_source=chatgpt.com)

---

## 3. 1514. Path With Maximum Probability

- **Өгүүлбэр:**
  n ширхэг node (0‑оос n‑1 хүртэл) бүхий undirected weighted граф өгөгдөнө. `edges[i] = [a,b]`, `succProb[i]` = тэр edge-ээр дамжих амжилтын магадлал. Эх node = start, зорилт node = end. Start → End хүртэлх замын дундаас хамгийн өндөр амжилттай магадлалтай замын магадлалыг ол. Зам байхгүй бол 0.
- **Оролт:**
  `n = 3, edges = [[0,1],[1,2],[0,2]], succProb = [0.5,0.5,0.2], start = 0, end = 2`
- **Гаралт:**
  `0.25`
- [LeetCode холбоос](https://leetcode.com/problems/path-with-maximum-probability/?utm_source=chatgpt.com)

---

## 4. 787. Cheapest Flights Within K Stops

- **Өгүүлбэр:**
  n ширхэг хотууд, нислэгийн жагсаалт `flights = [u,v,цэнэ]` өгөгдөнө. Эх = src, зорих = dst, K хүртэл завсрын зогсоолтой арга замыг ашиглан src → dst хүртэлх хамгийн бага үнэтэй нислэгийн үнэ ол. Хэрвээ боломжгүй бол -1.
- **Оролт:**
  `n = 3, flights = [[0,1,100],[1,2,100],[0,2,500]], src = 0, dst = 2, K = 1`
- **Гаралт:**
  `200`
- [LeetCode холбоос](https://leetcode.com/discuss/study-guide/5681074/Master-Graph-Theory%3A-The-Ultimate-Guide-to-Graph-Algorithms%21/?utm_source=chatgpt.com)

---

## 5. 505. The Maze II

- **Өгүүлбэр:**
  `maze` хүснэгт (0 = чөлөөтэй, 1 = хана) өгөгдөнө. Бөмбөг эхлэн байрлаад хананд тултал өнхрөнө, зогсох боломжгүй. Эхлэх бааз = start, зорилт = destination. Хөгжмийн замын урт (хөдөлгөөнүүдийн тоо) хамгийн бага болох өнхрөх замын уртыг ол. Зам байхгүй бол -1.
- **Оролт:**
  `maze = [[0,0,1,0,0],[0,0,0,0,0],[0,0,0,1,0],[1,1,0,1,1],[0,0,0,0,0]], start = [0,4], destination = [4,4]`
- **Гаралт:**
  `12`
- [LeetCode холбоос](https://leetcode.com/discuss/study-guide/5681074/Master-Graph-Theory%3A-The-Ultimate-Guide-to-Graph-Algorithms%21/?utm_source=chatgpt.com)
