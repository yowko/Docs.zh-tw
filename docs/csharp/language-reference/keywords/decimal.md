---
title: "decimal (C# 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "decimal_CSharpKeyword"
  - "decimal"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "decimal 關鍵字 [C#]"
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
caps.latest.revision: 32
caps.handback.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# decimal (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`decimal` 關鍵字表示 128 位元的資料類型。  相較於浮點類型，`decimal` 類型的精確度較高且範圍較小，因此非常適合財務和金融計算。  下表顯示 `decimal` 類型的大概範圍和精確度。  
  
|類型|大概範圍|精確度|.NET Framework 類型|  
|--------|----------|---------|-----------------------|  
|`decimal`|\(\-7.9 x 10<sup>28</sup> 至 7.9 x 10<sup>28</sup>\) \/ \(10<sup>0 至 28</sup>\)|28\-29 個有效數字|<xref:System.Decimal?displayProperty=fullName>|  
  
## 常值  
 如果要將數值實數常值視為 `decimal` 處理，請使用後置字元 m 或 M，例如：  
  
```  
  
decimal myMoney = 300.5m;  
```  
  
 如果沒有後置字元 m，會將數字視為 [double](../../../csharp/language-reference/keywords/double.md) 處理，因而產生編譯器錯誤。  
  
## 轉換  
 整數類資料類型會隱含轉換成 `decimal`，而且結果會判斷值為 `decimal`。  因此，您可以使用整數常值來初始化 Decimal 變數，而不需要後置字元，如下所示：  
  
```  
  
decimal myMoney = 300;  
```  
  
 浮點類型和 `decimal` 類型之間沒有隱含轉換，因此，這兩種類型之間必須使用轉型進行轉換。  例如：  
  
```  
  
        decimal myMoney = 99.9m;  
double x = (double)myMoney;  
myMoney = (decimal)x;  
```  
  
 您也可以在同一個運算式中混合使用 `decimal` 和數值整數類資料類型。  然而，未使用轉型就混合使用 `decimal` 與浮點類型會造成編譯錯誤。  
  
 如需隱含數值轉換的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
 如需明確數值轉換的詳細資訊，請參閱[明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)。  
  
## 格式化 Decimal 輸出  
 您可以使用 `String.Format` 方法，或透過會呼叫 `String.Format()` 的 <xref:System.Console.Write%2A?displayProperty=fullName> 方法格式化結果。  貨幣格式是使用標準貨幣格式字串 "C" 或 "c" 所指定，如本文稍後的第二個範例所示。  如需 `String.Format` 方法的詳細資訊，請參閱 <xref:System.String.Format%2A?displayProperty=fullName>。  
  
## 範例  
 下列範例會嘗試加入 [double](../../../csharp/language-reference/keywords/double.md) 和 `decimal` 變數，藉此造成編譯器錯誤。  
  
```c#  
double dub = 9;  
// The following line causes an error that reads "Operator '+' cannot be applied to   
// operands of type 'double' and 'decimal'"  
Console.WriteLine(dec + dub);   
  
// You can fix the error by using explicit casting of either operand.  
Console.WriteLine(dec + (decimal)dub);  
Console.WriteLine((double)dec + dub);  
  
```  
  
 結果會是下列錯誤：  
  
 `Operator '+' cannot be applied to operands of type 'double' and 'decimal'`  
  
 在這個範例中，`decimal` 和 [int](../../../csharp/language-reference/keywords/int.md) 會在同一個運算式中混用。  結果會判斷值為 `decimal` 類型。  
  
 [!code-cs[csrefKeywordsTypes#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_1.cs)]  
  
## 範例  
 在這個範例中，輸出是使用貨幣格式字串格式化。  您會發現，`x` 會捨入，因為小數位數超過 $0.99。  代表最大確切位數的變數 `y` 會以正確格式精確顯示。  
  
 [!code-cs[csrefKeywordsTypes#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_2.cs)]  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 <xref:System.Decimal>   
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [標準數值格式字串](../Topic/Standard%20Numeric%20Format%20Strings.md)