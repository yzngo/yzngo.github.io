---
title: ScriptObject
date: 2019-04-24 14:10:00 +0800
categories: [Unity3D, Script]
tags: [unity3d]
---




## Demo

```c#
using UnityEngine;

[CreateAssetMenu(menuName = "Level Database/Palette", fileName = "New Palette", order = 1)]
public class Palette : ScriptableObject
{
    [SerializeField] private Color[] colors;
    public Color this[int i] => colors[i];
}

```



## 用代码Create

- 如果是集合类型要new出来

```c#
[CreateAssetMenu(menuName = "Puzzle/LevelData", fileName = "LevelData", order = 2)]
public class LevelData : ScriptableObject
{
    public int EmptyBottleCount;
    public List<BottleData> BottleData;
}
-
string newName = "Level 1";
LevelData level = CreateInstance<LevelData>();
level.name = newName;
level.EmptyBottleCount = 1;
level.BottleData = new List<BottleData>();	//!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
AssetDatabase.CreateAsset(level, LEVELS_FOLDER_PATH + newName + ".asset");

levelDataProperty.arraySize++;
levelDataProperty.GetArrayElementAtIndex(levelDataProperty.arraySize - 1).objectReferenceValue = level;
levelsReorderableList.Index = levelDataProperty.arraySize - 1;
LevelsListOnSelectCallback(levelsReorderableList);

AssetDatabase.SaveAssets();
AssetDatabase.Refresh();
```
