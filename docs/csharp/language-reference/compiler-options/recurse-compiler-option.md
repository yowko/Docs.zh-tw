---
title: "/recurse (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/recurse"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/recurse compiler option [C#]"
  - "recurse compiler option [C#]"
  - "-recurse compiler option [C#]"
ms.assetid: 4e8212e5-04e3-45b1-8a42-41bc50e683b0
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# /recurse (C# Compiler Options)
\/recurse 選項可以讓您編譯指定目錄 \(dir\) 或專案目錄下，所有子目錄中的原始程式碼檔。  
  
## 語法  
  
```  
/recurse:[dir\]file  
```  
  
## 引數  
 `dir` \(選擇項\)  
 要做為搜尋起點的目錄。  如果沒有指定，搜尋就會從專案目錄開始。  
  
 `file`  
 要搜尋的檔案。  可以使用萬用字元。  
  
## 備註  
 **\/recurse** 選項可以讓您編譯指定目錄 \(`dir`\) 或專案目錄下，所有子目錄中的原始程式碼檔。  
  
 您可以在檔名中使用萬用字元，來編譯專案目錄中所有相符的檔案，而不需要使用 **\/recurse**。  
  
 在 Visual Studio 中無法使用這個編譯器選項，而且無法利用程式設計的方式變更它。  
  
## 範例  
 編譯目前目錄中的所有 C\# 檔案：  
  
```  
csc *.cs  
```  
  
 編譯 dir1\\dir2 目錄和該目錄下的任一目錄的所有 C\# 檔案，並產生 dir2.dll：  
  
```  
csc /target:library /out:dir2.dll /recurse:dir1\dir2\*.cs  
```  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [如何：修改專案屬性和組態設定](http://msdn.microsoft.com/zh-tw/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)