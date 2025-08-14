A simple and flexible React utility that adds Infinite Scroll and Pagination to your components.

Features
🔁 Infinite scrolling with IntersectionObserver
🔢 Simple and elegant pagination UI
⚛️ Built for React apps
🪶 Lightweight and easy to use

Install the package using npm:

npm i @rupeshkumar28/scroll-paginator

```
import React, { useState, useEffect } from 'react';
import { InfiniteScroll } from "@rupeshkumar28/scroll-paginator";

const MyComponent = () => {
  const [items, setItems] = useState([]);
  const [hasMore, setHasMore] = useState(true);

  const loadMoreItems = () => {
    const newItems = Array.from({ length: 10 }, (_, index) => ({
      id: items.length + index + 1,
      name: `Item ${items.length + index + 1}`,
    }));

    setItems(prev => [...prev, ...newItems]);

    if (items.length + newItems.length >= 50) {
      setHasMore(false);
    }
  };

  useEffect(() => {
    loadMoreItems();
  }, []);

  return (
    <InfiniteScroll items={items} loadMore={loadMoreItems} hasMore={hasMore}>
      {items.map(item => (
        <div key={item.id}>{item.name}</div>
      ))}
    </InfiniteScroll>
  );
};

export default MyComponent;
```
