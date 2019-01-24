---
title: 在 Visual Basic 中將規則運算式與 MaskedTextBox 控制項一起搭配使用
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: 58c0caa9d1df49ec53273e5b0f456cf89fc64c42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683686"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>在 Visual Basic 中將規則運算式與 MaskedTextBox 控制項一起搭配使用
這個範例示範如何將簡單的規則運算式，才能使用<xref:System.Windows.Forms.MaskedTextBox>控制項。  
  
## <a name="description-of-the-masking-language"></a>遮罩語言的說明  
 標準<xref:System.Windows.Forms.MaskedTextBox>遮罩語言會根據所使用的`Masked Edit`控制在 Visual Basic 6.0 和應該很熟悉從該平台移轉的使用者。  
  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>屬性<xref:System.Windows.Forms.MaskedTextBox>控制項指定要使用何種輸入的遮罩。 遮罩必須是一或多個下表中的遮罩項目所組成的字串。  
  
|遮罩項目|描述|規則運算式項目|  
|---------------------|-----------------|--------------------------------|  
|0|介於 0 到 9 之間任何單一數字。 必要項目。|\d|  
|9|數字或空格。 選擇性的項目。|[ \d]?|  
|#|數字或空格。 選擇性的項目。 如果這個位置空白遮罩中，它會轉譯為空格。 加號 （+） 和減號 （-） 允許符號。|[ \d+-]?|  
|L|ASCII 字母。 必要項目。|[a-zA-Z]|  
|?|ASCII 字母。 選擇性的項目。|[a-zA-Z]?|  
|&|字元。 必要項目。|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|字元。 選擇性的項目。|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|A|英數字元。 選擇性的項目。|\W|  
|。|適當的文化特性的小數預留位置。|不適用。|  
|,|適當數以千計的文化特性的預留位置。|不適用。|  
|:|適當的文化特性的時間分隔符號。|不適用。|  
|/|適當的文化特性的日期分隔符號。|不適用。|  
|$|適當的文化特性的貨幣符號。|不適用。|  
|\<|將轉換成小寫之後的所有字元。|不適用。|  
|>|將轉換成大寫之後的所有字元。|不適用。|  
|&#124;|復原上一個 shift 向上或向下移動。|不適用。|  
|&#92;|逸出的遮罩字元，將它轉換成常值。 「\\\\」 是一個反斜線逸出序列。|&#92;|  
|所有其他字元。|常值。 所有非遮罩項目會顯示為本身內<xref:System.Windows.Forms.MaskedTextBox>。|所有其他字元。|  
  
 小數點 （.）、 千分之一秒 （，）、 （:） 的時間、 日期 （/） 和貨幣 （$） 符號預設值所定義的應用程式的文化特性顯示這些符號。 您可以強制使用顯示另一個文化特性的符號<xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>屬性。  
  
## <a name="regular-expressions-and-masks"></a>規則運算式與遮罩  
 雖然您可以使用規則運算式和遮罩來驗證使用者輸入，則不完全相等。 規則運算式可以表示更複雜的模式與遮罩，但更簡潔的方式和文化特性相關格式遮罩可以用相同的資訊來表示。  
  
 下表會比較每個四個規則運算式和對等的遮罩。  
  
|規則運算式|遮罩|注意|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|`/`遮罩中的字元是邏輯日期分隔符號，以及適用於應用程式的目前文化特性的日期分隔符號形式顯示給使用者。|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|格式的日期 （日期、 月份縮寫及年份） 美國顯示與第一個字母大寫後面兩個小寫字母的三個字母月份縮寫。|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|美國電話號碼，選擇性的區碼。 如果使用者不希望輸入的選擇性字元，她可以輸入空格，或直接將滑鼠指標置於第一個 0 表示遮罩中的位置。|  
|`$\d{6}.00`|`$999,999.00`|範圍內的 0 到 999999 貨幣值。 在執行階段會取代 「 貨幣、 千位數和小數點字元 」，以相對的特定文化特性。|  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [在 Visual Basic 中驗證字串](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [MaskedTextBox 控制項](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
