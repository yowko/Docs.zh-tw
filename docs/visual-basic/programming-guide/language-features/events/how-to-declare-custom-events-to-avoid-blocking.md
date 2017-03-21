---
title: "如何︰ 宣告自訂事件以避免封鎖 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declaring events, custom
- events [Visual Basic], custom
- custom events
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: 12
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
ms.openlocfilehash: 34b222bdbfdae0673b7150c220ca477b7e286dda
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>如何：宣告自訂事件以避免封鎖 (Visual Basic)
重要的一個事件處理常式不會封鎖後續的事件處理常式時，有幾種情況。 自訂事件可讓您以非同步方式呼叫其事件處理常式的事件。  
  
 根據預設，事件宣告備份存放區欄位會是連續結合所有事件處理常式的多點傳送的委派。 這表示，如果某個處理常式需要很長的時間才能完成，它會封鎖其他處理常式到完成為止。 （正常運作的事件處理常式應該永遠不會執行時間較長或潛在的封鎖作業）。  
  
 而不是使用 Visual Basic 提供的事件的預設實作，您可以使用自訂的事件，以非同步方式執行的事件處理常式。  
  
## <a name="example"></a>範例  
 在此範例中，`AddHandler`存取子會將每個處理常式的委派加入`Click`事件<xref:System.Collections.ArrayList>儲存在`EventHandlerList`欄位。</xref:System.Collections.ArrayList>  
  
 當程式碼會引發`Click`事件，`RaiseEvent`存取子會以非同步方式使用的所有事件處理常式委派叫都用<xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>方法。</xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> 該方法會叫用背景工作執行緒上的每個處理常式，並會立即傳回，所以處理常式無法封鎖彼此。  
  
 [!code-vb[VbVbalrEvents #&27;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Collections.ArrayList></xref:System.Collections.ArrayList>   
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A></xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>   
 [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)   
 [如何：宣告自訂事件以節省記憶體](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
