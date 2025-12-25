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


## 5) Hooks

1) Context hooks (useContext)
2) State hooks (useState)
3) Ref hooks (useRef)
4) External Library hooks (useRouter, useForm, useQuery etc.)
5) Custom hooks
6) useMemo
7) useCallback
8) useEffect

## 6) Early Returns (Guard Clauses)

```ts
if (!isActive) return null;

if (isLoading) {
  return <div>Loading...</div>;
}
```


## 7) Render Functions

```ts
const renderFriends = () =>
  friends.map((friend) => (
    <li key={friend.id}>{friend.name}</li>
  ));
```


## 8) JSX Return