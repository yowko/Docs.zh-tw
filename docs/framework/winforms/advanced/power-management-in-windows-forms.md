---
title: 電源管理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- battery states
- power states
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
ms.openlocfilehash: 9ac39df43a08f62e50116c61c4bdeda4cd1c8281
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746861"
---
# <a name="power-management-in-windows-forms"></a><span data-ttu-id="617b2-102">Windows Form 中的電源管理</span><span class="sxs-lookup"><span data-stu-id="617b2-102">Power Management in Windows Forms</span></span>
<span data-ttu-id="617b2-103">您的 Windows Forms 應用程式可以利用 Windows 作業系統中的電源管理功能。</span><span class="sxs-lookup"><span data-stu-id="617b2-103">Your Windows Forms applications can take advantage of the power management features in the Windows operating system.</span></span> <span data-ttu-id="617b2-104">您的應用程式可以監視電腦的電源狀態，並在發生狀態變更時採取動作。</span><span class="sxs-lookup"><span data-stu-id="617b2-104">Your applications can monitor the power status of a computer and take action when a status change occurs.</span></span> <span data-ttu-id="617b2-105">例如，如果您的應用程式是在可攜式電腦上執行，您可能會想要在電腦的電池計量低於特定層級時，停用應用程式中的某些功能。</span><span class="sxs-lookup"><span data-stu-id="617b2-105">For example, if your application is running on a portable computer, you might want to disable certain features in your application when the computer's battery charge falls under a certain level.</span></span>  
  
 <span data-ttu-id="617b2-106">.NET Framework 提供在電源狀態變更時所發生的 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> 事件，例如當使用者暫停或繼續作業系統時，或當 AC 電源狀態或電池狀態變更時。</span><span class="sxs-lookup"><span data-stu-id="617b2-106">The .NET Framework provides a <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> event that occurs whenever there is a change in power status, such as when a user suspends or resumes the operating system, or when the AC power status or battery status changes.</span></span> <span data-ttu-id="617b2-107"><xref:System.Windows.Forms.SystemInformation> 類別的 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> 屬性可以用來查詢目前的狀態，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="617b2-107">The <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property of the <xref:System.Windows.Forms.SystemInformation> class can be used to query for the current status, as shown in the following code example.</span></span>  
  
 [!code-csharp[PowerMode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 <span data-ttu-id="617b2-108">除了 <xref:System.Windows.Forms.BatteryChargeStatus> 列舉以外，<xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> 屬性也包含用來判斷電池容量（<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>）和電池計量百分比（<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>、<xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>）的列舉。</span><span class="sxs-lookup"><span data-stu-id="617b2-108">Besides the <xref:System.Windows.Forms.BatteryChargeStatus> enumerations, the <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> property also contains enumerations for determining battery capacity (<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>) and battery charge percentage (<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>, <xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>).</span></span>  
  
 <span data-ttu-id="617b2-109">您可以使用 <xref:System.Windows.Forms.Application> 的 <xref:System.Windows.Forms.Application.SetSuspendState%2A> 方法，讓電腦進入休眠或暫停模式。</span><span class="sxs-lookup"><span data-stu-id="617b2-109">You can use the <xref:System.Windows.Forms.Application.SetSuspendState%2A> method of the <xref:System.Windows.Forms.Application> to put a computer into hibernation or suspend mode.</span></span> <span data-ttu-id="617b2-110">如果 `force` 引數設定為 `false`，則作業系統會將事件廣播至所有要求暫止許可權的應用程式。</span><span class="sxs-lookup"><span data-stu-id="617b2-110">If the `force` argument is set to `false`, the operating system will broadcast an event to all applications requesting permission to suspend.</span></span> <span data-ttu-id="617b2-111">如果 `disableWakeEvent` 引數設定為 `true`，則作業系統會停用所有喚醒事件。</span><span class="sxs-lookup"><span data-stu-id="617b2-111">If the `disableWakeEvent` argument is set to `true`, the operating system disables all wake events.</span></span>  
  
 <span data-ttu-id="617b2-112">下列程式碼範例示範如何讓電腦進入休眠狀態。</span><span class="sxs-lookup"><span data-stu-id="617b2-112">The following code example demonstrates how to put a computer into hibernation.</span></span>  
  
 [!code-csharp[PowerMode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="617b2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="617b2-113">See also</span></span>

- <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>
- <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>
- <xref:System.Windows.Forms.Application.SetSuspendState%2A>
- <xref:Microsoft.Win32.SystemEvents.SessionSwitch>
