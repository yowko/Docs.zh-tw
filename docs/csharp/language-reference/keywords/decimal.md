---
title: "decimal (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- decimal_CSharpKeyword
- decimal
dev_langs:
- CSharp
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
caps.latest.revision: 32
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 336a4a7bb485a48282dd740bafb81421e0cba693
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="decimal-c-reference"></a>decimal (C# 參考)
`decimal` 關鍵字表示 128 位元的資料類型。 相較於浮點類型，`decimal` 類型的精確度較高且範圍較小，因此非常適合財務和金融計算。 下表顯示 `decimal` 類型的大概範圍和精確度。  
  
|類型|大概範圍|精確度|.NET Framework 類型|  
|----------|-----------------------|---------------|-------------------------|  
|`decimal`|(-7.9 x 10<sup>28</sup> 至 7.9 x 10<sup>28</sup>) / (10<sup>0 至 28</sup>)|28-29 個有效數字|<xref:System.Decimal?displayProperty=fullName>|  
  
## <a name="literals"></a>常值  
 如果要將數值實數常值視為 `decimal` 處理，請使用後置字元 m 或 M，例如：  
  
```  
decimal myMoney = 300.5m;  
```  
  
 如果沒有後置字元 m，會將數字視為 [double](../../../csharp/language-reference/keywords/double.md) 處理，因而產生編譯器錯誤。  
  
## <a name="conversions"></a>轉換  
 整數類資料類型會隱含轉換成 `decimal`，而且結果會判斷值為 `decimal`。 因此，您可以使用整數常值來初始化 Decimal 變數，而不需要後置字元，如下所示：  
  
```  
decimal myMoney = 300;  
```  
  
 浮點類型和 `decimal` 類型之間沒有隱含轉換，因此，這兩種類型之間必須使用轉型進行轉換。 例如：  
  
```  
      decimal myMoney = 99.9m;  
double x = (double)myMoney;  
myMoney = (decimal)x;  
```  
  
 您也可以在同一個運算式中混合使用 `decimal` 和數值整數類資料類型。 然而，未使用轉型就混合使用 `decimal` 與浮點類型會造成編譯錯誤。  
  
 如需隱含數值轉換的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
 如需明確數值轉換的詳細資訊，請參閱[明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)。  
  
## <a name="formatting-decimal-output"></a>格式化 Decimal 輸出  
 您可以使用 `String.Format` 方法，或透過會呼叫 <xref:System.Console.Write%2A?displayProperty=fullName> 的 `String.Format()` 方法格式化結果。 貨幣格式是使用標準貨幣格式字串 "C" 或 "c" 所指定，如本文稍後的第二個範例所示。 如需 `String.Format` 方法的詳細資訊，請參閱 <xref:System.String.Format%2A?displayProperty=fullName>。  
  
## <a name="example"></a>範例  
 下列範例會嘗試新增 [double](../../../csharp/language-reference/keywords/double.md) 和 `decimal` 變數，而造成編譯器錯誤。  
  
```csharp  
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
  
 在這個範例中，`decimal` 和 [int](../../../csharp/language-reference/keywords/int.md) 會在同一個運算式中混用。 結果會判斷值為 `decimal` 類型。  
  
 [!code-cs[csrefKeywordsTypes#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_1.cs)]  
  
## <a name="example"></a>範例  
 在這個範例中，輸出是使用貨幣格式字串格式化。 您會發現，`x` 會捨入，因為小數位數超過 $0.99。 代表最大確切位數的變數 `y` 會以正確格式精確顯示。  
  
 [!code-cs[csrefKeywordsTypes#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_2.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Decimal>   
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [標準數值格式字串](../../../standard/base-types/standard-numeric-format-strings.md)

