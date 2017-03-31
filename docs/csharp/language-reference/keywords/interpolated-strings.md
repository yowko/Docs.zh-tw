---
title: "字串插值 (C#) | Microsoft Docs"
ms.date: 2017-02-03
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 9
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a3e2641e5c7cd3ce98ca869889848e8cdf4eed62
ms.lasthandoff: 03/13/2017

---
# <a name="interpolated-strings-c-reference"></a>字串插值 (C# 參考)

可用來建構字串。  字串插值類似包含「插入運算式」**的範本字串。  字串插值會傳回一個字串，以將內含的插入運算式取代為運算式的字串表示。  

字串插值的引數比[複合格式字串](../../../standard/base-types/composite-format.md#composite-format-string)更容易了解。  例如，字串插值  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}"); 
```  
包含兩個插入運算式 '{name}' 和 '{hours:hh}'。 對等的複合格式字串為：

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours);  
```  

字串插值的結構為：  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [<:format-string>] } <text> ..."  
```  

其中： 

- *field-width* 是帶正負號的整數，表示欄位中的字元數。 如果是正數，則欄位會靠右對齊；如果是負數，則會靠左對齊。 

- *format-string* 是一個格式字串，適用於將格式化的物件類型。 例如，若為 @System.DateTime 值，它可能是標準日期和時間格式字串，像是 "D" 或 "d"。

 您可以在使用字串常值的任何位置使用字串插值。  每次執行含有字串插值的程式碼時，都會評估字串插值。 這可讓您分開定義和評估字串插值。  
  
 若要在字串插值中包含大括號 ("{" 或 "}")，請使用雙大括號 "{{" 或 "}}"。  如需詳細資訊，請參閱＜隱含轉換＞一節。  

當字串插值包含在字串插值中具有特殊意義的其他字元時 (例如引號 (")、冒號 (:) 或逗號 (,))，如果這些字元出現在常值文字中，則必須將它逸出；如果這些字元是包含在插入運算式中的語言項目，則必須加入以括號分隔的運算式。 下列範例會將引號逸出，以在結果字串中包含這些引號，而且會使用括號來分隔運算式 `(age == 1 ? "" : "s")`，以防止將冒號解譯為格式字串的開頭。

[!code-cs[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]  

## <a name="implicit-conversions"></a>隱含轉換  

有三個來自字串插值的隱含型別轉換：  

1. 將字串插值轉換成 @System.String。 下列範例會傳回一個字串，其字串插值運算式已取代為運算式的字串表示。 例如: 

   [!code-cs[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]  

   這是字串解譯的最終結果。 所有出現的雙大括弧 (“{{“ 和 “}}”) 都會轉換成單一大括弧。 

2. 將字串插值轉換成 <xref:System.IFormattable> 變數，可讓您從單一 <xref:System.IFormattable> 執行個體建立多個具有特定文化特性內容的結果字串。 若要加入個別文化特性的正確數值和日期格式等項目時，這樣做會很有用。  所有出現的雙大括號 (“{{“ 和 “}}”) 會保持為雙大括號，直到您明確或隱含呼叫 @System.Object.ToString 方法格式化字串為止。  所有包含插值運算式會轉換成 {0}、\{1\} 等。  

   下列範例使用反映來顯示成員，以及從字串插值建立之 <xref:System.IFormattable> 變數的欄位和屬性值。 它也會將 <xref:System.IFormattable> 變數傳遞至 @System.Console(System.String) 方法。

   [!code-cs[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]  

   請注意，只能使用反映來檢查字串插值。 如果將它傳遞至字串格式化方法 (例如 @System.Console.WriteLine(System.String))，則會解析其格式項目並傳回結果字串。 

3. 將字串插值轉換成 <xref:System.FormattableString> 變數，以代表複合格式字串。 檢查複合格式字串及其如何轉譯為結果字串有助於在建立查詢時，防止插入式攻擊。  <xref:System.FormattableString> 也包含 <xref:System.FormattableString.ToString> 多載，讓您產生 @System.Globalization.InvariantCulture 和 @System.Globalization.CurrentCulture 的結果字串。  所有出現的雙大括弧 (“{{“ 和 “}}”) 會保持為雙大括弧，直到您格式化為止。  所有包含插值運算式會轉換成 {0}、\{1\} 等。  

   [!code-cs[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]  

## <a name="language-specification"></a>語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IFormattable?displayProperty=fullName>   
 <xref:System.FormattableString?displayProperty=fullName>   
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)

