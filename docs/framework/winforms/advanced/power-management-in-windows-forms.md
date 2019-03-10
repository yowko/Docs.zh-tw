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
ms.openlocfilehash: 77d2096239ec70f98ebfc299f1eda75ad4490be9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712418"
---
# <a name="power-management-in-windows-forms"></a><span data-ttu-id="4ad63-102">Windows Form 中的電源管理</span><span class="sxs-lookup"><span data-stu-id="4ad63-102">Power Management in Windows Forms</span></span>
<span data-ttu-id="4ad63-103">Windows Forms 應用程式可以利用電源管理功能的 Windows 作業系統中。</span><span class="sxs-lookup"><span data-stu-id="4ad63-103">Your Windows Forms applications can take advantage of the power management features in the Windows operating system.</span></span> <span data-ttu-id="4ad63-104">您的應用程式可以監視電腦的電源狀態，並採取動作，發生狀態變更時。</span><span class="sxs-lookup"><span data-stu-id="4ad63-104">Your applications can monitor the power status of a computer and take action when a status change occurs.</span></span> <span data-ttu-id="4ad63-105">比方說，如果您的應用程式正在執行的可攜式電腦上，您可能要停用您的應用程式中的特定功能，當電腦的電池電力低於特定層級。</span><span class="sxs-lookup"><span data-stu-id="4ad63-105">For example, if your application is running on a portable computer, you might want to disable certain features in your application when the computer's battery charge falls under a certain level.</span></span>  
  
 <span data-ttu-id="4ad63-106">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]提供<xref:Microsoft.Win32.SystemEvents.PowerModeChanged>電源狀態，例如當使用者暫停或繼續作業系統，或 AC 電源狀態或電池狀態變更的變更時，就會發生的事件。</span><span class="sxs-lookup"><span data-stu-id="4ad63-106">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] provides a <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> event that occurs whenever there is a change in power status, such as when a user suspends or resumes the operating system, or when the AC power status or battery status changes.</span></span> <span data-ttu-id="4ad63-107"><xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>屬性<xref:System.Windows.Forms.SystemInformation>類別可以用來查詢目前的狀態，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="4ad63-107">The <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property of the <xref:System.Windows.Forms.SystemInformation> class can be used to query for the current status, as shown in the following code example.</span></span>  
  
 [!code-csharp[PowerMode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 <span data-ttu-id="4ad63-108">除了<xref:System.Windows.Forms.BatteryChargeStatus>列舉型別<xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>屬性也包含列舉型別來判斷電池容量 (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) 和電池充電百分比 (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>， <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>)。</span><span class="sxs-lookup"><span data-stu-id="4ad63-108">Besides the <xref:System.Windows.Forms.BatteryChargeStatus> enumerations, the <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property also contains enumerations for determining battery capacity (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) and battery charge percentage (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span></span>  
  
 <span data-ttu-id="4ad63-109">您可以使用<xref:System.Windows.Forms.Application.SetSuspendState%2A>方法的<xref:System.Windows.Forms.Application>讓電腦進入休眠狀態或暫停模式。</span><span class="sxs-lookup"><span data-stu-id="4ad63-109">You can use the <xref:System.Windows.Forms.Application.SetSuspendState%2A> method of the <xref:System.Windows.Forms.Application> to put a computer into hibernation or suspend mode.</span></span> <span data-ttu-id="4ad63-110">如果`force`引數設定為`false`，作業系統會廣播到所有要求暫止的權限的應用程式事件。</span><span class="sxs-lookup"><span data-stu-id="4ad63-110">If the `force` argument is set to `false`, the operating system will broadcast an event to all applications requesting permission to suspend.</span></span> <span data-ttu-id="4ad63-111">如果`disableWakeEvent`引數設定為`true`，作業系統會停用網路喚醒的所有事件。</span><span class="sxs-lookup"><span data-stu-id="4ad63-111">If the `disableWakeEvent` argument is set to `true`, the operating system disables all wake events.</span></span>  
  
 <span data-ttu-id="4ad63-112">下列程式碼範例示範如何讓電腦進入休眠狀態。</span><span class="sxs-lookup"><span data-stu-id="4ad63-112">The following code example demonstrates how to put a computer into hibernation.</span></span>  
  
 [!code-csharp[PowerMode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4ad63-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ad63-113">See also</span></span>
- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
