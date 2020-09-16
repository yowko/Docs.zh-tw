---
title: 將規則運算式與 MaskedTextBox 控制項搭配使用
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: 1bb5ac5381dc85f598ef46638fbc8cd1a8643825
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555740"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>在 Visual Basic 中將規則運算式與 MaskedTextBox 控制項一起搭配使用
這個範例示範如何轉換簡單的正則運算式，以使用 <xref:System.Windows.Forms.MaskedTextBox> 控制項。  
  
## <a name="description-of-the-masking-language"></a>遮罩語言的描述  
 標準 <xref:System.Windows.Forms.MaskedTextBox> 遮罩語言是以 Visual Basic 6.0 中的控制項所使用的語言為基礎 `Masked Edit` ，對於從該平臺遷移的使用者來說，應該很熟悉。  
  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>控制項的屬性會 <xref:System.Windows.Forms.MaskedTextBox> 指定要使用的輸入遮罩。 遮罩必須是由下表中的一或多個遮罩元素組成的字串。  
  
|遮罩元素|描述|正則運算式元素|  
|---------------------|-----------------|--------------------------------|  
|0|介於0到9之間的任何單一數位。 需要專案。|\d|  
|9|數位或空格。 專案選擇性。|[\d]？|  
|#|數位或空格。 專案選擇性。 如果遮罩中的這個位置是空白的，則會呈現為空格。 此外，還允許 (+) 和減號 ( ) 符號。|[\d +-]？|  
|L|ASCII 字母。 需要專案。|[a-zA-Z]|  
|?|ASCII 字母。 專案選擇性。|[a-z]？|  
|&|字元。 需要專案。|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|字元。 專案選擇性。|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|A|字母。 專案選擇性。|\W|  
|.|符合文化特性的小數預留位置。|無法使用。|  
|,|符合文化特性的千位預留位置。|無法使用。|  
|:|符合文化特性的時間分隔符號。|無法使用。|  
|/|符合文化特性的日期分隔符號。|無法使用。|  
|$|符合文化特性的貨幣符號。|無法使用。|  
|\<|將後面的所有字元轉換成小寫。|無法使用。|  
|>|將後面的所有字元轉換成大寫。|無法使用。|  
|&#124;|復原上一個向上或向下移動。|無法使用。|  
|&#92;|將遮罩字元轉換成常值。 " \\ \\ " 是反斜線的 escape 序列。|&#92;|  
|所有其他字元。|常值。 所有的非遮罩元素都會出現在中 <xref:System.Windows.Forms.MaskedTextBox> 。|所有其他字元。|  
  
 Decimal ( ) 、萬分之一 (、) 、time (： ) 、date (/) 和 currency ($) 符號預設為顯示這些符號，如應用程式文化特性所定義。 您可以使用屬性來強制它們顯示其他文化特性的符號 <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> 。  
  
## <a name="regular-expressions-and-masks"></a>正則運算式和遮罩  
 雖然您可以使用正則運算式和遮罩來驗證使用者輸入，但它們並不完全相同。 正則運算式可以表達比遮罩更複雜的模式，但遮罩可以更簡潔且以文化特性相關的格式表達相同的資訊。  
  
 下表比較四個正則運算式以及每一個正則運算式和對等的遮罩。  
  
|規則運算式|Mask|注意|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|`/`遮罩中的字元是邏輯日期分隔符號，而且會顯示給使用者，作為應用程式目前文化特性的適當日期分隔符號。|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|日期 (day、month 縮寫和 year) ，其中三個字母的月份縮寫會以首字母開頭，後面接著兩個小寫字母的形式顯示。|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|美國電話號碼，區碼選擇性。 如果使用者不想輸入選擇性字元，則可以輸入空格或將滑鼠指標直接放在前0所代表之遮罩中的位置。|  
|`$\d{6}.00`|`$999,999.00`|介於0到999999範圍內的貨幣值。 Currency、千和小字元將會在執行時間取代為其文化特性特定的對等專案。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [在 Visual Basic 中驗證字串](validating-strings.md)
- [MaskedTextBox 控制項](/dotnet/desktop/winforms/controls/maskedtextbox-control-windows-forms)
