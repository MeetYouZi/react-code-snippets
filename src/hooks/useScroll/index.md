# useScroll

用于监听窗体或组件滚动的 `Hook`

## 示例

```jsx
/**
 * title: 组件滚动 demo
 */
import React from 'react'
import useScroll from './useScroll'

export default () => {
  const [{ x, y }, ref] = useScroll()

  return (
    <>
      <div>当前 scrollLeft : {x}</div>
      <div>当前 scrollTop : {y}</div>
      <div ref={ref} style={{ height: '25vh', overflow: 'auto' }}>
        <div style={{ width: '500vw', height: '500vh' }}>这是一个滚动组件</div>
      </div>
    </>
  )
}
```

```jsx
/**
 * title: 窗体滚动 demo
 */
import React from 'react'
import useScroll from './useScroll'

export default () => {
  const [{ x, y }] = useScroll(({ x, y }) => {
    console.log('window', x, y)
  })

  return (
    <>
      <div>当前窗口的 scrollLeft : {x}</div>
      <div>当前窗口的 scrollTop : {y}</div>
    </>
  )
}
```

## API

```js
useScroll(fn: ({ x, y }) => {})

const [{ x, y }] = useScroll(fn)

const [{ x, y }, ref] = useScroll(fn)
```

### Result

| 参数     | 作用                          |
| -------- | ----------------------------- |
| { x, y } | 滚动容器当前的滚动位置        |
| ref      | 需要监听滚动事件的 `dom` 元素 |

### Params

| 参数 | 作用                                   |
| ---- | -------------------------------------- |
| fn   | 滚动触发后的回调，会传入当前的滚动位置 |
