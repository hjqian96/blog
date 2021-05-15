---
title: Matlab 画图
mathjax: true
tags:
  - Matlab
abbrlink: '2198e562'
date: 2020-04-19 11:29:47
categories:
---

一些常用的 Matlab 画图设置或者小技巧, 先占个坑位, 持续更新.....

### 标题或者坐标轴中插入LaTeX

```matlab
figure(1)
x = 0.1:0.1:10;
plot(x, sin(x)./x);
xlabel('$x$','interpreter','latex', 'FontSize', 18)
xlabel('$y$','interpreter','latex', 'FontSize', 18)
title('$\frac{sin(x)}{x}$','interpreter','latex', 'FontSize', 18)
```

### 分图展示
```matlab 
subplot(2,2,1);
x = linspace(-3.8,3.8);
y_cos = cos(x);
plot(x,y_cos);
title('Subplot 1: Cosine')

subplot(2,2,2);
y_poly = 1 - x.^2./2 + x.^4./24;
plot(x,y_poly,'g');
title('Subplot 2: Polynomial')

subplot(2,2,[3,4]);
plot(x,y_cos,'b',x,y_poly,'g');
title('Subplot 3 and 4: Both')
```

### 一些快捷键

Ctrl + R 注释（多行有效）
Ctrl + T 去掉注释，对多行有效

## References
- http://blog.sciencenet.cn/blog-3178873-1136310.html
- https://zhuanlan.zhihu.com/p/92283650
