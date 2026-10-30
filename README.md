# PDA_Assignment_2

---

## Findings: how income, jobs and health fit together

The data are World Bank indicators for about 218 countries, 2000-2024: GDP per capita (current US$), life expectancy at birth, and the unemployment rate. Regional and income-group aggregates (World, Euro area and so on) were removed so countries are not double counted. All code, figures and caveats are in [notebooks/gdp_per_capita.ipynb](notebooks/gdp_per_capita.ipynb); each question below names its section and figure.

**How to read the numbers.** *ρ* (rho) is a rank correlation: +1 means two things always rise together, 0 means no link, -1 means one rises as the other falls. Values near 0.1 are weak, around 0.5 moderate and above 0.8 strong. *Intervals* in brackets are 95% ranges from resampling countries; when two intervals do not overlap, the difference is unlikely to be chance. GDP is in current US$ and life expectancy is at birth. Country-level figures are medians, so every country counts equally whatever its population.

**The one-paragraph story.** Income and health travel together: richer countries live far longer, and this held in every year and even through the pandemic. Jobs are the odd one out: unemployment is not connected to income or health across countries, and only loosely follows the economy inside a country. The exceptions are informative: a few rich countries with high unemployment (Spain above all), and poor countries that live much longer than their income predicts (Tajikistan, the Kyrgyz Republic, Nepal). Continents differ enormously in income and health, Africa made the largest health gains of the period, and none of that rested on the fastest economic growth.

### 1. How are GDP per capita, unemployment, and life expectancy related across countries from 2000 to 2024?

**Short answer: GDP and life expectancy are strongly linked; unemployment is unrelated to either.** (Notebook section 2, Figures 1-2.)

*The story.* Plotting every country-year, GDP per capita and life expectancy rise together with **ρ ≈ 0.87**. Each tenfold increase in GDP per capita goes with about **10.5 more years of life**, with diminishing returns at high incomes. The link was just as strong in every single year (ρ between **0.85 and 0.88**). Unemployment, by contrast, has essentially no relationship with GDP or life expectancy (|ρ| below **0.1**), and year by year it drifts between about **-0.24 and +0.15** with no consistent direction.

| Pair | ρ (all country-years) | Reading |
|---|---|---|
| GDP per capita vs life expectancy | about 0.87 | Strong, stable every year |
| GDP per capita vs unemployment | below 0.1 in size | No link |
| Life expectancy vs unemployment | below 0.1 in size | No link |

*Caveat.* Correlation is not causation; unemployment is reported for only about 58% of country-years.

### 2. Do countries with higher GDP per capita tend to have lower unemployment rates?

**Short answer: no across countries, but yes inside a country over time.** (Section 3, Figures 3-4.)

*The story.* Across **170 countries**, average GDP per capita says nothing about average unemployment (**ρ = 0.05, p ≈ 0.5**). The pattern is hump-shaped, not a slope: median unemployment is lowest in the poorest quartile (**4.6%**) and richest quartile (**5.6%**) and highest in the middle (about **8.5%**). Poor countries report low open unemployment largely because most people work informally and cannot afford to be unemployed.

Inside a single country the pattern is different: in **76% of 146 countries**, unemployment was lower in the years when GDP per capita was higher. Rising GDP per capita is a reasonable rough signal that unemployment is easing in one country, but not a way to rank countries.

*Caveat.* Unemployment uses national definitions, and GDP in current US$ mixes real growth with inflation and exchange rates.

### 3. Do countries with higher GDP per capita tend to have longer life expectancy?

**Short answer: yes, clearly.** (Section 4, Figure 5.)

*The story.* Using each country's 2000-2024 average, each tenfold increase in GDP per capita goes with about **10.9 more years of life expectancy**. Sorting countries into income quartiles shows the staircase: median life expectancy is **61.1** years in the poorest quartile, **70.4** in lower-middle, **74.2** in upper-middle and **80.5** in the richest. The biggest single step, about **9 years**, is from the poorest group to the next, so gains are largest when moving out of the lowest incomes.

| Income quartile | Median life expectancy (years) |
|---|---|
| Low | 61.1 |
| Lower-middle | 70.4 |
| Upper-middle | 74.2 |
| High | 80.5 |

*Caveat.* Not causation (health also raises productivity), and GDP is not adjusted for local prices.

### 4. Within each country, how do changes in GDP per capita relate to changes in unemployment?

**Short answer: in the direction you would expect, but weakly.** (Section 5, Figure 6.)

*The story.* Comparing each country's yearly GDP growth with the change in its unemployment rate, the typical country has a correlation of **-0.29**: faster growth goes with falling unemployment. Nearly half of countries (**48%**) are below -0.3 and only **2%** are above +0.3, so almost no country shows unemployment rising systematically when GDP grows. But the effect is small: **1 percentage point** more growth goes with only about **0.03 percentage points** lower unemployment. Growth years are better and recession years worse, but the size of the swing is driven by other things.

*Caveat.* Unemployment often responds to GDP with a lag of a year or more, which same-year changes miss.

### 5. Within each country, how do changes in GDP per capita relate to changes in life expectancy?

**Short answer: over the long run they move together; from year to year the link is faint.** (Section 6, Figure 7.)

*The story.* Over time, **99% of 214 countries** show GDP and life expectancy rising together (median ρ = **0.79**). But that is largely both series trending upward. Comparing yearly changes, the typical country's correlation is only **0.12** (pooled **0.10** across 5,048 country-years), though the direction is still mostly positive: **65% of 213 countries** are positive, **25%** above +0.3 and only **5%** below -0.3. In size, **1 point** more growth goes with only about **0.007 more years** of life expectancy. Dropping 2020-2021, when COVID-19 hit both, changes the pooled figure only from 0.10 to **0.09**.

| View | Median ρ within countries | Share of countries positive |
|---|---|---|
| Levels over time | 0.79 | 99% (of 214) |
| Yearly changes | 0.12 | 65% (of 213) |

*Caveat.* Health effects of income can arrive years later, which same-year changes miss.

### 6. How is unemployment related to life expectancy?

**Short answer: essentially not related, apart from a hint among the richest countries.** (Section 7, Figure 8.)

*The story.* Across **170 countries**, average unemployment and life expectancy are unrelated (**ρ = 0.02, p = 0.84**). Year-to-year changes inside countries agree: median ρ **-0.01**, **49%** of 120 countries positive, pooled **-0.02** (n = 2,639).

Income hides a small pattern. Within income quartiles the correlation runs from **+0.14** (low) and **+0.01** (lower-middle) to **-0.16** (upper-middle) and **-0.37** (high): among the richest countries, higher unemployment goes with somewhat lower life expectancy. With only about 40 countries per group, that is suggestive, not firm. Tracking countries over time, levels lean negative (median ρ **-0.28**, only **32%** of 146 countries positive), but yearly changes show nothing, which points to a shared long-run drift and not a year-by-year effect.

| Income quartile | ρ between countries |
|---|---|
| Low | +0.14 |
| Lower-middle | +0.01 |
| Upper-middle | -0.16 |
| High | -0.37 |

*Caveat.* Unemployment in poorer countries understates joblessness because of informal work.

### 7. Which countries have high GDP per capita but also high unemployment?

**Short answer: only four of the 43 rich countries, led by Spain.** (Section 8, Figure 9.)

*The story.* "High" was defined by quartile: GDP per capita of at least **$26,452** (top quartile) and average unemployment above **9.9%** (top quartile), on 2000-2024 averages. Of **43 high-GDP countries**, just **4** also have high unemployment. Spain stands out at **15.4%**, well ahead of the next. It is the only large economy on the list and has high life expectancy (**81.9** years). The others are small territories or island economies. Just under the line sit Guam and Greenland (9.6%), Italy (9.2%) and France (8.8%), so the list is sensitive to the cut-off.

| Country | GDP per capita (US$) | Unemployment (%) | Life expectancy (years) |
|---|---|---|---|
| Spain | 27,905 | 15.4 | 81.9 |
| New Caledonia | 30,465 | 12.6 | 76.3 |
| Puerto Rico (US) | 27,149 | 11.3 | 78.9 |
| Bahamas, The | 29,740 | 10.9 | 73.4 |

*Caveat.* Averages over 2000-2024 hide large swings, such as Spain's peak after 2008, and the reasons given for the island economies are plausible explanations, not tested here.

### 8. Which countries have low GDP per capita but relatively high life expectancy?

**Short answer: none beat the world median, but several live much longer than their income predicts.** (Section 9, Figure 10.)

*The story.* Of the **54 countries** in the poorest quartile (average GDP per capita of **$1,743 or less**), **none** exceeds the all-country median life expectancy of **72.4 years**, so income still sets a ceiling. "Relatively high" therefore means above what income predicts. The biggest overperformers are mostly in Central and South Asia: Tajikistan reaches **68.5 years on about $716 per person**, **7.8 years above** the income trend, followed by the Kyrgyz Republic (+7.4), Nicaragua (+6.7), Syria (+6.4), Nepal (+6.1) and Bangladesh (+5.5). These are good places to look for low-cost health gains that income does not explain.

| Country | GDP per capita (US$) | Life expectancy (years) | Above trend (years) |
|---|---|---|---|
| Tajikistan | 716 | 68.5 | +7.8 |
| Kyrgyz Republic | 1,044 | 69.9 | +7.4 |
| Nicaragua | 1,720 | 71.6 | +6.7 |
| Syrian Arab Republic | 1,422 | 70.5 | +6.4 |
| Nepal | 752 | 67.1 | +6.1 |
| Bangladesh | 1,230 | 68.8 | +5.5 |

*Caveat.* Syria's long-run average is pulled down by the war years, and why these countries do well is not tested here.

---

## Findings for questions 9-12: did anything change, and where?

Questions 9-12 ask whether that picture is stable: first across time (before and after 2020), then across the world (by continent). Notebook sections 10-13, Figures 11-14.

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