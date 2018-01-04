---
title: "如何：啟動服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 8352edaa9386adc1fbf3057c6e98f5a9cf9ce4a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-start-services"></a><span data-ttu-id="0c9e6-102">如何：啟動服務</span><span class="sxs-lookup"><span data-stu-id="0c9e6-102">How to: Start Services</span></span>
<span data-ttu-id="0c9e6-103">安裝服務之後，它必須啟動。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-103">After a service is installed, it must be started.</span></span> <span data-ttu-id="0c9e6-104">開始呼叫<xref:System.ServiceProcess.ServiceBase.OnStart%2A>服務類別上的方法。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-104">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="0c9e6-105">通常，<xref:System.ServiceProcess.ServiceBase.OnStart%2A>方法來定義服務將會執行實際工作。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-105">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="0c9e6-106">服務啟動之後，它會保持有效，直到以手動方式暫停或停止。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-106">After a service starts, it remains active until it is manually paused or stopped.</span></span>  
  
 <span data-ttu-id="0c9e6-107">服務可以設定要自動或手動啟動。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-107">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="0c9e6-108">安裝所在的電腦已重新開機，或第一次開啟時，將會啟動時自動啟動服務。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-108">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="0c9e6-109">使用者必須啟動服務，以手動方式啟動。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-109">A user must start a service that starts manually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c9e6-110">根據預設，服務則是以建立[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]設定為手動啟動。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-110">By default, services created with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] are set to start manually.</span></span>  
  
 <span data-ttu-id="0c9e6-111">有數種方式，您可以手動啟動服務，從**伺服器總管**，從**服務控制管理員**，或從程式碼使用的元件呼叫<xref:System.ServiceProcess.ServiceController>。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-111">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>  
  
 <span data-ttu-id="0c9e6-112">您設定<xref:System.ServiceProcess.ServiceInstaller.StartType%2A>屬性<xref:System.ServiceProcess.ServiceInstaller>類別以決定服務是否應該在手動或自動啟動。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-112">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>  
  
### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="0c9e6-113">若要指定服務應該啟動的方式</span><span class="sxs-lookup"><span data-stu-id="0c9e6-113">To specify how a service should start</span></span>  
  
1.  <span data-ttu-id="0c9e6-114">建立您的服務之後, 加入必要的安裝它。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="0c9e6-115">如需詳細資訊，請參閱[如何： 加入至您的服務應用程式的安裝程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2.  <span data-ttu-id="0c9e6-116">在設計工具中，按一下您要使用服務的服務安裝程式。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-116">In the designer, click the service installer for the service you are working with.</span></span>  
  
3.  <span data-ttu-id="0c9e6-117">在**屬性**視窗中，將<xref:System.ServiceProcess.ServiceInstaller.StartType%2A>屬性，以下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="0c9e6-117">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>  
  
    |<span data-ttu-id="0c9e6-118">若要讓安裝程式服務</span><span class="sxs-lookup"><span data-stu-id="0c9e6-118">To have your service install</span></span>|<span data-ttu-id="0c9e6-119">將此值設定</span><span class="sxs-lookup"><span data-stu-id="0c9e6-119">Set this value</span></span>|  
    |----------------------------------|--------------------|  
    |<span data-ttu-id="0c9e6-120">重新啟動電腦</span><span class="sxs-lookup"><span data-stu-id="0c9e6-120">When the computer is restarted</span></span>|<span data-ttu-id="0c9e6-121">**自動**</span><span class="sxs-lookup"><span data-stu-id="0c9e6-121">**Automatic**</span></span>|  
    |<span data-ttu-id="0c9e6-122">當明確的使用者動作啟動服務</span><span class="sxs-lookup"><span data-stu-id="0c9e6-122">When an explicit user action starts the service</span></span>|<span data-ttu-id="0c9e6-123">**手動**</span><span class="sxs-lookup"><span data-stu-id="0c9e6-123">**Manual**</span></span>|  
  
    > [!TIP]
    >  <span data-ttu-id="0c9e6-124">若要避免您的服務所完全啟動，您可以設定<xref:System.ServiceProcess.ServiceInstaller.StartType%2A>屬性**已停用**。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-124">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="0c9e6-125">如果您要將伺服器重新開機多次，而且想要節省時間而導致無法正常啟動正在啟動服務，您可以這樣做。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-125">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0c9e6-126">之後安裝您的服務，可以變更這些屬性和其他屬性。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-126">These and other properties can be changed after your service is installed.</span></span>  
  
     <span data-ttu-id="0c9e6-127">有數種方式，您可以啟動的服務具有其<xref:System.ServiceProcess.ServiceInstaller.StartType%2A>程序設定為**手動**— 從**伺服器總管**，從**Windows 服務控制管理員**，或從程式碼。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-127">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="0c9e6-128">請務必注意所有這些方法實際上的內容中啟動服務**服務控制管理員**;**伺服器總管**和以程式設計方式啟動服務的實際管理控制站。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-128">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="0c9e6-129">若要從 [伺服器總管] 中手動啟動服務</span><span class="sxs-lookup"><span data-stu-id="0c9e6-129">To manually start a service from Server Explorer</span></span>  
  
1.  <span data-ttu-id="0c9e6-130">在**伺服器總管**，新增您想如果未列出的伺服器。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-130">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="0c9e6-131">如需詳細資訊，請參閱 < 如何： 存取及初始化伺服器總管資料庫總管。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-131">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
2.  <span data-ttu-id="0c9e6-132">展開**服務** 節點，然後找出您想要啟動的服務。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-132">Expand the **Services** node, and then locate the service you want to start.</span></span>  
  
3.  <span data-ttu-id="0c9e6-133">以滑鼠右鍵按一下服務名稱，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-133">Right-click the name of the service, and click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="0c9e6-134">若要手動啟動服務從服務控制管理員</span><span class="sxs-lookup"><span data-stu-id="0c9e6-134">To manually start a service from Services Control Manager</span></span>  
  
1.  <span data-ttu-id="0c9e6-135">開啟**服務控制管理員**由下列其中一項動作：</span><span class="sxs-lookup"><span data-stu-id="0c9e6-135">Open the **Services Control Manager** by doing one of the following:</span></span>  
  
    -   <span data-ttu-id="0c9e6-136">在 Windows XP 和 2000 Professional，以滑鼠右鍵按一下**我的電腦**桌面，然後按一下**管理**。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-136">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="0c9e6-137">在出現的對話方塊中，依序展開**服務和應用程式**節點。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-137">In the dialog box that appears, expand the **Services and Applications** node.</span></span>  
  
         <span data-ttu-id="0c9e6-138">\-或-</span><span class="sxs-lookup"><span data-stu-id="0c9e6-138">\- or -</span></span>  
  
    -   <span data-ttu-id="0c9e6-139">在 Windows Server 2003 和 Windows 2000 Server 中，按一下 **啟動**，指向 **程式**，按一下**系統管理工具**，然後按一下 **服務**.</span><span class="sxs-lookup"><span data-stu-id="0c9e6-139">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="0c9e6-140">在 Windows NT 4.0 版，您可以開啟此對話方塊中，從**控制台**。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-140">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>  
  
     <span data-ttu-id="0c9e6-141">您現在應該會看到您的服務中所列**服務**視窗的區段。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-141">You should now see your service listed in the **Services** section of the window.</span></span>  
  
2.  <span data-ttu-id="0c9e6-142">清單中選取您的服務，以滑鼠右鍵按一下，然後按**啟動**。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-142">Select your service in the list, right-click it, and then click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="0c9e6-143">若要從程式碼中手動啟動服務</span><span class="sxs-lookup"><span data-stu-id="0c9e6-143">To manually start a service from code</span></span>  
  
1.  <span data-ttu-id="0c9e6-144">建立的執行個體<xref:System.ServiceProcess.ServiceController>類別，並將它設定為與您想要管理的服務互動。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-144">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>  
  
2.  <span data-ttu-id="0c9e6-145">呼叫 <xref:System.ServiceProcess.ServiceController.Start%2A> 方法啟動服務。</span><span class="sxs-lookup"><span data-stu-id="0c9e6-145">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c9e6-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="0c9e6-146">See Also</span></span>  
 [<span data-ttu-id="0c9e6-147">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="0c9e6-147">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="0c9e6-148">如何：建立 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="0c9e6-148">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="0c9e6-149">如何：將 Installer 新增至服務應用程式</span><span class="sxs-lookup"><span data-stu-id="0c9e6-149">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
