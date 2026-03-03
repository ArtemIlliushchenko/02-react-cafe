# React + TypeScript + Vite
# Домашнє завдання 2 – Відгуки про кав’ярню (React + TypeScript)

## Опис
Друге домашнє завдання з TypeScript.  
Практика типізації React-компонентів, пропсів, станів, union-типів та інтерфейсів у функціональних компонентах.

Це класична «відгуки про сервіс» (аналог «Feedback Widget»), але повністю на TypeScript з чіткою типізацією всіх пропсів, станів та колбеків.

## Технології / стек
- React
- TypeScript
- Vite 
- CSS-модулі (module.css)
- Хуки: `useState`
- Union-типи (`'good' | 'neutral' | 'bad'`)
- Інтерфейси для стану та пропсів
- Умовний рендеринг
- Типізація колбеків та пропсів

## Структура проєкту

| Файл / Компонент     | Призначення                              | Основні типи / особливості                              |
|----------------------|------------------------------------------|------------------------------------------------------------------|
| src/types/votes.ts   | Типи та інтерфейси                       | `VoteType`, `Votes` (інтерфейс стану)                            |
| src/App.tsx          | Головний компонент                       | `useState<Votes>`, обчислення totalVotes та positiveRate         |
| src/components/CafeInfo/CafeInfo.tsx | Заголовок та опис кав’ярні               | Статичний компонент без пропсів                                  |
| src/components/Notification/Notification.tsx | Повідомлення «No feedback yet»           | Показується, коли totalVotes === 0                               |
| src/components/VoteOptions/VoteOptions.tsx | Кнопки Good / Neutral / Bad + Reset      | Пропси: `onVote`, `onReset`, `canReset`                          |
| src/components/VoteStats/VoteStats.tsx | Статистика відгуків                      | Пропси: `votes: Votes`, `totalVotes`, `positiveRate`             |
| src/App.module.css   | Стилі головної обгортки                  | —                                                                |
| src/components/*/module.css | Локальні стилі компонентів               | —                                                                |

## Основні типи (з types/votes.ts)

```ts
export type VoteType = 'good' | 'neutral' | 'bad';

export interface Votes {
  good: number;
  neutral: number;
  bad: number;
}
```
## Функціонал

Три кнопки для оцінки: Good / Neutral / Bad
Кнопка Reset з’являється тільки після першої оцінки (totalVotes > 0)
При відсутності голосів показується повідомлення «No feedback yet»
Автоматичний підрахунок:
Total votes
Positive feedback percentage (округлення до цілого числа)

Стан зберігається в useState<Votes>
Усі колбеки та пропси строго типізовані → TypeScript ловить помилки на етапі написання коду

## Посилання

Демо [посилання](https://02-react-cafe-yfg1.vercel.app)
