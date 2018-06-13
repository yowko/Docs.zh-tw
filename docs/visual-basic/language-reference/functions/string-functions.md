---
title: 字串函式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- string functions
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
ms.openlocfilehash: f6c7f28cee03c2d5ac258cf1e2c8956225334f7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604142"
---
# <a name="string-functions-visual-basic"></a>字串函式 (Visual Basic)
下表列出 Visual Basic 提供搜尋和操作字串的函式。  
  
|.NET framework 方法|描述|  
|---------------------------|-----------------|  
|<xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>|傳回`Integer`值，表示為字元的對應字元碼。|  
|<xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>|傳回與指定的字元碼相關聯的字元。|  
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|傳回以零為起始的陣列，包含子集`String`陣列根據指定的篩選準則。|  
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|傳回根據格式中所包含的指示格式化字串`String`運算式。|  
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|傳回格式化為使用系統控制台 中定義的貨幣符號的貨幣值的運算式。|  
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|傳回代表日期/時間值的字串運算式。|  
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|傳回格式化的數字的運算式。|  
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|傳回格式化為百分比 (也就是乘以 100) 且尾端包含 % 字元的運算式。|  
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|傳回整數，指定一個字串在另一個字串的第一個出現的起始位置。|  
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|傳回一個字串在另一個，從字串右側開始的第一次出現的位置。|  
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|傳回建立聯結的子字串陣列中包含的數字的字串。|  
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|傳回字串或字元轉換成小寫。|  
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|傳回字串，包含指定的從左邊的字串的字元數。|  
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|傳回整數，其中包含在字串中的字元數。|  
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|傳回靠左對齊的字串，包含調整為指定之長度的指定的字串。|  
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|傳回字串，包含前置空格的指定字串的複本。|  
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|傳回字串，包含指定的從字串的字元數。|  
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|傳回字串中指定的子字串已取代為另一個子字串指定的次數。|  
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|傳回字串，包含指定的從字串右側的字元數。|  
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|傳回靠右對齊的字串，包含調整為指定之長度的指定的字串。|  
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|傳回字串，包含不含尾端空格的指定字串的複本。|  
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|傳回字串，其中包含指定的空格數目。|  
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|傳回以零為起始的一維陣列，包含指定的數目的子字串。|  
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|會傳回-1、 0 或 1 會根據字串比較的結果。|  
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|傳回轉換成指定的字串。|  
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|傳回字串或物件，內含指定的字元重複指定的次數。|  
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|傳回指定之字串的字元順序會顛倒的字串。|  
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|傳回字串，包含任何開頭或尾端空格的指定字串的複本。|  
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|傳回字串或包含指定的字串轉換成大寫的字元。|  
  
 您可以使用[Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)陳述式來設定是否使用不區分大小寫的文字比較字串排序次序取決於您的系統地區設定 (`Text`) 或內部的二進位表示法的字元 （`Binary`). 預設文字比較方法是`Binary`。  
  
## <a name="example"></a>範例  
 這個範例會使用`UCase`函數來傳回字串的大寫版本。  
  
 [!code-vb[VbVbalrStrings#31](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_1.vb)]  
  
## <a name="example"></a>範例  
 這個範例會使用`LTrim`函式刪除前置空格和`RTrim`函式刪除結尾的空格字串變數中。 它會使用`Trim`函式來刪除這兩種類型的空格。  
  
 [!code-vb[VbVbalrStrings#25](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_2.vb)]  
  
## <a name="example"></a>範例  
 這個範例會使用`Mid`函數從字串傳回指定的字元數。  
  
 [!code-vb[VbVbalrStrings#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_3.vb)]  
  
## <a name="example"></a>範例  
 這個範例會使用`Len`字串中傳回的字元數。  
  
 [!code-vb[VbVbalrStrings#33](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_4.vb)]  
  
## <a name="example"></a>範例  
 這個範例會使用`InStr`函式傳回一個字串在另一個字串的第一次出現的位置。  
  
 [!code-vb[VbVbalrStrings#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_5.vb)]  
  
## <a name="example"></a>範例  
 此範例示範的各種用法`Format`函式來同時使用的格式化值`String`格式及使用者定義的格式。 日期分隔符號 (`/`)，時間分隔符號 (`:`)，和 AM/PM 指標 (`t`和`tt`)，實際的格式化的輸出，顯示您的系統程式碼使用的地區設定而定。 當時間和日期會顯示在開發環境中，會使用簡短時間格式和程式碼的地區設定的簡短日期格式。  
  
> [!NOTE]
>  針對使用 24 小時制，AM/PM 標記的地區設定 (`t`和`tt`) 顯示執行任何動作。  
  
 [!code-vb[VbVbalrStrings#27](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_6.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)  
 [Visual Basic 執行階段程式庫成員](../../../visual-basic/language-reference/runtime-library-members.md)  
 [字串操作摘要](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)
