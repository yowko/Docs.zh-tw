---
title: Optional (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
ms.openlocfilehash: 67ceedffecdfba8ec0c2829a3af31d194f18bd88
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820785"
---
# <a name="optional-visual-basic"></a>Optional (Visual Basic)
指定呼叫程序時，可以省略程序引數。  
  
## <a name="remarks"></a>備註  
 每一個選擇性的參數，您必須指定該參數的預設值的常數運算式。 如果運算式評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，值的資料類型的預設值做為參數的預設值。  
  
 如果參數清單包含選擇性參數，便會跟隨它的每個參數也必須是選擇性。  
  
 `Optional` 修飾詞可用於以下內容：  
  
-   [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  呼叫程序時使用或不含選擇性參數，您可以依位置或依名稱傳遞引數。 如需詳細資訊，請參閱 <<c0> [ 傳遞引數依位置和名稱](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)。  
  
> [!NOTE]
>  您也可以使用多載，以定義與選擇性參數的程序。 如果您有一個選擇性參數，您可以定義兩個程序，一個可接受的參數，其中並不多載的版本。 如需詳細資訊，請參閱 [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)。  
  
## <a name="example"></a>範例  
 下列範例會定義具有一個選擇性參數的程序。  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何呼叫程序，使用依位置傳遞的引數，並以依名稱傳遞的引數。 程序中的兩個選擇性參數。  
  
 [!code-vb[VbVbalrKeywords#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class8.vb#21)]  
  
## <a name="see-also"></a>另請參閱

- [參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)
- [選擇性參數](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
