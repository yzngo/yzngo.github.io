---
title: Unity - Plugin-I2Localization
date: 2021-04-03 14:10:00 +0800
categories: [Unity3D, Localization]
tags: [unity3d]
---

[Doc](http://inter-illusion.com/assets/I2LocalizationManual/Features.html)

## 一 工作流
1. 资源文件 Resources -> I2Languages
   - Spreadsheets 导入导出csv, 必须UTF8编码格式
   - Terms  设置词条
   - Languages  设置语言
   - Tools 
        - Script 生成字典脚本, 以便于可在代码里直接通过`.`的方式引用I2字符串
        - CharSet 得到使用的字符 -> 用于创建TextMeshPro的字体文件
## 二 基本操作 (I2.Loc)

### 1. 更换Language
   - 设备语言接口 Application.systemLanguage    I2首先会尝试使用这个接口设置语言

     1) 脚本设置(通过name)  
     
     ```c#
        if (LocalizationManager.HasLanguage(LanguageName))
        {
            LocalizationManager.CurrentLanguage = LanguageName;
        }
     ```
     
     
     
     * 语言字符串()内的为语言变体  如: English(Canada)
     
     2) 脚本设置(通过Code) 
        LocalizationManager.CurrentLanguageCode="en-US";
     
     3) 按钮直接设置,无需新写脚本
        - 挂载[SetLanguage]组件, 按钮回调添加此组件的[SetLanguage.ApplyLanguage]

### 2. 根据Language更换Font
    1. 在Term中添加一个TextMeshP Font的项目, 设置好字体
    2. 在Localize组件上, 把上面写好的项作为第二个项

### 2. 设置本地化字符串
1. I2 Localize 主要组件, 需要本地化的文本需要添加这个组件, *即所有文本都要添加这个组件*
2. 得到本地化字符串
   - string text = LocalizationManager.GetTranslation("Key");
3. 生成脚本
   - Tools -> Script
   - string text = ScriptLocalization.Key;
4. 转换为LocalizedString
   - string text = (LocalizedString)"Key";
