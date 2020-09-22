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
ms.openlocfilehash: 0379a6cabe819365b22994a5e4f9353d98b2c768
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873192"
---
# <a name="mid-statement"></a>Mid 陳述式

以另一個字串中的字元取代變數中指定的字元數 `String` 。  
  
## <a name="syntax"></a>Syntax  
  
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
 必要。 `Integer` 運算式。 `Target`取代文字開頭的字元位置。 `Start` 使用以一為基礎的索引。  
  
 `Length`  
 選擇性。 `Integer` 運算式。 要取代的字元數。 如果省略， `String` 則會使用所有。  
  
 `StringExpression`  
 必要。 `String` 取代部分的運算式 `Target` 。  
  
## <a name="exceptions"></a>例外狀況  
  
|例外狀況類型|條件|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start` <= 0 或 `Length` < 0。|  
  
## <a name="remarks"></a>備註  

 被取代的字元數一律小於或等於中的字元數 `Target` 。  
  
 Visual Basic 有 <xref:Microsoft.VisualBasic.Strings.Mid%2A> 函數和 `Mid` 語句。 這些專案都是在字串中的指定字元數上運作，但函數會在 `Mid` `Mid` 語句取代字元時傳回字元。 如需詳細資訊，請參閱<xref:Microsoft.VisualBasic.Strings.Mid%2A>。  
  
> [!NOTE]
> `MidB`舊版 Visual Basic 的語句會取代以位元組為單位的子字串，而不是字元。 它主要用來將雙位元組字元集中的字串轉換 (DBCS) 應用程式。 所有 Visual Basic 字串都是 Unicode，不再 `MidB` 支援。  
  
## <a name="example"></a>範例  

 這個範例會使用 `Mid` 語句，將字串變數中指定的字元數取代為另一個字串中的字元。  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>規格需求  

 **命名空間：** [Microsoft.](../runtime-library-members.md)  
  
 **課程模組：**`Strings`  
  
 **元件：** Microsoft.VisualBasic.dll) 中的 Visual Basic 執行時間程式庫 (  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [字串](../../programming-guide/language-features/strings/index.md)
- [Visual Basic 中的字串簡介](../../programming-guide/language-features/strings/introduction-to-strings.md)
