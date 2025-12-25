## 1) Imports

1) React
2) external libraries
3) UI components
4) hooks
5) utils/helpers
6) styles

#### Example

```ts
import { useState, useEffect, useMemo, useCallback } from "react";
import clsx from "clsx";

import { Button } from "@/components/ui/button";
import { fetchUsers } from "@/lib/api";

import styles from "./UserCard.module.css";
```


## 2) Types / Interfaces

1) Enums
2) Local Types
3) Props

#### Example

```ts
enum Role {
  ADMIN = "ADMIN",
  USER = "USER"
}

type User = {
  id: string;
  name: string;
  role: Role;
};

interface UserCardProps {
  user: User;
  isActive?: boolean;
}
```


## 3) Constants

```ts
const MAX_FRIENDS = 50;
const MIN_USERNAME_LENGTH = 3;
```


## 4) Function Component Declaration

```ts
export function UserCard({ user, isActive = true }: UserCardProps) {
```


## 5) States (useState)


## 6) Refs (useRef)


## 7) Memos (useMemo)


## 8) Callbacks / Handlers (useCallback)


## 9) Effects (useEffect)


## 10) Early Returns (Guard Clauses)

```ts
if (!isActive) return null;

if (isLoading) {
  return <div>Loading...</div>;
}
```


## 11) Render Functions

```ts
const renderFriends = () =>
  friends.map((friend) => (
    <li key={friend.id}>{friend.name}</li>
  ));
```


## 12) JSX Return