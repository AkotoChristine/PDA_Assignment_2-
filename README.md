# PDA_Assignment_2

Main questions to answer
- How are GDP per capita, unemployment, and life expectancy related across countries from 2000 to 2024?
- Do countries with higher GDP per capita tend to have lower unemployment rates?
- Do countries with higher GDP per capita tend to have longer life expectancy?
- Within each country, how do changes in GDP per capita relate to changes in unemployment?
- Within each country, how do changes in GDP per capita relate to changes in life expectancy?
- How is unemployment related to life expectancy?
- Which countries have high GDP per capita but also high unemployment?

8. Which countries have low GDP per capita but relatively high life expectancy?
9. Did these relationships differ between 2000-2019 and 2020-2024?
10. How do the three indicators differ across continents?
11. Is the GDP-life expectancy relationship stronger in some continents than others?
12. Which continent saw the largest life expectancy gain, and how did GDP per capita change over the same period?

---

## Findings for questions 9-12: did anything change, and where?

The first eight questions established the basic picture: richer countries live longer, and unemployment is a poor guide to either income or health. Questions 9-12 ask whether that picture is stable. First across time (before and after 2020), then across the world (by continent). All code, figures and caveats are in [notebooks/gdp_per_capita.ipynb](notebooks/gdp_per_capita.ipynb), sections 10-13 (Figures 11-14).

**How to read the numbers.** *ρ* (rho) is a rank correlation: +1 means two things always rise together, 0 means no link, -1 means one rises as the other falls. Values near 0.1 are weak, around 0.5 moderate and above 0.8 strong. *Intervals* in brackets are 95% ranges from resampling countries; when two intervals do not overlap, the difference is unlikely to be chance. GDP is in current US$ and life expectancy is at birth. Country-level figures are medians, so every country counts equally whatever its population.

### 9. Did these relationships differ between 2000-2019 and 2020-2024?

**Short answer: almost not at all, with one exception.** Even through the COVID-19 years, the world's economic and health patterns kept the same shape.

*The story.* The link between income and health survived the pandemic intact. Across countries, GDP per capita and life expectancy were correlated at **ρ = 0.87** (0.83 to 0.90) before 2020 and **0.86** (0.81 to 0.89) after, and each tenfold increase in GDP per capita went with about **10.7** extra years of life before 2020 and **9.9** after. Unemployment stayed unconnected to both: its correlation with GDP was -0.05 then -0.10, and with life expectancy -0.04 then -0.05, all of them statistically indistinguishable from zero.

Inside countries, the picture was just as steady. A good year for GDP growth barely moved life expectancy (ρ = **0.10** before, **0.09** after), and growth went with falling unemployment in both periods (**-0.24** before, **-0.31** after; the intervals overlap, so this is not a clear change).

*The exception.* The one relationship that changed is the link between yearly changes in unemployment and in life expectancy. Before 2020 it was essentially zero (**ρ = 0.06**, interval 0.01 to 0.10). After 2019 it turned negative (**ρ = -0.22**, interval -0.30 to -0.14): years when unemployment rose tended to be years when life expectancy fell. The two intervals do not overlap. The likely reason is that the pandemic hit jobs and health at the same time, but this notebook does not test that explanation.

*What did slow down.* Progress itself cooled. The typical country's life expectancy gain fell from **+0.29 to +0.20 years per year**, and GDP per capita growth from **5.4% to 3.8% per year**.

| Relationship | 2000-2019 | 2020-2024 | Different? |
|---|---|---|---|
| GDP vs life expectancy (across countries) | 0.87 | 0.86 | No |
| GDP vs unemployment (across countries) | -0.05 | -0.10 | No |
| Unemployment vs life expectancy (across countries) | -0.04 | -0.05 | No |
| GDP growth vs change in life expectancy (within countries) | 0.10 | 0.09 | No |
| GDP growth vs change in unemployment (within countries) | -0.24 | -0.31 | No (intervals overlap) |
| Change in unemployment vs change in life expectancy (within countries) | 0.06 | -0.22 | **Yes** |

*Caveat.* 2020-2024 is only five years, so its estimates are less precise, and overlapping intervals are a rough guide rather than a formal test.

### 10. How do the three indicators differ across continents?

**Short answer: continents are very different in income and health, and only mildly different in unemployment.**

*The story.* The dataset has no continent column, so each country was assigned one (Middle Eastern countries are in Asia). Comparing each country's 2000-2024 average, Europe sits at the top of both income and health, with a median GDP per capita of about **$26,100** and life expectancy of **80.0 years**. Africa sits at the bottom of both, at about **$1,200** and **59.7 years**. That is a roughly 20-fold income gap and a 20-year life gap.

The middle of the table holds a surprise. Oceania has a higher median income than Asia (**$4,300 vs $3,800**) but a lower life expectancy (**69.9 vs 72.7 years**), so income is not the whole story. Unemployment tells a different tale altogether: it runs from **4.4%** in Asia to **8.4%** in South America, and it does not follow income. Africa, the poorest continent, is in the middle at **6.6%**, and wealthy Europe sits above Asia and Oceania at **7.1%**. This matches the earlier finding that income does not predict unemployment.

| Continent | Countries | GDP per capita (median, US$) | Life expectancy (median, years) | Unemployment (median, %) |
|---|---|---|---|---|
| Europe | 48 | 26,103 | 80.0 | 7.1 |
| North America | 32 | 13,317 | 74.5 | 7.8 |
| South America | 12 | 5,862 | 73.7 | 8.4 |
| Oceania | 19 | 4,257 | 69.9 | 6.1 |
| Asia | 48 | 3,798 | 72.7 | 4.4 |
| Africa | 54 | 1,245 | 59.7 | 6.6 |

The tests agree with the picture: differences between continents are overwhelming for GDP (p ≈ 9e-20) and life expectancy (p ≈ 1e-23), but only weak for unemployment (p = 0.03, which would not survive a correction for running three tests).

*Caveat.* The continent labels come from a hand-made country-code mapping, and South America has only 12 countries.

### 11. Is the GDP-life expectancy relationship stronger in some continents than others?

**Short answer: yes, in how tightly income predicts health, but not clearly in how much extra life each tenfold rise in income buys.**

*The story.* Within each continent, we asked whether richer countries live longer. In **Asia (ρ = 0.89)** and **Europe (0.81)** the answer is a firm yes: knowing a country's income tells you most of what you need to know about its life expectancy. In **Africa** the link is much weaker (**ρ = 0.45**, interval 0.19 to 0.65, clearly below both Asia's 0.78 to 0.94 and Europe's 0.69 to 0.88). African countries with similar incomes can have very different life expectancies, which points to factors other than income, such as health systems, disease burden and conflict, though this is not tested here. North America (0.65), Oceania (0.69) and South America (0.59) sit in between with intervals too wide to rank.

The *size* of the link is a different story. The extra years per tenfold income increase range from **5.8** (North America) to **10.5** (Oceania), but the intervals overlap heavily, so no continent clearly differs from the others. South America's **14.1** looks like the highest, yet its interval (3.9 to 19.3) rests on just 12 countries. One more observation: every continent's slope except South America's is below the all-country slope of **10.9** years per tenfold increase, which suggests that part of the worldwide link comes from differences *between* continents (rich Europe against poorer Africa), not only within them. This was not tested directly.

Inside countries, yearly growth barely moves life expectancy anywhere (ρ between **0.05 and 0.19**), and in Africa (0.05) and Oceania (0.06) it is not clearly different from zero.

| Continent | Countries | ρ across countries | Years per 10x GDP | ρ of yearly changes within countries |
|---|---|---|---|---|
| Asia | 48 | **0.89** (0.78-0.94) | 8.6 (7.4-9.7) | 0.13 |
| Europe | 48 | **0.81** (0.69-0.88) | 7.3 (5.9-8.6) | 0.10 |
| Oceania | 19 | 0.69 (0.30-0.88) | 10.5 (7.4-13.4) | 0.06 |
| North America | 32 | 0.65 (0.30-0.87) | 5.8 (3.0-8.2) | 0.12 |
| South America | 12 | 0.59 (-0.15-0.93) | 14.1 (3.9-19.3) | 0.19 |
| Africa | 54 | **0.45** (0.19-0.65) | 8.3 (4.6-12.1) | 0.05 |

*Caveat.* Small samples (South America 12, Oceania 19) and a narrower income range inside a continent can both lower its correlation.

### 12. Which continent saw the largest life expectancy gain, and how did GDP per capita change over the same period?

**Short answer: Africa gained the most, a median of 9.8 years per country, while its GDP per capita grew at only a middling pace.**

*The story.* Taking each country from its first to its last year of data (from 2003 or earlier to 2021 or later; 206 countries), the continent that started lowest improved most. The typical African country went from **53.1 to 65.8 years**, a gain of **9.8 years** (interval 8.3 to 10.7). The runner-up, Asia, gained **6.5** (5.4 to 7.3), entirely below Africa's range, so Africa's lead is not a statistical accident. South America followed with **5.9**, Europe with **4.7**, North America with **3.7** and Oceania with **3.4**.

Money does not explain the ranking. GDP per capita rose in every continent, but the median African country's rose **2.9 times** (about $520 to $1,720), less than Asia's **3.8 times** (the fastest), South America's **3.5**, and Europe's **3.4**, and level with Oceania's **2.9**. Only North America grew slower at **2.4**. Asia grew faster than Africa yet gained 3.3 fewer years of life. This fits the earlier finding that yearly GDP growth barely moves life expectancy: the big gains look more like catching up on basic health improvements from a low starting point than a payoff from faster growth. That reading is not tested here. The gains also survived the pandemic: the median gain up to 2019 was already **7.7** years in Africa, and each continent's gain to the last year is larger still.

| Continent | Countries | Life expectancy, start to end (years) | Median gain (years) | GDP per capita multiple |
|---|---|---|---|---|
| **Africa** | 52 | 53.1 to 65.8 | **9.8** (8.3-10.7) | 2.9x |
| Asia | 47 | 70.9 to 74.9 | 6.5 (5.4-7.3) | **3.8x** |
| South America | 12 | 70.5 to 76.8 | 5.9 (3.8-6.8) | 3.5x |
| Europe | 47 | 76.6 to 81.8 | 4.7 (4.4-5.2) | 3.4x |
| North America | 29 | 72.5 to 75.1 | 3.7 (2.9-4.6) | 2.4x |
| Oceania | 19 | 68.6 to 71.7 | 3.4 (2.7-3.8) | 2.9x |

Africa remains the lowest in level (65.8 years against Europe's 81.8), but the gap has narrowed from about 23 years to about 16.

*Caveat.* GDP is in current US$, so its change mixes real growth with inflation and exchange-rate moves, and the dollar gains are far larger in rich continents (about +$24,000 in Europe against about +$1,200 in Africa).

### The thread through questions 9-12

Taken together: **the link between income and health is stable over time but uneven across places.** It survived 2020, it is strongest in Asia and Europe and weakest in Africa, and it is not what drove the largest health gains of the period. Those went to Africa, which started lowest and did not grow fastest. Throughout, unemployment stayed the odd one out: unrelated to income or health across countries, differing little between continents, and moving together with health from year to year only in the pandemic years.