## 游戏介绍

这是一个记忆型翻牌游戏，总共三个 level，分别对应的是 2x2, 4x4, 6x6 的卡片数量。
游戏一开始的时候，所有卡牌都是背面朝上，玩家点击一张卡牌，可以翻转这张卡牌。
玩家需要通过找到两张一样的卡牌，实现得分。

## 游戏实现

可以根据下方的游戏流程和参照最终游戏效果来直接实现。
或者，按照以下步骤一步一步实现：

### 1. 熟悉现有代码

仔细阅读提供的代码，包括 html，css 和 js。(建议玩一玩最终版本，链接在最下方）
运用现有的 css，翻转卡片。（只改动 html）

### 2. 点击卡片实现翻转

通过改变 js，实现当点击卡片的时候，翻转卡片

### 3. 卡片翻转逻辑

实现以下逻辑

```
用户点击卡片，
    如果该卡片未被翻开过
        翻开卡片，如果这是翻开的第二张卡片，检查两张卡片是否一致
            如果一致，持续打开卡片，增加玩家分数
            否则，1.5秒后盖上这两张卡片
    如果已经被翻开
        把该卡片盖上
```
<img width="586" alt="image" src="https://github.com/LazeBear/jr-fullstack-assignment/assets/19187875/9f3d922b-49f0-4599-9ea5-c7f1ef0fe881">


### 4. 倒计时

加入一个 60s 的倒计时，倒计时应该实时的反应在 ui 上

<img width="577" alt="image" src="https://github.com/LazeBear/jr-fullstack-assignment/assets/19187875/7bf080e3-42c5-4ee1-9df8-653ef690aeb5">

### 5. 分数计算

加入分数计算，计算公式为：当前等级 \*_ 2 _ 当前倒计时的时间

<img width="173" alt="image" src="https://github.com/LazeBear/jr-fullstack-assignment/assets/19187875/993bca9e-bffa-4215-aee8-493e6f187dc4">

### 6. 动态创建游戏卡片

先删除 html 中`<div class="game-board" style="grid-template-columns: 1fr 1fr">` 的部分（整个 node）
然后在 js 中，通过代码生成卡片，然后显示在页面中

### 7. 游戏难度

现在的游戏只能支持 level 1，也就是 2x2 的游戏。我们想要根据 level，生成更多的卡片来提高难度
在 html 中，有一部分 commented out 的代码，`<!-- <div class="game-board">`
想要实现的效果，应该是玩家点击 Start Game， 然后内容由 instruction 替换成实际的 game board
之后每一次的 level 变化，都会重新生成新的 game board

<img width="209" alt="image" src="https://github.com/LazeBear/jr-fullstack-assignment/assets/19187875/ee301aa2-6eec-4109-9efa-92330d55753d">


### 8. 游戏优化

思考一下有哪些我们在之前步骤中没有考虑到的功能？
比如，

1. 随机生成卡片顺序
2. 倒计时结束后，玩家不应该能够继续点击卡片实现翻转
3. 玩家应该可以随时停止游戏，或开始一局新的游戏

 ...
   （可以参照最终游戏效果）

## 游戏流程

1. 用户点击 Start Game，更新游戏界面。level 1， 四张卡片。倒计时开始。
2. 用户点击卡片，
   如果该卡片未被翻开过
   翻开卡片，如果这是翻开的第二张卡片，检查两张卡片是否一致
   如果一致，持续打开卡片，增加玩家分数
   否则，1.5 秒后盖上这两张卡片
   如果已经被翻开
   把该卡片盖上
3. 如果 60s 已到，所有卡片并未全部翻转，游戏结束，弹出 alert，显示分数
4. 如果 60s 内，所有卡片全部翻转，进入下一 level。如果当前为第三个 level，结束游戏，结算分数

## 最终游戏效果

https://lazebear.github.io/Mem/
