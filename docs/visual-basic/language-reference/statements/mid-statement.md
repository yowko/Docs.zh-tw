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
ms.openlocfilehash: 90408fd8a8cfc9b74c8422d0571d61f8534403f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404445"
---
# <a name="mid-statement"></a>Mid 陳述式
以另一個字串中的字元取代變數中指定的字元數 `String` 。  
  
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
 必要。 `String`要修改之變數的名稱。  
  
 `Start`  
 必要。 `Integer` 運算式。 中的字元位置 `Target` ：取代文字的開始位置。 `Start`使用以一個為基礎的索引。  
  
 `Length`  
 選擇性。 `Integer` 運算式。 要取代的字元數。 如果省略， `String` 則會使用所有。  
  
 `StringExpression`  
 必要。 `String`取代部分的運算式 `Target` 。  
  
## <a name="exceptions"></a>例外狀況  
  
|例外狀況型別|狀況|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start`<= 0 或 `Length` < 0。|  
  
## <a name="remarks"></a>備註  
 已取代的字元數一律小於或等於中的字元數 `Target` 。  
  
 Visual Basic 具有 <xref:Microsoft.VisualBasic.Strings.Mid%2A> 函數和 `Mid` 語句。 這些專案都是在字串中以指定的字元數來運作，但是函式會傳回 `Mid` 字元，而語句則會 `Mid` 取代這些字元。 如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Strings.Mid%2A> 。  
  
> [!NOTE]
> `MidB`舊版 Visual Basic 的語句會取代子字串（以位元組為單位），而不是字元。 它主要是用來在雙位元組字集（DBCS）應用程式中轉換字串。 所有 Visual Basic 字串都是 Unicode，不再受到 `MidB` 支援。  
  
## <a name="example"></a>範例  
 這個範例會使用 `Mid` 語句，將字串變數中指定數目的字元取代為另一個字串中的字元。  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>規格需求  
 **命名空間：** [Microsoft.](../runtime-library-members.md)  
  
 **模組：**`Strings`  
  
 **元件：** Visual Basic 執行時間程式庫（在 Microsoft 中）  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [字串](../../programming-guide/language-features/strings/index.md)
- [Visual Basic 中的字串簡介](../../programming-guide/language-features/strings/introduction-to-strings.md)
