---
title: Windows Form 中的電源管理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
ms.openlocfilehash: 6bb9b4f30a88ece93b17ff2510087b220d538738
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979715"
---
# <a name="power-management-in-windows-forms"></a>Windows Form 中的電源管理
Windows Forms 應用程式可以利用電源管理功能的 Windows 作業系統中。 您的應用程式可以監視電腦的電源狀態，並採取動作，發生狀態變更時。 比方說，如果您的應用程式正在執行的可攜式電腦上，您可能要停用您的應用程式中的特定功能，當電腦的電池電力低於特定層級。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]提供<xref:Microsoft.Win32.SystemEvents.PowerModeChanged>電源狀態，例如當使用者暫停或繼續作業系統，或 AC 電源狀態或電池狀態變更的變更時，就會發生的事件。 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>屬性<xref:System.Windows.Forms.SystemInformation>類別可以用來查詢目前的狀態，如下列程式碼範例所示。  
  
 [!code-csharp[PowerMode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 除了<xref:System.Windows.Forms.BatteryChargeStatus>列舉型別<xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>屬性也包含列舉型別來判斷電池容量 (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) 和電池充電百分比 (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>， <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>)。  
  
 您可以使用<xref:System.Windows.Forms.Application.SetSuspendState%2A>方法的<xref:System.Windows.Forms.Application>讓電腦進入休眠狀態或暫停模式。 如果`force`引數設定為`false`，作業系統會廣播到所有要求暫止的權限的應用程式事件。 如果`disableWakeEvent`引數設定為`true`，作業系統會停用網路喚醒的所有事件。  
  
 下列程式碼範例示範如何讓電腦進入休眠狀態。  
  
 [!code-csharp[PowerMode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
