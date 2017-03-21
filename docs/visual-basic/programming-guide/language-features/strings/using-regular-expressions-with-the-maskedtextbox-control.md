---
title: "使用規則運算式與 MaskedTextBox 控制項，在 Visual Basic |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 15d8f131aa834321fcf7e8ca633929385c666e6a
ms.lasthandoff: 03/13/2017

---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>在 Visual Basic 中將規則運算式與 MaskedTextBox 控制項一起搭配使用
這個範例示範如何將簡單的規則運算式，才能使用<xref:System.Windows.Forms.MaskedTextBox>控制項。</xref:System.Windows.Forms.MaskedTextBox>  
  
## <a name="description-of-the-masking-language"></a>遮罩語言說明  
 標準<xref:System.Windows.Forms.MaskedTextBox>遮罩語言根據所使用的`Masked Edit`控制[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]6.0 和應該很熟悉來自該平台移轉的使用者。</xref:System.Windows.Forms.MaskedTextBox>  
  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>屬性<xref:System.Windows.Forms.MaskedTextBox>控制項指定要使用何種輸入的遮罩。</xref:System.Windows.Forms.MaskedTextBox> </xref:System.Windows.Forms.MaskedTextBox.Mask%2A> 遮罩必須是由一或多個下表中的遮罩項目所組成的字串。  
  
|遮罩項目|描述|規則運算式項目|  
|---------------------|-----------------|--------------------------------|  
|0|任何介於 0 到 9 的單一數字。 必要項目。|\d|  
|9|數字或空格。 選擇性的項目。|[ \d]?|  
|#|數字或空格。 選擇性的項目。 如果這個位置空白遮罩中，它會呈現為空格。 加號 （+） 和減號 （-） 允許符號。|[ \d+-]?|  
|L|ASCII 字母。 必要項目。|[a A-za-z]|  
|?|ASCII 字母。 選擇性的項目。|[a A-za-z]？|  
|&|字元。 必要項目。|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|字元。 選擇性的項目。|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]？|  
|A|英數字元。 選擇性的項目。|\W|  
|.|適當文化特性的小數預留位置。|不適用。|  
|,|文化特性適當的千分位符號。|不適用。|  
|:|適當文化特性的時間分隔符號。|不適用。|  
|/|適當文化特性的日期分隔符號。|不適用。|  
|$|適當文化特性的貨幣符號。|不適用。|  
|\<|將轉換成小寫之後的所有字元。|不適用。|  
|>|將轉換成大寫之後的所有字元。|不適用。|  
|&#124;|設定復原先前的上移或下移。|不適用。|  
|\|逸出遮罩字元，將它轉換成常值。 「\\\\」 是一個反斜線逸出序列。|\|  
|所有其他字元。|常值。 所有非遮罩的項目內<xref:System.Windows.Forms.MaskedTextBox>.</xref:System.Windows.Forms.MaskedTextBox> ，就會出現以自身身分|所有其他字元。|  
  
 小數點 （.）、 千分之一 （，）、 時間 （:）、 日期 （/），以及顯示這些符號所定義的應用程式的文化特性的貨幣 （$） 符號預設。 您可以強制它們使用另一個文化特性的符號來顯示<xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>屬性。</xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>  
  
## <a name="regular-expressions-and-masks"></a>規則運算式與遮罩  
 雖然您可以使用規則運算式和遮罩來驗證使用者輸入，則不完全相等。 規則運算式可以表達更複雜的模式比遮罩，但遮罩可以表示相同的資訊更簡潔的方式和文化特性所特有的格式。  
  
 下表會比較每四個規則運算式和對等的遮罩。  
  
|規則運算式|遮罩|備註|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|`/`遮罩中的字元是邏輯日期分隔符號，，它會顯示給使用者，適用於應用程式的目前文化特性的日期分隔符號。|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|中的三個字母月份縮寫顯示第一個字母大寫後面兩個小寫字母與美國格式日期 （日、 月份縮寫和年）。|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|選擇性的區碼美國電話號碼。 如果使用者不希望輸入選擇性的字元，她可以輸入空格，或直接將滑鼠指標置於遮罩中的第一個 0 表示的位置。|  
|`$\d{6}.00`|`$999,999.00`|介於 0 到 999999 貨幣值。 貨幣、 千位和十進位字元將會取代在執行階段其特定文化特性的對等用法。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A></xref:System.Windows.Forms.MaskedTextBox.Mask%2A>   
 <xref:System.Windows.Forms.MaskedTextBox></xref:System.Windows.Forms.MaskedTextBox>   
 [在 Visual Basic 中驗證字串](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)   
 [MaskedTextBox 控制項](http://msdn.microsoft.com/library/235d6121-027d-481d-8d59-4f6794d15d0c)
