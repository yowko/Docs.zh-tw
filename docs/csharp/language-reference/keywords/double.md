---
title: "double (C# 參考) | Microsoft Docs"
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
  - "double"
  - "double_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "double 資料類型 [C#]"
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# double (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`double` 關鍵字代表可儲存 64 位元浮點數值的簡單型別。  下表列出 `double` 型別的精確度和大約範圍。  
  
|型別|大概範圍|精確度|.NET Framework 型別|  
|--------|----------|---------|-----------------------|  
|`double`|±5.0 × 10<sup>−324</sup> 到 ±1.7 × 10<sup>308</sup>|15\-16 位數|<xref:System.Double?displayProperty=fullName>|  
  
## 常值  
 根據預設，指派運算子右邊的實數常值會被視為 `double` 處理。  但是，如果您想將整數當成 `double`，請用後置字元 d 或 D，例如：  
  
```  
  
double x = 3D;  
```  
  
## 轉換  
 您可以在一個運算式裡混合數值整數型別和浮點型別。  在這種情況裡，整數型別會轉換成浮點型別。  運算式的評估會根據下列規則來執行：  
  
-   如果其中一個浮點型別是 `double`，此運算式就會評估為 `double`，或者若是在關聯運算式或布林運算式中則為 [bool](../../../csharp/language-reference/keywords/bool.md)。  
  
-   如果運算式中沒有 `double` 型別，則會評估為 [float](../../../csharp/language-reference/keywords/float.md)，或者如果是在關係運算式或布林運算式中則為 [bool](../../../csharp/language-reference/keywords/bool.md)。  
  
 浮點運算式可以包含下列值的集合：  
  
-   正零和負零  
  
-   正無限大和負無限大  
  
-   非數字的值 \(NaN\)  
  
-   非零值的有限集合  
  
 如需這些數值的詳細資訊，請參閱 [IEEE](http://go.microsoft.com/fwlink/?LinkId=26269) 網站上的 IEEE Standard for Binary Floating\-Point Arithmetic。  
  
## 範例  
 在下列程式碼範例中，會同時加入 [int](../../../csharp/language-reference/keywords/int.md)、[short](../../../csharp/language-reference/keywords/short.md)、[float](../../../csharp/language-reference/keywords/float.md) 和 `double` 以產生 `double` 結果。  
  
 [!code-cs[csrefKeywordsTypes#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/double_1.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [預設值表](../../../csharp/language-reference/keywords/default-values-table.md)   
 [內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [浮點類型表](../../../csharp/language-reference/keywords/floating-point-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)