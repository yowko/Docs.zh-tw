---
title: "RemoveHandler 陳述式 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
dev_langs:
- VB
helpviewer_keywords:
- RemoveHandler keyword
- RemoveHandler statement
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d35de576bd9e267800acc2a9bfd5761dd977622f
ms.lasthandoff: 03/13/2017

---
# <a name="removehandler-statement"></a>RemoveHandler 陳述式
移除的事件與事件處理常式之間的關聯。  
  
## <a name="syntax"></a>語法  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`event`|要處理事件的名稱。|  
|`eventhandler`|目前正在處理的事件程序的名稱。|  
  
## <a name="remarks"></a>備註  
 `AddHandler`和`RemoveHandler`陳述式可讓您能夠啟動和停止程式執行期間的特定事件的事件處理。  
  
> [!NOTE]
>  自訂事件，`RemoveHandler`陳述式會叫用此事件`RemoveHandler`存取子。 如需自訂事件的詳細資訊，請參閱[Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)。  
  
## <a name="example"></a>範例  
 [!code-vb[VbVbalrEvents #&17;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [AddHandler 陳述式](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [控制代碼](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)   
 [事件](../../../visual-basic/programming-guide/language-features/events/index.md)
