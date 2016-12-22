---
title: "char (C# 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "char"
  - "char_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "char 資料類型 [C#]"
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
caps.latest.revision: 27
caps.handback.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# char (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`char` 關鍵字是用來宣告 .NET Framework 使用 Unicode 字元表示 <xref:System.Char?displayProperty=fullName> 結構的執行個體。  `Char` 物件的值為 16 位元數值 \(序數\) 值。  
  
 Unicode 字元是用來在全世界大多數書寫語言。  
  
|型別|Range|Size|.NET Framework 型別|  
|--------|-----------|----------|-----------------------|  
|`char`|U\+0000 至 U\+FFFF|Unicode 16 位元字元|<xref:System.Char?displayProperty=fullName>|  
  
## 常值  
 `char` 型別的常數可以寫成字元常值、十六進位逸出序列 \(Escape Sequence\) 或 Unicode 表示。  您也可以轉換整數字元碼。  在下列範例中，四個 `char` 變數是以相同字元 `X` 進行初始化：  
  
 [!code-cs[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]  
  
## 轉換  
 `char` 可以隱含地轉換成 [ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md)。  然而，其他的型別不能隱含地轉換成 `char` 型別。  
  
 <xref:System.Char?displayProperty=fullName> 型別提供了一些處理 `char` 值的靜態方法。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 <xref:System.Char>   
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [可為 Null 的類型](../../../visual-basic/reference/command-line-compiler/index.md)   
 [字串](../../../csharp/programming-guide/strings/index.md)