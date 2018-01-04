---
title: "限制的 Windows Form Timer 元件 &#39; s [間隔] 屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ec53957a61806239fdd41761de6e172681b7497b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="limitations-of-the-windows-forms-timer-component39s-interval-property"></a>限制的 Windows Form Timer 元件 &#39; s [間隔] 屬性
Windows Form<xref:System.Windows.Forms.Timer>元件有<xref:System.Windows.Forms.Timer.Interval%2A>屬性，指定一個計時器事件和下之間所經過的毫秒數。 除非已停用該元件，計時器會繼續接收<xref:System.Windows.Forms.Timer.Tick>大致相等間隔的時間的事件。  
  
 這個元件是專為 Windows Form 環境所設計。 如果您需要適用於伺服器環境的計時器，請參閱[伺服器架構的計時器簡介](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)。  
  
## <a name="the-interval-property"></a>[間隔] 屬性  
 <xref:System.Windows.Forms.Timer.Interval%2A>屬性有幾項限制來進行程式設計時，請考慮<xref:System.Windows.Forms.Timer>元件：  
  
-   如果您的應用程式或其他應用程式在系統上進行大量的需求 — 例如長迴圈、 需要大量計算，或磁碟機、 網路或通訊埠存取，您的應用程式可能不會得到計時器事件，通常為<xref:System.Windows.Forms.Timer.Interval%2A>屬性會指定。  
  
-   間隔不保證在時間上完全停用。 若要確保精確度，計時器應該檢查系統時鐘，如有需要而嘗試追蹤的累積的時間在內部。  
  
-   有效位數<xref:System.Windows.Forms.Timer.Interval%2A>屬性是以毫秒為單位。 某些電腦提供高解析度的計數器高於毫秒的解析度。 這類計數器的可用性取決於您的電腦的處理器硬體。 如需詳細資訊，請參閱 172338，」 方式來使用 QueryPerformanceCounter 到時間程式碼，"在 Microsoft 知識庫文件在 http://support.microsoft.com。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.Timer>  
 [Timer 元件](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Timer 元件概觀](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
