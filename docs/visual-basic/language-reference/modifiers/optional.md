---
title: Optional (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3aa01c2c1ae731c8fe00fdee24521760db69e624
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="optional-visual-basic"></a>Optional (Visual Basic)
指定呼叫程序時，可以省略程序引數。  
  
## <a name="remarks"></a>備註  
 每一個選擇性參數，您必須指定為該參數的預設值的常數運算式。 如果運算式評估為[Nothing](../../../visual-basic/language-reference/nothing.md)，預設值的數值資料類型作為參數的預設值。  
  
 如果參數清單包含一個選擇性參數，它後面的每個參數也必須是選擇性。  
  
 `Optional` 修飾詞可用於以下內容：  
  
-   [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  當呼叫程序使用或不含選擇性參數，您可以在依位置或名稱傳遞引數。 如需詳細資訊，請參閱[傳遞引數依位置和名稱](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)。  
  
> [!NOTE]
>  您也可以使用多載，以定義具有選擇性參數的程序。 如果您有一個選擇性參數，您可以定義程序接受參數，一個沒有兩個多載的版本。 如需詳細資訊，請參閱[程序多載](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)。  
  
## <a name="example"></a>範例  
 下列範例會定義具有選擇性參數的程序。  
  
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
 下列範例會示範如何依位置傳遞引數與依名稱傳遞引數呼叫的程序。 程序有兩個選擇性參數。  
  
 [!code-vb[VbVbalrKeywords#21](../../../visual-basic/language-reference/codesnippet/VisualBasic/optional_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [選擇性參數](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
