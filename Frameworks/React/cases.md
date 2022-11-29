# React 解決問題集

## 遞迴渲染樹物件

```typescript
type Tree = {
  name?: string;
  nodes?: Tree[];
};

type RenderTreeProps = {
  tree?: Tree;
};

const RenderTree = ({tree}: RenderTreeProps) => {
  return (
    <div key={tree.name}>{tree.name}</div>
    {tree.nodes?.map((node) => {
        // Recursive render child component
        return <RenderTree key={child.name} />;
    })}
  )
}
```
