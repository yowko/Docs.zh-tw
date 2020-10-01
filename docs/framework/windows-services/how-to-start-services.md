---
title: 作法：啟動服務
description: 瞭解幾種啟動服務的方式。 安裝服務之後，必須加以啟動。 開始呼叫服務類別上的 OnStart 方法。
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
ms.openlocfilehash: 1ca597379ab2a8fdae19fcfc5351c29d716753dc
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608409"
---
# <a name="how-to-start-services"></a><span data-ttu-id="26ffb-105">作法：啟動服務</span><span class="sxs-lookup"><span data-stu-id="26ffb-105">How to: Start Services</span></span>

<span data-ttu-id="26ffb-106">安裝服務之後，必須加以啟動。</span><span class="sxs-lookup"><span data-stu-id="26ffb-106">After a service is installed, it must be started.</span></span> <span data-ttu-id="26ffb-107">從呼叫服務類別上的 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法開始。</span><span class="sxs-lookup"><span data-stu-id="26ffb-107">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="26ffb-108">通常，<xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法會定義服務將執行的有用工作。</span><span class="sxs-lookup"><span data-stu-id="26ffb-108">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="26ffb-109">服務啟動之後，即會保持作用中，直到您以手動方式暫停或停止它為止。</span><span class="sxs-lookup"><span data-stu-id="26ffb-109">After a service starts, it remains active until it is manually paused or stopped.</span></span>

<span data-ttu-id="26ffb-110">服務可以設定為自動或手動啟動。</span><span class="sxs-lookup"><span data-stu-id="26ffb-110">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="26ffb-111">自動啟動的服務將在其安裝所在的電腦重新開機或第一次開啟時啟動。</span><span class="sxs-lookup"><span data-stu-id="26ffb-111">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="26ffb-112">使用者必須啟動以手動方式啟動的服務。</span><span class="sxs-lookup"><span data-stu-id="26ffb-112">A user must start a service that starts manually.</span></span>

> [!NOTE]
> <span data-ttu-id="26ffb-113">根據預設，使用 Visual Studio 建立的服務均會設定為以手動方式啟動。</span><span class="sxs-lookup"><span data-stu-id="26ffb-113">By default, services created with Visual Studio are set to start manually.</span></span>

<span data-ttu-id="26ffb-114">有數種方式可讓您以手動方法啟動服務：從 [伺服器總管]\*\*\*\*、從 [服務控制管理員]\*\*\*\*，或從程式碼使用稱為 <xref:System.ServiceProcess.ServiceController> 的元件。</span><span class="sxs-lookup"><span data-stu-id="26ffb-114">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>

<span data-ttu-id="26ffb-115">您會設定 <xref:System.ServiceProcess.ServiceInstaller> 類別上的 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 屬性，以決定服務應手動或自動啟動。</span><span class="sxs-lookup"><span data-stu-id="26ffb-115">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>

### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="26ffb-116">指定啟動服務的方式</span><span class="sxs-lookup"><span data-stu-id="26ffb-116">To specify how a service should start</span></span>

1. <span data-ttu-id="26ffb-117">建立服務之後，為其加入必要的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="26ffb-117">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="26ffb-118">如需詳細資訊，請參閱[如何：將安裝程式加入服務應用程式](how-to-add-installers-to-your-service-application.md)。</span><span class="sxs-lookup"><span data-stu-id="26ffb-118">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>

2. <span data-ttu-id="26ffb-119">在設計工具中，按一下所要使用服務的服務安裝程式。</span><span class="sxs-lookup"><span data-stu-id="26ffb-119">In the designer, click the service installer for the service you are working with.</span></span>

3. <span data-ttu-id="26ffb-120">在 [屬性]\*\*\*\* 視窗中，將 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 屬性設定為下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="26ffb-120">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>

    |<span data-ttu-id="26ffb-121">若要安裝服務</span><span class="sxs-lookup"><span data-stu-id="26ffb-121">To have your service install</span></span>|<span data-ttu-id="26ffb-122">設定此值</span><span class="sxs-lookup"><span data-stu-id="26ffb-122">Set this value</span></span>|
    |----------------------------------|--------------------|
    |<span data-ttu-id="26ffb-123">當電腦重新開機時</span><span class="sxs-lookup"><span data-stu-id="26ffb-123">When the computer is restarted</span></span>|<span data-ttu-id="26ffb-124">**自動**</span><span class="sxs-lookup"><span data-stu-id="26ffb-124">**Automatic**</span></span>|
    |<span data-ttu-id="26ffb-125">當明確的使用者動作啟動服務時</span><span class="sxs-lookup"><span data-stu-id="26ffb-125">When an explicit user action starts the service</span></span>|<span data-ttu-id="26ffb-126">**手動**</span><span class="sxs-lookup"><span data-stu-id="26ffb-126">**Manual**</span></span>|

    > [!TIP]
    > <span data-ttu-id="26ffb-127">若不要讓服務啟動，可以將 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 屬性設定為 **Disabled**。</span><span class="sxs-lookup"><span data-stu-id="26ffb-127">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="26ffb-128">如果您要將伺服器重新開機多次，而且想要防止要正常啟動的服務被啟動，藉以節省時間，則可以這樣做。</span><span class="sxs-lookup"><span data-stu-id="26ffb-128">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>

    > [!NOTE]
    > <span data-ttu-id="26ffb-129">您可以在安裝服務之後變更這些屬性和其他屬性。</span><span class="sxs-lookup"><span data-stu-id="26ffb-129">These and other properties can be changed after your service is installed.</span></span>

    <span data-ttu-id="26ffb-130">有數種方式可讓您啟動要將其 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 處理序設定為 **Manual** 的服務：從 [伺服器總管]\*\*\*\*、從 [Windows 服務控制管理員]\*\*\*\* 或從程式碼。</span><span class="sxs-lookup"><span data-stu-id="26ffb-130">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="26ffb-131">請務必注意，並非所有的這些方法都會在**服務控制管理員**的內容中實際啟動服務；**伺服器總管**和以程式設計方式啟動服務的方法會實際操作該控制程式。</span><span class="sxs-lookup"><span data-stu-id="26ffb-131">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>

### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="26ffb-132">以手動方式從伺服器總管啟動服務</span><span class="sxs-lookup"><span data-stu-id="26ffb-132">To manually start a service from Server Explorer</span></span>

1. <span data-ttu-id="26ffb-133">在 [伺服器總管]\*\*\*\* 中，加入您所需的伺服器 (如果尚未列出該伺服器)。</span><span class="sxs-lookup"><span data-stu-id="26ffb-133">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="26ffb-134">如需詳細資訊，請參閱＜如何：存取及初始化伺服器總管/資料庫總管＞。</span><span class="sxs-lookup"><span data-stu-id="26ffb-134">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>

2. <span data-ttu-id="26ffb-135">展開 [服務]\*\*\*\* 節點，然後找出您想要啟動的服務。</span><span class="sxs-lookup"><span data-stu-id="26ffb-135">Expand the **Services** node, and then locate the service you want to start.</span></span>

3. <span data-ttu-id="26ffb-136">在服務名稱上按一下滑鼠右鍵，然後按一下 [啟動]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="26ffb-136">Right-click the name of the service, and click **Start**.</span></span>

### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="26ffb-137">以手動方式從服務控制管理員啟動服務</span><span class="sxs-lookup"><span data-stu-id="26ffb-137">To manually start a service from Services Control Manager</span></span>

1. <span data-ttu-id="26ffb-138">執行下列其中一個動作來開啟 [服務控制管理員]\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="26ffb-138">Open the **Services Control Manager** by doing one of the following:</span></span>

    - <span data-ttu-id="26ffb-139">在 Windows XP 和 2000 Professional 中，以滑鼠右鍵按一下桌面上的 [我的電腦]\*\*\*\*，然後按一下 [管理]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="26ffb-139">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="26ffb-140">在出現的對話方塊中，展開 [服務與應用程式]\*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="26ffb-140">In the dialog box that appears, expand the **Services and Applications** node.</span></span>

      <span data-ttu-id="26ffb-141">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="26ffb-141">\- or -</span></span>

    - <span data-ttu-id="26ffb-142">在 Windows Server 2003 和 Windows 2000 Server 中，按一下 [啟動]\*\*\*\*、指向 [程式集]\*\*\*\*、按一下 [系統管理工具]\*\*\*\*，然後按一下 [服務]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="26ffb-142">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="26ffb-143">在 Windows NT 4.0 版中，您可以從 [控制台]\*\*\*\* 開啟此對話方塊。</span><span class="sxs-lookup"><span data-stu-id="26ffb-143">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>

    <span data-ttu-id="26ffb-144">現在您應該會看到服務列於這個視窗的 [服務]\*\*\*\* 區段中。</span><span class="sxs-lookup"><span data-stu-id="26ffb-144">You should now see your service listed in the **Services** section of the window.</span></span>

2. <span data-ttu-id="26ffb-145">從清單中選取您的服務，以滑鼠右鍵按一下該服務，然後按一下 [啟動]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="26ffb-145">Select your service in the list, right-click it, and then click **Start**.</span></span>

### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="26ffb-146">以手動方式從程式碼啟動服務</span><span class="sxs-lookup"><span data-stu-id="26ffb-146">To manually start a service from code</span></span>

1. <span data-ttu-id="26ffb-147">建立 <xref:System.ServiceProcess.ServiceController> 類別的執行個體，並將它設定為與您想要管理的服務互動。</span><span class="sxs-lookup"><span data-stu-id="26ffb-147">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>

2. <span data-ttu-id="26ffb-148">呼叫 <xref:System.ServiceProcess.ServiceController.Start%2A> 方法啟動服務。</span><span class="sxs-lookup"><span data-stu-id="26ffb-148">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="26ffb-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26ffb-149">See also</span></span>

- [<span data-ttu-id="26ffb-150">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="26ffb-150">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="26ffb-151">作法：建立 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="26ffb-151">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="26ffb-152">作法：將安裝程式新增至服務應用程式</span><span class="sxs-lookup"><span data-stu-id="26ffb-152">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
