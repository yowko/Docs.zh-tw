---
title: "事件 &quot;&lt;eventname1&gt;&quot;無法實作事件&quot;&lt;eventname2&gt;&quot;在介面&quot;&lt;介面&gt;&quot; 因為其委派型別&lt;delegate1&gt;&quot;和&quot;&lt;delegate2&gt;&quot; 不符 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
dev_langs:
- VB
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: 6
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: b6253b3e9ad07c3715c55a8cfd0891792b45a452
ms.lasthandoff: 03/13/2017

---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a>事件 '&lt;eventname1&gt;'無法實作事件'&lt;eventname2&gt;'在介面'&lt;介面&gt;' 因為其委派型別&lt;delegate1&gt;'和'&lt;delegate2&gt;' 不相符
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]無法實作事件，因為事件之委派型別和介面中的事件之委派型別不相符。 如果您在介面中定義多個事件，然後嘗試將它們與相同的事件一起實作，則會發生這個錯誤。 只有在使用 `As` 語法宣告所有實作的事件並指定相同的委派類型時，事件才能實作兩個以上的事件。  
  
 **錯誤識別碼︰** BC31423  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請分別實作這些事件。  
  
     -或-  
  
-   使用的介面中定義之事件`As`語法，並指定相同的委派型別。  
  
## <a name="see-also"></a>另請參閱  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [事件](../../../visual-basic/programming-guide/language-features/events/index.md)
