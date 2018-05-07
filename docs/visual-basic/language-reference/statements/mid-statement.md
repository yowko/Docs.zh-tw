---
title: Mid 陳述式
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
ms.openlocfilehash: 90b805df902dcdfebe85421583dd54e9af04bec9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mid-statement"></a>Mid 陳述式
取代指定的字元數`String`變數與另一個字串的字元。  
  
## <a name="syntax"></a>語法  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>組件  
 `Target`  
 必要。 名稱`String`修改變數。  
  
 `Start`  
 必要。 `Integer` 運算式。 字元位置`Target`開始取代文字。 `Start` 會使用 1 為基底的索引。  
  
 `Length`  
 選擇性。 `Integer` 運算式。 要取代的字元數。 如果省略，則所有`String`用。  
  
 `StringExpression`  
 必要。 `String` 取代部份的運算式`Target`。  
  
## <a name="exceptions"></a>例外狀況  
  
|例外狀況類型|條件|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start` < = 0 或`Length`< 0。|  
  
## <a name="remarks"></a>備註  
 被取代的字元數目一律為小於或等於中的字元數`Target`。  
  
 Visual Basic 擁有<xref:Microsoft.VisualBasic.Strings.Mid%2A>函式和`Mid`陳述式。 兩者的指定數目的字元在字串中, 操作這些項目但`Mid`函式會傳回的字元時`Mid`陳述式會取代字元。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Strings.Mid%2A>。  
  
> [!NOTE]
>  `MidB`較舊版本的 Visual Basic 的陳述式可以取代位元組，而非字元的子字串。 它是主要用來轉換雙位元組字元集 (DBCS) 應用程式中的字串。 所有的 Visual Basic 字串都位於 Unicode，和`MidB`不再支援。  
  
## <a name="example"></a>範例  
 這個範例會使用`Mid`陳述式來取代指定的字串變數中的字元數，另一個字串的字元。  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/mid-statement_1.vb)]  
  
## <a name="requirements"></a>需求  
 **命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **模組：** `Strings`  
  
 **組件︰** [!INCLUDE[vbprvbruntime](~/includes/vbprvbruntime-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 [字串](../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [Visual Basic 中的字串簡介](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
