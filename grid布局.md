## 网格布局

将容器内的元素切割成一个个格子，可以对单元格进行操作，也可以对某几个或者整个容器操作，从而满足日常较为复杂的布局场景

- display: grid/inline-grid：区别于 block/inline-block 类似
- grid-template-columns：网格列数及其占宽，可以 px、百分比、fr（类似 flex 中的分配率）
- grid-template-rows：网格行数及其所占高，单位有 columns 一致
  - 常用函数
    - minmax()，在一个范围内取值，第一个参数是最小值，第二个参数是最大值
    - repeat()，重复输出指定次数某一个表达式，第一个参数为次数，第二个为表达
- row-gap：行间距
- column-gap：列间距
- gap：行列间距
- grid-auto-flow：优先排列的方向
  - 可选值
    - row/row dense，dense 表示尽可能的占满
    - column/column dense，dense 表示尽可能的占满
- justify-items：用于控制每一个单元格的水平方向排列
  - start
  - end
  - center
  - stretch，表示占满
- align-items：用于控制每一个单元格的垂直方向排列
  - start
  - end
  - center
  - stretch，表示占满
- place-items: <align-items> <justify-items>
- justify-content：整个网格的水平方向排列
  - start
  - end
  - center
  - stretch，表示占满
  - space-around，被空隙包裹
  - space-between，包裹空隙
  - space-evenly， 所有空隙宽度一致
- align-content：整个网格的垂直方向排列
  - start
  - end
  - center
  - stretch，表示占满
  - space-around，被空隙包裹
  - space-between，包裹空隙
  - space-evenly， 所有空隙高度一致
- grid-template-areas：给每一个单元格命名
  - 用法：
  -  `grid-template-areas: 'a b c''d . f''g h i'`，. 表示占位
  - `grid-area: a`，指定哪个单元格，类名和单元格名同时作用，优先使用此

