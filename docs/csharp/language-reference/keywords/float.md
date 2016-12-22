---
title: "float (C# 參考) | Microsoft Docs"
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
  - "float"
  - "float_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "float 關鍵字 [C#]"
  - "浮點數 [C#], float 關鍵字"
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# float (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`float` 關鍵字代表可儲存 32 位元浮點數值的簡單型別。  下表列出 `float` 型別的精確度和大約範圍。  
  
|型別|大概範圍|精確度|.NET Framework 型別|  
|--------|----------|---------|-----------------------|  
|`float`|\-3.4 × 10<sup>38</sup>到 \+3.4 × 10<sup>38</sup>|7 位數|<xref:System.Single?displayProperty=fullName>|  
  
## 常值  
 根據預設，指派運算子右邊的實數常值會被視為 [double](../../../csharp/language-reference/keywords/double.md)。  因此請使用後置字元 `f` 或 `F` 初始化 float 變數，如下列範例所示：  
  
```  
  
float x = 3.5F;  
```  
  
 如果上述宣告中沒有使用後置字元，編譯時就會發生錯誤，因為這樣實際上是嘗試將 [double](../../../csharp/language-reference/keywords/double.md) 值存到 `float` 變數內。  
  
## 轉換  
 您可以在一個運算式裡混合數值整數型別和浮點型別。  在這種情況裡，整數型別會轉換成浮點型別。  運算式的評估會根據下列規則來執行：  
  
-   如果其中一個浮點型別是 [double](../../../csharp/language-reference/keywords/double.md)，運算式就會評估為 [double](../../../csharp/language-reference/keywords/double.md)，或者如果是在關係運算式或布林運算式中則為 [bool](../../../csharp/language-reference/keywords/bool.md)。  
  
-   如果運算式中沒有 [double](../../../csharp/language-reference/keywords/double.md) 型別，運算式就會評估為 `float`，或者如果是在關係運算式或布林運算式中則為 [bool](../../../csharp/language-reference/keywords/bool.md)。  
  
 浮點運算式可以包含下列值的集合：  
  
-   正零和負零  
  
-   正無限大和負無限大  
  
-   非數字值 \(NaN\)  
  
-   非零值的有限集合  
  
 如需這些數值的詳細資訊，請參閱 [IEEE](http://go.microsoft.com/fwlink/?LinkId=26269) 網站上的 IEEE Standard for Binary Floating\-Point Arithmetic。  
  
## 範例  
 在下列程式碼範例的算術運算式中含有一個 [int](../../../csharp/language-reference/keywords/int.md)、一個 [short](../../../csharp/language-reference/keywords/short.md) 和一個 `float`，因此運算結果為 `float` \(請記住 `float` 是 <xref:System.Single?displayProperty=fullName> 型別的別名\)。 請注意，此運算式中並沒有 [double](../../../csharp/language-reference/keywords/double.md)。  
  
 [!code-cs[csrefKeywordsTypes#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/float_1.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 <xref:System.Single>   
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [轉型和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)