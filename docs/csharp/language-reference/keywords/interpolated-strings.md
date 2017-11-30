---
title: "字串插值 (C#)"
ms.date: 10/18/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b8a1fe0be82a0e09d61c66ed463199ff626c9faa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="interpolated-strings-c-reference"></a>字串插值 (C# 參考)

可用來建構字串。  字串插值類似包含「插入運算式」的範本字串。  字串插值會傳回一個字串，以將內含的插入運算式取代為運算式的字串表示。 C# 6 及更新版本中使用這項功能。

字串插值的引數比[複合格式字串](../../../standard/base-types/composite-formatting.md#composite-format-string)更容易了解。  例如，字串插值  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}");
```  
包含兩個插值的運算式 '{name}' 和 ' {小時： hh}'。 對等的複合格式字串為：

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

字串插值的結構為：  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

其中： 

- *field-width* 是帶正負號的整數，表示欄位中的字元數。 如果是正數，則欄位會靠右對齊；如果是負數，則會靠左對齊。 

- *format-string* 是一個格式字串，適用於將格式化的物件類型。 例如，若為 <xref:System.DateTime> 值，它可能是標準日期和時間格式字串，像是 "D" 或 "d"。

> [!IMPORTANT]
> 您不能有任何空白字元之間`$`和`"`開頭的字串。 這樣做會讓編譯時期錯誤。

 您可以在使用字串常值的任何位置使用字串插值。  每次執行含有字串插值的程式碼時，都會評估字串插值。 這可讓您分開定義和評估字串插值。  
  
 若要在字串插值中包含大括弧 ("{" 或 "}")，請使用雙大括弧 "{{" 或 "}}"。  如需詳細資訊，請參閱＜隱含轉換＞一節。  

當字串插值包含在字串插值中具有特殊意義的其他字元時 (例如引號 (")、冒號 (:) 或逗號 (,))，如果這些字元出現在常值文字中，則必須將它逸出；如果這些字元是包含在插入運算式中的語言項目，則必須加入以括號分隔的運算式。 下列範例會將引號逸出，以在結果字串中包含這些引號，而且會使用括號來分隔運算式 `(age == 1 ? "" : "s")`，以防止將冒號解譯為格式字串的開頭。

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]  

逐字以內插值取代字串使用`$`字元後面`@`字元。 如需逐字字串的詳細資訊，請參閱[字串](string.md)主題。 下列程式碼是先前使用逐字字串插值的程式碼片段的修改的版本：

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings5.cs#1)]  

因為並不會遵照逐字字串格式的變更所需`\`逸出序列。

> [!IMPORTANT]
> `$`必須出現在之前語彙基元`@`逐字字串插值中語彙基元。


## <a name="implicit-conversions"></a>隱含轉換  

有三個來自字串插值的隱含型別轉換：  

1. 將字串插值轉換成 <xref:System.String>。 下列範例會傳回一個字串，其字串插值運算式已取代為運算式的字串表示。 例如: 

   [!code-csharp[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]  

   這是字串解譯的最終結果。 所有出現的雙大括弧 ("{{" 和 "}}") 都會轉換成單一大括弧。 

2. 將字串插值轉換成 <xref:System.IFormattable> 變數，可讓您從單一 <xref:System.IFormattable> 執行個體建立多個具有特定文化特性內容的結果字串。 若要加入個別文化特性的正確數值和日期格式等項目時，這樣做會很有用。  在您明確或隱含呼叫 <xref:System.Object.ToString> 方法以格式化字串之前，所有出現的雙大括弧 ("{{" 和 "}}") 會保持為雙大括弧。  所有包含插值運算式會轉換成 {0}、\{1\} 等。  

   下列範例使用反映來顯示成員，以及從字串插值建立之 <xref:System.IFormattable> 變數的欄位和屬性值。 它也會傳遞<xref:System.IFormattable>變數設為<xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>方法。

   [!code-csharp[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]  

   請注意，只能使用反映來檢查字串插值。 如果將它傳遞為字串，例如格式化方法<xref:System.Console.WriteLine(System.String)>、 它的格式項目都已解決，而且傳回的結果字串。 

3. 將字串插值轉換成 <xref:System.FormattableString> 變數，以代表複合格式字串。 檢查複合格式字串及其如何轉譯為結果字串有助於在建立查詢時，防止插入式攻擊。 <xref:System.FormattableString> 也包含 <xref:System.FormattableString.ToString> 多載，可讓您產生 <xref:System.Globalization.CultureInfo.InvariantCulture> 和 <xref:System.Globalization.CultureInfo.CurrentCulture> 的結果字串。  在您格式化之前，所有出現的雙大括弧 ("{{" 和 "}}") 會保持為雙大括弧。  所有包含插值運算式會轉換成 {0}、\{1\} 等。  

   [!code-csharp[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]  

## <a name="language-specification"></a>語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)
