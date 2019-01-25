---
title: HOW TO：宣告自訂事件以避免封鎖 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: e1fed68f4abffb0e20230f55b0ddeffc63f7c78d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691537"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>HOW TO：宣告自訂事件以避免封鎖 (Visual Basic)
有幾種情況時很重要的一個事件處理常式不會封鎖後續的事件處理常式。 自訂事件可讓要以非同步方式呼叫其事件處理常式的事件。  
  
 根據預設，事件宣告備份存放區欄位會是以序列方式結合了所有事件處理常式的多點傳送的委派。 這表示，如果有一個處理常式會花很長的時間才能完成，它會封鎖其他處理常式到完成為止。 （正常運作的事件處理常式應該永遠不會執行長時間或潛在的封鎖作業）。  
  
 而不是使用 Visual Basic 提供的事件的預設實作，您可以使用自訂的事件，以非同步方式執行的事件處理常式。  
  
## <a name="example"></a>範例  
 在此範例中，`AddHandler`存取子新增的每個處理常式的委派`Click`事件，以<xref:System.Collections.ArrayList>儲存在`EventHandlerList`欄位。  
  
 當程式碼會引發`Click`事件，`RaiseEvent`存取子會以非同步方式使用的所有事件處理常式委派叫都用<xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>方法。 該方法會叫用背景工作執行緒上的每個處理常式，並會立即傳回，讓處理常式無法封鎖彼此。  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-avoid-blocking_1.vb)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [如何：宣告自訂事件以節省記憶體](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
