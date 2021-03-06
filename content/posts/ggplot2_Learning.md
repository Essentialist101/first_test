---
title: "ggplot2 Learning"
date: 2021-07-19T15:39:39+08:00
author: "HCZ"
draft: true
categories: [R Language]
---

### 一个简单的例子

```{r}
library(ggplot2)
ggplot(mpg, aes(displ, hwy))+
  geom_point(aes(color = class))+
  geom_smooth(se = FALSE)+
  labs(title = paste("Fuel efficiency generally decreases with engine size"))
```

```{r}
library(ggplot2)
library(dplyr)
library(gapminder)
data <- gapminder %>% filter(year=="2007") %>% dplyr::select(-year)

data %>%
  arrange(desc(pop)) %>%
  mutate(country = factor(country)) %>%
  ggplot(aes(x=gdpPercap, y=lifeExp, size = pop)) +
    geom_point(alpha=0.5) +
    scale_size(range = c(.1, 24), name="Population (M)")

data %>%
  arrange(desc(pop)) %>%
  mutate(country = factor(country, country)) %>%
  ggplot(aes(x=gdpPercap, y=lifeExp, size=pop, color=continent)) +
    geom_point(alpha=0.5) +
    scale_size(range = c(.1, 24), name="Population (M)")
```



















