---
title: 事件 &#39;&lt;eventname1&gt;&#39; 無法實作事件 &#39;&lt;事件名稱 2>&gt;&#39; 介面 &#39;&lt;介面&gt;&#39; 因為它們的委派類型 &#39;&lt;delegate1&gt;&#39; 和 &#39;&lt;delegate2&gt;&#39; 不相符
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b0fcbbf8a6e23270e4dcbf9d813c773e1522a92a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a>事件 &#39;&lt;eventname1&gt;&#39; 無法實作事件 &#39;&lt;事件名稱 2>&gt;&#39; 介面 &#39;&lt;介面&gt;&#39; 因為它們的委派類型 &#39;&lt;delegate1&gt;&#39; 和 &#39;&lt;delegate2&gt;&#39; 不相符
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]無法實作事件，因為事件的委派類型的介面中的事件委派類型不相符。 如果您在介面中定義多個事件，然後嘗試將它們與相同的事件一起實作，則會發生這個錯誤。 只有在使用 `As` 語法宣告所有實作的事件並指定相同的委派類型時，事件才能實作兩個以上的事件。  
  
 **錯誤 ID:** BC31423  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請分別實作這些事件。  
  
     -或-  
  
-   在介面中使用定義的事件`As`語法，並指定相同的委派類型。  
  
## <a name="see-also"></a>另請參閱  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [事件](../../../visual-basic/programming-guide/language-features/events/index.md)
