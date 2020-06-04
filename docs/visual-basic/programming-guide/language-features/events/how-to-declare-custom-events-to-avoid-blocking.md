---
title: 如何：宣告自訂事件以避免封鎖
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
ms.openlocfilehash: a9f9529d468a036d81c4e436429cbdb3207efd6e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405153"
---
# <a name="how-to-declare-custom-events-to-avoid-blocking-visual-basic"></a>如何：宣告自訂事件以避免封鎖 (Visual Basic)
有幾種情況很重要：一個事件處理常式不會封鎖後續的事件處理常式。 自訂事件可讓事件以非同步方式呼叫其事件處理常式。  
  
 根據預設，事件宣告的「備份存放區」欄位是一個多播委派，可將所有事件處理常式序列結合在一起。 這表示如果某個處理常式需要很長的時間才能完成，它會封鎖其他處理常式，直到它完成為止。 （行為良好的事件處理常式應該永遠不會執行冗長或可能封鎖的作業）。  
  
 您可以使用自訂事件，以非同步方式執行事件處理常式，而不是使用 Visual Basic 提供之事件的預設執行。  
  
## <a name="example"></a>範例  
 在此範例中， `AddHandler` 存取子會將事件之每個處理常式的委派加入 `Click` 至 <xref:System.Collections.ArrayList> 儲存在欄位中的 `EventHandlerList` 。  
  
 當程式碼引發 `Click` 事件時， `RaiseEvent` 存取子會使用方法，以非同步方式叫用所有的事件處理常式委派 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> 。 該方法會叫用工作者執行緒上的每個處理常式，並立即傳回，因此處理程式無法彼此封鎖。  
  
 [!code-vb[VbVbalrEvents#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#27)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Collections.ArrayList>
- <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>
- [事件](index.md)
- [如何：宣告自訂事件以節省記憶體](how-to-declare-custom-events-to-conserve-memory.md)
