---
title: Throw 陳述式 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50ada551c32b8296f0dad2ae929ca9c81a14a711
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
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
  
 **模組：**`Interaction`  
  
 **組件：** Visual Basic Runtime Library （位於 Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>另請參閱  
 [Try...Catch...Finally 陳述式](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [On Error 陳述式](../../../visual-basic/language-reference/statements/on-error-statement.md)
