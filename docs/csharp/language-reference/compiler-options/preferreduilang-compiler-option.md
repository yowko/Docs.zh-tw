---
title: "/preferreduilang (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "/preferreduilang"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "preferreduilang compiler option [C#]"
  - "/preferreduilang compiler option [C#]"
  - "-preferreduilang compiler option [C#]"
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# /preferreduilang (C# Compiler Options)
使用 `/preferreduilang` 編譯器選項，您可以指定 C\# 編譯器顯示輸出的語言，例如錯誤訊息。  
  
## 語法  
  
```  
/preferreduilang: language  
```  
  
## Arguments  
 `language`  
 為編譯器輸出所使用的語言之[語言名稱](http://go.microsoft.com/fwlink/p/?LinkId=236992) 。  
  
## 備註  
 您可以使用 `/preferreduilang` 編譯器選項來指定 C\# 編譯器的錯誤訊息和其他命令列輸出使用的語言。  如果未安裝此語言的語言套件，則改用作業系統的語言設定，不會回報錯誤。  
  
```c#  
csc.exe /preferreduilang:ja-JP  
```  
  
## 需求  
  
## 請參閱  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)