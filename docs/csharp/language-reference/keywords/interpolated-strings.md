---
title: "字串插值 (C# 和 Visual Basic 參考) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 字串插值 (C# 和 Visual Basic 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

可用來建構字串。  字串插值運算式類似包含運算式的範本字串。  字串插值運算式會透過以運算式結果的 ToString 表示取代包含運算式，來建立字串。  對於引數而言，字串插值比 [複合格式](../Topic/Composite%20Formatting.md)更容易了解。  以下是字串插值的範例：  
  
```c#  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")  
```  
  
 字串插值的結構如下所示：  
  
```  
$ " <text> { <interpolation-expression> <optional-comma-field-width> <optional-colon-format> } <text> ... } "  
```  
  
 您可以在使用字串常值的任何位置使用字串插值。  當執行程式時，如果執行到含有字串插值常值的程式碼，則程式碼會透過評估插值運算式，來計算新的字串常值。  每次執行含有字串插值的程式碼時，都會進行這項計算。  
  
 若要在字串插值中包含大括弧 \("{" 或 "}"\)，請使用雙大括弧 "{{" 或 "}}"。  如需詳細資訊，請參閱＜隱含轉換＞一節。  
  
## 隱含轉換  
 字串插值會隱含轉換：  
  
```c#  
var s = $"hello, {name}" System.IFormattable s = $"Hello, {name}" System.FormattableString s = $"Hello, {name}"  
  
```  
  
 第一個範例會產生 `string` 值，其中所有字串插值都已經過計算。  最後的結果會包含字串類型。  所有出現的雙大括弧 \(“{{“ 和 “}}”\) 都會轉換成單一大括弧。  
  
 第二個範例會產生 <xref:System.IFormattable> 變數，讓您轉換具有非變異內容的字串。  這可用來取得不同語言的正確數值和資料格式。  所有出現的雙大括弧 \(“{{“ 和 “}}”\) 會保持為雙大括弧，直到您使用 ToString 格式化字串為止。  所有包含插值運算式會轉換成 {0}、\\{1\\} 等。  
  
```c#  
s.ToString(null, System.Globalization.CultureInfo.InvariantCulture);  
```  
  
 第三個範例會產生 <xref:System.FormattableString>，讓您檢查從插值計算產生的物件。  檢查物件及其如何轉譯為字串有助於在建置查詢時，防止插入式攻擊。<xref:System.FormattableString> 可方便您產生 InvariantCulture 和 CurrentCulture 字串結果。  所有出現的雙大括弧 \(“{{“ 和 “}}”\) 會保持為雙大括弧，直到您格式化為止。  所有包含插值運算式會轉換成 {0}、\\{1\\} 等。  
  
## 範例  
  
```c#  
$"Name = {name}, hours = {hours:hh}" var s = $"hello, {name}" System.IFormattable s = $"Hello, {name}" System.FormattableString s = $"Hello, {name}" $"{person.Name, 20} is {person.Age:D3} year {(p.Age == 1 ? "" : "s")} old."  
  
```  
  
 您不需要在包含插值運算式內加註引號字元，因為插值運算式的開頭為 $，而編譯器會將包含插值運算式當做對稱文字來掃描，直到找到逗號、冒號或右大括弧為止。基於相同原因，最後一個範例會使用括號將條件運算式 \(`p.Age == 1 ? "" : "s"`\) 置於插值運算式內，而不使用冒號來起始格式規格。在包含插值運算式外 \(但仍在字串插值運算式內\)，您可以和平常一樣逸出引號字元。  
  
## 語法  
  
```  
expression: interpolated-string-expression interpolated-string-expression: interpolated-string-start interpolations interpolated-string-end interpolations: single-interpolation single-interpolation interpolated-string-mid interpolations single-interpolation: interpolation-start interpolation-start : regular-string-literal interpolation-start: expression expression , expression  
  
```  
  
## 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
 如需詳細資訊，請參閱 [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)。  
  
## 請參閱  
 <xref:System.IFormattable?displayProperty=fullName>   
 <xref:System.FormattableString?displayProperty=fullName>   
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)   
 [Visual Basic Programming Guide](../../../visual-basic/reference/command-line-compiler/index.md)