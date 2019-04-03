---
title: Throw 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: 2494eac2f61f112f3ba6321ada7404f8cd618049
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821366"
---
# <a name="throw-statement-visual-basic"></a>Throw 陳述式 (Visual Basic)
擲回例外狀況程序內。  
  
## <a name="syntax"></a>語法  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a>組件  
 `expression`  
 提供將會擲回的例外狀況的相關資訊。 選擇性時位於`Catch`陳述式，否則為必要項。  
  
## <a name="remarks"></a>備註  
 `Throw`陳述式會擲回的例外狀況，您可以使用結構化例外狀況處理程式碼處理 (`Try`...`Catch`...`Finally`) 或非結構化例外狀況處理程式碼 (`On Error GoTo`)。 您可以使用`Throw`陳述式來截取您的程式碼中的錯誤，因為 Visual Basic 會在呼叫堆疊中向上移動，直到找到適當的例外狀況處理程式碼。  
  
 A`Throw`但沒有運算式的陳述式僅適用於在`Catch`陳述式，在其中 case 陳述式會重新擲回目前正在處理的例外狀況`Catch`陳述式。  
  
 `Throw`陳述式會重設的呼叫堆疊`expression`例外狀況。 如果`expression`未提供，呼叫堆疊會保持不變。 您可以透過例外狀況的呼叫堆疊<xref:System.Exception.StackTrace%2A>屬性。  
  
## <a name="example"></a>範例  
 下列程式碼會使用`Throw`擲回例外狀況的陳述式：  
  
 [!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]  
  
## <a name="requirements"></a>需求  
 **命名空間：**[Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **模組：** `Interaction`  
  
 **組件：** Visual Basic Runtime Library (位於 Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>另請參閱

- [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [On Error 陳述式](../../../visual-basic/language-reference/statements/on-error-statement.md)
