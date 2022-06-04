---
title: Unity - RectTransform
date: 2021-04-03 14:10:00 +0800
categories: [Unity3D, UI]
tags: [unity3d,uGUI]
---



## 坐标变换

```c#
// 当前屏幕坐标（实际运行时的分辨率大小）
// 左下角(0,0),右上角(width, height)
Screen.width;  // current screen
Screen.height  // current height

// 拿到世界坐标
transform.position
    
// 世界坐标转换到屏幕坐标, 以下两个方法是等价的，只是返回类型不同
Vector3 screenPoint = camera.WorldToScreenPoint(transform.position);
Vector2 screenPoint = RectTransformUtility.WorldToScreenPoint(Camera cam, Vector3 worldPoint);

// 屏幕坐标转换到uGUI本地坐标
// 返回值表示转换后的uGUI本地坐标是否在父对象的Rect内
public static bool RectTransformUtility.ScreenPointToLocalPointInRectangle(
      RectTransform rect,		// 父对象的RectTransform
      Vector2 screenPoint,		// 屏幕坐标点
      Camera cam,				// 渲染Canvas的相机，Overlay = null
      out Vector2 localPoint);	// 转换后的uGUI本地坐标

// 设置uGUI对象的宽和高
rectTransform.anchoredPosition = new Vector2(x, y);		// position
rectTransform.sizeDelta = new Vector2(width, height);	// size
```



## 锚点

- 最好是在Game视图的分辨率设置为Canvas的`参考分辨率`时设置锚点。因为此时的元件位置是准确无误的。
- 锚点是相对于父对象的。
- 快捷键shift，alt

## 轴心点 Pivot

```c#
                        (1,1)
 |----------------------|
 |                      |
 |                      |
 |      (0.5, 0.5)      |
 |                      |
 |                      |
 |______________________|
(0,0) 
```



## 缩放 Scale

- scale 只用于动画或其他特殊效果, 调整布局只调整UI的 width 和 height
- width 和 height 为负 UI元素 会变透明, scale为负不会







