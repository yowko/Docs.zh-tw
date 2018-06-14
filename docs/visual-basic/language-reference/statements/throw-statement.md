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
ms.openlocfilehash: cfa53b3585846da25711739fb7af4bde21746b29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602849"
---
# <a name="throw-statement-visual-basic"></a>Throw 陳述式 (Visual Basic)
擲回例外狀況程序內。  
  
## <a name="syntax"></a>語法  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a>組件  
 `expression`  
 提供要擲回的例外狀況的相關資訊。 當位於`Catch`陳述式，否則為必要項。  
  
## <a name="remarks"></a>備註  
 `Throw`陳述式會擲回的例外狀況，您可以處理與結構化例外狀況處理程式碼 (`Try`...`Catch`...`Finally`) 或非結構化例外狀況處理程式碼 (`On Error GoTo`)。 您可以使用`Throw`陳述式來攔截錯誤程式碼內，因為 Visual Basic 將呼叫堆疊向上移動，直到找到適當的例外狀況處理程式碼。  
  
 A`Throw`沒有運算式的陳述式只可用在`Catch`陳述式，在其中案例陳述式會重新擲回目前所處理的例外狀況`Catch`陳述式。  
  
 `Throw`陳述式重設的呼叫堆疊`expression`例外狀況。 如果`expression`未提供，呼叫堆疊會保持不變。 您可以存取透過例外狀況的呼叫堆疊<xref:System.Exception.StackTrace%2A>屬性。  
  
## <a name="example"></a>範例  
 下列程式碼會使用`Throw`陳述式擲回例外狀況：  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## <a name="requirements"></a>需求  
 **命名空間：** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **模組：** `Interaction`  
  
 **組件：** Visual Basic Runtime Library （位於 Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>另請參閱  
 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [On Error 陳述式](../../../visual-basic/language-reference/statements/on-error-statement.md)
