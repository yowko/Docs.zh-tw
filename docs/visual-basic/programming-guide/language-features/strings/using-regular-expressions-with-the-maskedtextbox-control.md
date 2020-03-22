---
title: 將規則運算式與 MaskedTextBox 控制項搭配使用
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: b997f6f495fca51e888bb995fee0361d29d68048
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148280"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>在 Visual Basic 中將規則運算式與 MaskedTextBox 控制項一起搭配使用
此示例演示如何轉換簡單的正則運算式以使用<xref:System.Windows.Forms.MaskedTextBox>控制項。  
  
## <a name="description-of-the-masking-language"></a>掩蔽語言的描述  
 標準<xref:System.Windows.Forms.MaskedTextBox>掩蔽語言基於 Visual Basic 6.0`Masked Edit`中控制項所使用的語言，並且對於從該平臺遷移的使用者應熟悉。  
  
 控制項<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>的屬性<xref:System.Windows.Forms.MaskedTextBox>指定要使用的輸入遮罩。 遮罩必須是由下表中的一個或多個掩蔽元素組成的字串。  
  
|遮蔽元素|描述|正則運算式元素|  
|---------------------|-----------------|--------------------------------|  
|0|0 和 9 之間的任何位數位。 需要輸入。|\d|  
|9|數位或空格。 條目可選。|[d]？|  
|#|數位或空格。 條目可選。 如果此位置在蒙版中留空，則該位置將呈現為空格。 允許加上 （+） 和減 （-） 標誌。|[d]-？|  
|L|ASCII 字母。 需要輸入。|[a-zA-Z]|  
|?|ASCII 字母。 條目可選。|[a-zA-Z]？|  
|&|字元。 需要輸入。|[p]ll_p_l_p_p_Lo_]|  
|C|字元。 條目可選。|[p]ll_p_l_p_l_p_Lo_？|  
|A|字母。 條目可選。|\W|  
|.|適合區域性的小數位符。|無法使用。|  
|,|文化適當的數千個預留位置。|無法使用。|  
|:|適合區域性的時間分隔符號。|無法使用。|  
|/|適合區域性的日期分隔符號。|無法使用。|  
|$|文化適當的貨幣符號。|無法使用。|  
|\<|將以下所有字元轉換為小寫。|無法使用。|  
|>|將隨後的所有字元轉換為大寫。|無法使用。|  
|&#124;|撤銷上一個移位或向下移動。|無法使用。|  
|&#92;|轉義蒙版字元，將其轉換為文本。 ""\\\\是反斜線的逸出序列。|&#92;|  
|所有其他字元。|常值。 所有非遮罩元素都將在 中<xref:System.Windows.Forms.MaskedTextBox>顯示為自身。|所有其他字元。|  
  
 十進位 （.）、千分之一 （、時間（:)、日期 （/） 和貨幣 （$） 符號預設顯示應用程式區域性定義的這些符號。 可以使用<xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>屬性強制它們顯示其他區域性的符號。  
  
## <a name="regular-expressions-and-masks"></a>正則運算式和蒙版  
 儘管可以使用正則運算式和蒙版來驗證使用者輸入，但它們並不完全等效。 正則運算式可以表達比蒙版更複雜的模式，但蒙版可以更簡潔地以與文化相關的格式表達相同的資訊。  
  
 下表比較了四個正則運算式和每個運算式的等效遮罩。  
  
|規則運算式|Mask|注意|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|掩`/`碼中的字元是邏輯日期分隔符號，在使用者看來，它將顯示為適合應用程式目前範圍性的日期分隔符號。|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|以美國格式顯示三個字母的月縮寫的日期（天、月縮寫和年份），其中以大寫字母後跟兩個小寫字母顯示。|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|美國電話號碼，區號可選。 如果使用者不希望輸入可選字元，他們可以輸入空格或將滑鼠指標直接放在由前 0 表示的蒙版中的位置。|  
|`$\d{6}.00`|`$999,999.00`|0 到 999999 範圍內的貨幣值。 貨幣、千分之和十進位字元將在運行時替換為特定于區域性的等效字元。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [在 Visual Basic 中驗證字串](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [MaskedTextBox 控制項](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
