# Scroll Paginator

A React utility for implementing **infinite scrolling** and **pagination** with hooks and components.

## Installation

To install the package, run:

```bash
npm install scroll-paginator



## Usage

### 1. **Infinite Scroll**

The `InfiniteScroll` component allows you to implement infinite scrolling. It will load more data as the user scrolls to the bottom of the list.

#### Example Usage:

```tsx
import React, { useState, useEffect } from 'react';
import { InfiniteScroll } from 'scroll-paginator';

const MyComponent = () => {
  const [items, setItems] = useState<any[]>([]);
  const [hasMore, setHasMore] = useState<boolean>(true);

  const loadMoreItems = async () => {
    // Simulate loading more items (e.g., from an API)
    const newItems = Array.from({ length: 10 }, (_, index) => ({
      id: items.length + index + 1,
      name: `Item ${items.length + index + 1}`,
    }));

    setItems((prevItems) => [...prevItems, ...newItems]);

    // Stop fetching when you reach 50 items (example)
    if (items.length + newItems.length >= 50) {
      setHasMore(false);
    }
  };

  useEffect(() => {
    loadMoreItems();
  }, []);

  return (
    <InfiniteScroll
      items={items}
      loadMore={loadMoreItems}
      hasMore={hasMore}
    >
      {items.map((item) => (
        <div key={item.id}>{item.name}</div>
      ))}
    </InfiniteScroll>
  );
};

export default MyComponent;




### 2. **Pagination**

The `Pagination` component allows you to implement a pagination system. It helps you display a subset of data and navigate between pages.

#### Example Usage:

```tsx
import React, { useState } from 'react';
import { Pagination } from 'scroll-paginator';

const MyComponent = () => {
  const [currentPage, setCurrentPage] = useState<number>(1);
  const totalPages = 10; // Assume we have 10 pages of data

  const handlePageChange = (page: number) => {
    setCurrentPage(page);
    // You can fetch new data based on the page here
  };

  return (
    <div>
      <Pagination
        currentPage={currentPage}
        totalPages={totalPages}
        onPageChange={handlePageChange}
      />
      <p>Current Page: {currentPage}</p>
    </div>
  );
};

export default MyComponent;



## API Reference

### **InfiniteScroll**

#### Props

| Prop         | Type      | Description                                                                 |
|--------------|-----------|-----------------------------------------------------------------------------|
| `items`      | `Array`   | List of items to display.                                                   |
| `loadMore`   | `Function`| Function that triggers loading more items (e.g., fetch more items from an API).|
| `hasMore`    | `Boolean` | Whether there are more items to load (e.g., `true` to continue loading).    |

### **Pagination**

#### Props

| Prop           | Type      | Description                                                                  |
|----------------|-----------|------------------------------------------------------------------------------|
| `currentPage`  | `Number`  | The current active page number.                                               |
| `totalPages`   | `Number`  | The total number of pages.                                                   |
| `onPageChange` | `Function`| A function that gets called when the page changes. It receives the new page number. |

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Contributing

If you'd like to contribute to this project, feel free to fork the repository and submit a pull request. You can also report issues or suggest new features by opening an issue on the GitHub repository.

---

## Changelog

### v1.0.0
- Initial release with Infinite Scroll and Pagination components.

---

## Known Issues

If you encounter any issues or bugs, please report them by opening an issue in the GitHub repository.

