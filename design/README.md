### context
> [原文件](../packages/react-router/index.tsx)

#### [NavigationContext](https://api.codestream.com/c/X-vb0kCFvXvIJGWz/akq99plWSrSgLOmVeIkYow)
`NavigationContext.Provider` 作为 `Router` 的顶层包裹

```ts
interface NavigationContextObject {
  basename: string;
  navigator: Navigator;
  static: boolean;
}

const NavigationContext = React.createContext<NavigationContextObject>(null!);
```


#### [LocationContext](https://api.codestream.com/c/X-vb0kCFvXvIJGWz/APwsWmJfTuaZjzXQgUOoQA)

`LocationContext.Provider` 同样作为 `Router` 的顶层包裹（被 `NavigationContext.Provider` 包裹）

```ts
interface LocationContextObject {
  action: Action;
  location: Location;
}

const LocationContext = React.createContext<LocationContextObject>(null!);
```

#### [RouteContext](https://api.codestream.com/c/X-vb0kCFvXvIJGWz/jHd4RbhqTSyZ4IJ9AWvOfg)

`RouteContext.Provider` 包裹路由组件

```ts
interface RouteContextObject {
  outlet: React.ReactElement | null;
  matches: RouteMatch[];
}

const RouteContext = React.createContext<RouteContextObject>({
  outlet: null,
  matches: []
});
```

### 几个 hooks
#### useRoutes

#### useNavigate

返回 `navigate` 函数

```ts
export interface NavigateFunction {
  (to: To, options?: NavigateOptions): void;
  (delta: number): void;
}
```


#### useParams
返回匹配路由的参数

```ts
type Params<Key extends string = string> = {
  readonly [key in Key]: string | undefined;
}

type UseParams = <Key extends string = string>() => Readonly<Params<Key>>
```

#### useHref
用于获取完整 href

```ts
type UseHref = (to: To) => string
```

#### useLocation
用于获取当前 location

#### useMatch
用于判断指定 pattern 是否匹配当前 url，如果匹配则返回对应的 match 对象

```ts
type UseMatch<ParamKey extends string = string>(
  pattern: PathPattern | string
): PathMatch<ParamKey> | null
```

#### useNavigationType
用于获取当前导航的 action 类型：POP、PUSH、REPLACE