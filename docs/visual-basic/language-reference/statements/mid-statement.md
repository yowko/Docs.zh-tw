---
title: Mid 語句 (Visual Basic)
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
ms.openlocfilehash: 212ce1f06a01c39acbce43d8d069dae3526b1b4d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963543"
---
# <a name="mid-statement"></a>Mid 陳述式
以另一個字串中的字元取代`String`變數中指定的字元數。  
  
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
 必要項。 要修改之`String`變數的名稱。  
  
 `Start`  
 必要項。 `Integer`運算式. 中`Target`的字元位置: 取代文字的開始位置。 `Start`使用以一個為基礎的索引。  
  
 `Length`  
 選擇性。 `Integer`運算式. 要取代的字元數。 如果省略, `String`則會使用所有。  
  
 `StringExpression`  
 必要項。 `String`取代部分的`Target`運算式。  
  
## <a name="exceptions"></a>例外狀況  
  
|例外狀況類型|條件|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start`< = 0 或`Length` < 0。|  
  
## <a name="remarks"></a>備註  
 已取代的字元數一律小於或等於中`Target`的字元數。  
  
 Visual Basic 具有<xref:Microsoft.VisualBasic.Strings.Mid%2A>函數`Mid`和語句。 這些專案都是在字串中以指定的字元數來運作, 但是`Mid`函式會傳回字元, `Mid`而語句則會取代這些字元。 如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Strings.Mid%2A>。  
  
> [!NOTE]
> 舊版`MidB` Visual Basic 的語句會取代子字串 (以位元組為單位), 而不是字元。 它主要是用來在雙位元組字集 (DBCS) 應用程式中轉換字串。 所有 Visual Basic 字串都是 Unicode, `MidB`不再受到支援。  
  
## <a name="example"></a>範例  
 這個範例會使用`Mid`語句, 將字串變數中指定數目的字元取代為另一個字串中的字元。  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>需求  
 **命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **模組:** `Strings`  
  
 **Assembly**Visual Basic Runtime Library (位於 Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [字串](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Visual Basic 中的字串簡介](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
