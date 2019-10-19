---
title: Mid 語句（Visual Basic）
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: ea22af2eb896542bfc329e087101608e08c45107
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581481"
---
# <a name="mid-statement"></a>Mid 陳述式
以另一個字串中的字元取代 `String` 變數中指定的字元數。  
  
## <a name="syntax"></a>語法  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>組件  
 `Target`  
 必要項。 要修改之 `String` 變數的名稱。  
  
 `Start`  
 必要項。 `Integer` 運算式。 @No__t_0 中的字元位置會開始取代文字。 `Start` 使用以一為基礎的索引。  
  
 `Length`  
 選擇項。 `Integer` 運算式。 要取代的字元數。 如果省略，則會使用所有的 `String`。  
  
 `StringExpression`  
 必要項。 取代 `Target` 部分的 `String` 運算式。  
  
## <a name="exceptions"></a>例外狀況  
  
|例外狀況類型|條件|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start` < = 0 或 `Length` < 0。|  
  
## <a name="remarks"></a>備註  
 已取代的字元數一律小於或等於 `Target` 中的字元數。  
  
 Visual Basic 具有 <xref:Microsoft.VisualBasic.Strings.Mid%2A> 函數和 `Mid` 語句。 這些專案都是在字串中以指定的字元數來運作，但是 `Mid` 函式會傳回字元，而 `Mid` 語句則會取代這些字元。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Strings.Mid%2A>。  
  
> [!NOTE]
> 舊版 Visual Basic 的 `MidB` 語句會取代子字串（以位元組為單位），而不是字元。 它主要是用來在雙位元組字集（DBCS）應用程式中轉換字串。 所有 Visual Basic 字串都是 Unicode，而且不再支援 `MidB`。  
  
## <a name="example"></a>範例  
 這個範例會使用 `Mid` 語句，將字串變數中指定數目的字元取代為另一個字串中的字元。  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>需求  
 **命名空間：** [Microsoft.](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **模組：** `Strings`  
  
 **元件：** Visual Basic 執行時間程式庫（在 Microsoft 中）  
  
## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [字串](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Visual Basic 中的字串簡介](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
