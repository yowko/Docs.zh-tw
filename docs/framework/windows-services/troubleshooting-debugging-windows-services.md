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
ms.openlocfilehash: 0dbbebd14ce0ff5f69a12c256238c7e0a02494cb
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47199940"
---
# <a name="troubleshooting-debugging-windows-services"></a><span data-ttu-id="4aec4-102">疑難排解：對 Windows 服務進行偵錯</span><span class="sxs-lookup"><span data-stu-id="4aec4-102">Troubleshooting: Debugging Windows Services</span></span>
<span data-ttu-id="4aec4-103">當您對 Windows 服務應用程式進行偵錯時，您的服務會與 **Windows Service Manager** 互動。</span><span class="sxs-lookup"><span data-stu-id="4aec4-103">When you debug a Windows service application, your service and the **Windows Service Manager** interact.</span></span> <span data-ttu-id="4aec4-104">**Service Manager** 會藉由呼叫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法來啟動您的服務，然後等候 30 秒以待 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法傳回。</span><span class="sxs-lookup"><span data-stu-id="4aec4-104">The **Service Manager** starts your service by calling the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and then waits 30 seconds for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method to return.</span></span> <span data-ttu-id="4aec4-105">如果該方法此時並未傳回，管理員就會顯示錯誤，指出無法啟動服務。</span><span class="sxs-lookup"><span data-stu-id="4aec4-105">If the method does not return in this time, the manager shows an error that the service cannot be started.</span></span>  
  
 <span data-ttu-id="4aec4-106">當您以[如何：偵錯 Windows 服務應用程式](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)中所述方式來對 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法進行偵錯時，一定會注意到這段 30 秒的期間。</span><span class="sxs-lookup"><span data-stu-id="4aec4-106">When you debug the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method as described in [How to: Debug Windows Service Applications](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md), you must be aware of this 30-second period.</span></span> <span data-ttu-id="4aec4-107">如果您在 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法中放置中斷點，並且未在 30 秒內逐步執行它，則管理員將不會啟動服務。</span><span class="sxs-lookup"><span data-stu-id="4aec4-107">If you place a breakpoint in the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method and do not step through it in 30 seconds, the manager will not start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aec4-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="4aec4-108">See Also</span></span>  
 [<span data-ttu-id="4aec4-109">如何：偵錯 Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="4aec4-109">How to: Debug Windows Service Applications</span></span>](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [<span data-ttu-id="4aec4-110">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="4aec4-110">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
