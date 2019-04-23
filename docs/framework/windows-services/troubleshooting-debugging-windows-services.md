---
title: 疑難排解：對 Windows 服務進行偵錯
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
author: ghogen
ms.openlocfilehash: 0552fc005a25e83065bb44e425770f9cef84f71b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082577"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="1b426-102">疑難排解：對 Windows 服務進行偵錯</span><span class="sxs-lookup"><span data-stu-id="1b426-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="1b426-103">當您對 Windows 服務應用程式進行偵錯時，您的服務會與 **Windows Service Manager** 互動。</span><span class="sxs-lookup"><span data-stu-id="1b426-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="1b426-104">**Service Manager** 會藉由呼叫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法來啟動您的服務，然後等候 30 秒以待 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法傳回。</span><span class="sxs-lookup"><span data-stu-id="1b426-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="1b426-105">如果該方法此時並未傳回，管理員就會顯示錯誤，指出無法啟動服務。</span><span class="sxs-lookup"><span data-stu-id="1b426-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="1b426-106">當您偵錯<xref:System.ServiceProcess.ServiceBase.OnStart%2A>方法中所述[How to:對 Windows 服務應用程式偵錯](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)中所述，對  方法進行偵錯時，一定會注意到這段 30 秒的期間。</span><span class="sxs-lookup"><span data-stu-id="1b426-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="1b426-107">如果您在 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法中放置中斷點，並且未在 30 秒內逐步執行它，則管理員將不會啟動服務。</span><span class="sxs-lookup"><span data-stu-id="1b426-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b426-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b426-108">See also</span></span>

- [<span data-ttu-id="1b426-109">如何：對 Windows 服務應用程式偵錯</span><span class="sxs-lookup"><span data-stu-id="1b426-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [<span data-ttu-id="1b426-110">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="1b426-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
