# Концепция основанная на модели
В основе лежит идея того что всю ответственность о состоянии сущности и её логики можно привязать к моделе.

## Термины

### Test сase
Сущность, которая собирает в себе:
* информацию о предмете проверки
* информацию о том какие состояния может принимать(фича тоглы и а/б), 
может быть релизованна как теги или кастомизированно при необходимости за счет структуры тест кейса
* вариации шагов и датасэтов для различных состояний

Изменение происходит на двух уровнях:
1. Изменение общей информации
1. Изменение вариации

Может быть типизирован для упрощения реализации.
Например, может быть простым в случае если имеет только одну вариацию и сложным в случае с несколькими.

### Вариация
Шаги и датасеты описывающие, как в той или иной ситуации(например для разных позиций фича тоглов) мы будем проходить данный тесткейс

### Ветвь
Это набор тесткейсов, которые должны быть изменены с изменением текущего функционала.

## Бизнес логика

### Создание
Тесткейс создается просто как модель.

### Редактирование 
Редактирование орфографии делается сразу в мастер. 
Не позволяет редактировать больше чем определенное кол-во информациию

Редактирование логики происходит через блокировку оригинала.
И создание только одной копии в которую вносятся изменения в ветке куда забрали тесткейс.

tco - оригинал тесткейса

tcc - копия для редактирования
  
``` 
          tcc
          -------------------
         /                   \
--------------------------------------------------------->
tco
```

* В момент когда создана копия tco блокируется на изменение и удаление.
* В момент когда измененный тесткей мержится в основной, старые тесткейс уходит в историю и полностью заменяется новым.
* Пока в копию не было внесены изменения, допускается редактирование tco на орфографию.

### Удаление
Удаление происходит просто отправкой в архив тесткейса.

### Версионирование
Построено на последовательности тест кейсов в архиве.
