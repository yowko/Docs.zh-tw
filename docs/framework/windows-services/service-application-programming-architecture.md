---
title: "服務應用程式的程式設計架構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceController components, programming architecture
- ServiceBase class, service states
- Windows Service applications, code model
- services, programming architecture
- ServiceController class
- services, states
- ServiceProcessInstaller class, service application code model
- Windows Service applications, states
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
caps.latest.revision: "15"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: e9c16f2e603a3ce9bbc59be4e01aa492239d2c63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="service-application-programming-architecture"></a><span data-ttu-id="a5d7c-102">服務應用程式的程式設計架構</span><span class="sxs-lookup"><span data-stu-id="a5d7c-102">Service Application Programming Architecture</span></span>
<span data-ttu-id="a5d7c-103">Windows 服務應用程式為基礎的類別，繼承自<xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>類別。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-103">Windows Service applications are based on a class that inherits from the <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="a5d7c-104">您覆寫這個類別的方法，並定義它們，以判斷您的服務行為的功能。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-104">You override methods from this class and define functionality for them to determine how your service behaves.</span></span>  
  
 <span data-ttu-id="a5d7c-105">涉及服務建立的的主要類別如下：</span><span class="sxs-lookup"><span data-stu-id="a5d7c-105">The main classes involved in service creation are:</span></span>  
  
-   <span data-ttu-id="a5d7c-106"><xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>— 您覆寫方法<xref:System.ServiceProcess.ServiceBase>類別建立服務時，並定義程式碼以判斷如何在此服務函式繼承類別。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-106"><xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> — You override methods from the <xref:System.ServiceProcess.ServiceBase> class when creating a service and define the code to determine how your service functions in this inherited class.</span></span>  
  
-   <span data-ttu-id="a5d7c-107"><xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType>和<xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType>— 您可以使用這些類別來安裝和解除安裝您的服務。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-107"><xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType> and <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> —You use these classes to install and uninstall your service.</span></span>  
  
 <span data-ttu-id="a5d7c-108">此外，類別命名為<xref:System.ServiceProcess.ServiceController>可用來管理此服務本身。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-108">In addition, a class named <xref:System.ServiceProcess.ServiceController> can be used to manipulate the service itself.</span></span> <span data-ttu-id="a5d7c-109">這個類別並不會涉及建立服務，但可用來啟動及停止服務，傳遞命令，以及傳回一連串的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-109">This class is not involved in the creation of a service, but can be used to start and stop the service, pass commands to it, and return a series of enumerations.</span></span>  
  
## <a name="defining-your-services-behavior"></a><span data-ttu-id="a5d7c-110">定義您的服務行為</span><span class="sxs-lookup"><span data-stu-id="a5d7c-110">Defining Your Service's Behavior</span></span>  
 <span data-ttu-id="a5d7c-111">在服務類別中，您已覆寫基底類別函式，以決定服務控制管理員中變更您的服務狀態時，會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-111">In your service class, you override base class functions that determine what happens when the state of your service is changed in the Services Control Manager.</span></span> <span data-ttu-id="a5d7c-112"><xref:System.ServiceProcess.ServiceBase>類別會公開下列方法，您可以覆寫，以將自訂行為。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-112">The <xref:System.ServiceProcess.ServiceBase> class exposes the following methods, which you can override to add custom behavior.</span></span>  
  
|<span data-ttu-id="a5d7c-113">方法</span><span class="sxs-lookup"><span data-stu-id="a5d7c-113">Method</span></span>|<span data-ttu-id="a5d7c-114">若要覆寫</span><span class="sxs-lookup"><span data-stu-id="a5d7c-114">Override to</span></span>|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|<span data-ttu-id="a5d7c-115">表示當服務開始執行時，應該採取什麼動作。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-115">Indicate what actions should be taken when your service starts running.</span></span> <span data-ttu-id="a5d7c-116">您必須撰寫程式碼，在此程序，為您的服務可以執行實際工作。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-116">You must write code in this procedure for your service to perform useful work.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|<span data-ttu-id="a5d7c-117">指出暫停您的服務時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-117">Indicate what should happen when your service is paused.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|<span data-ttu-id="a5d7c-118">表示當您的服務會停止執行時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-118">Indicate what should happen when your service stops running.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|<span data-ttu-id="a5d7c-119">表示當您的服務會繼續正常運作，在暫停後要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-119">Indicate what should happen when your service resumes normal functioning after being paused.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|<span data-ttu-id="a5d7c-120">表示之前的系統關機，如果您的服務執行在該時間應該發生。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-120">Indicate what should happen just prior to your system shutting down, if your service is running at that time.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|<span data-ttu-id="a5d7c-121">表示當服務收到自訂的命令時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-121">Indicate what should happen when your service receives a custom command.</span></span> <span data-ttu-id="a5d7c-122">如需有關自訂命令的詳細資訊，請參閱 MSDN 線上。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-122">For more information on custom commands, see MSDN online.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|<span data-ttu-id="a5d7c-123">表示接收電源管理事件，例如電力偏低或暫停的作業時，服務應該如何回應。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-123">Indicate how the service should respond when a power management event is received, such as a low battery or suspended operation.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="a5d7c-124">這些方法表示服務在其存留期間，通過的狀態服務從某個狀態轉換到下一步。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-124">These methods represent states that the service moves through in its lifetime; the service transitions from one state to the next.</span></span> <span data-ttu-id="a5d7c-125">例如，將永遠不會取得服務回應<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>命令之前，先<xref:System.ServiceProcess.ServiceBase.OnStart%2A>已呼叫。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-125">For example, you will never get the service to respond to an <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> command before <xref:System.ServiceProcess.ServiceBase.OnStart%2A> has been called.</span></span>  
  
 <span data-ttu-id="a5d7c-126">有數個其他屬性和感興趣的方法。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-126">There are several other properties and methods that are of interest.</span></span> <span data-ttu-id="a5d7c-127">這些活動包括：</span><span class="sxs-lookup"><span data-stu-id="a5d7c-127">These include:</span></span>  
  
-   <span data-ttu-id="a5d7c-128"><xref:System.ServiceProcess.ServiceBase.Run%2A>方法<xref:System.ServiceProcess.ServiceBase>類別。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-128">The <xref:System.ServiceProcess.ServiceBase.Run%2A> method on the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="a5d7c-129">這是服務的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-129">This is the main entry point for the service.</span></span> <span data-ttu-id="a5d7c-130">當您建立使用 Windows 服務範本的服務時，程式碼會在您的應用程式中插入`Main`方法來執行服務。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-130">When you create a service using the Windows Service template, code is inserted in your application's `Main` method to run the service.</span></span> <span data-ttu-id="a5d7c-131">此程式碼看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="a5d7c-131">This code looks like this:</span></span>  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    >  <span data-ttu-id="a5d7c-132">這些範例會使用型別的陣列<xref:System.ServiceProcess.ServiceBase>所在可以加入您的應用程式包含每個服務，，然後所有的服務可以一起執行。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-132">These examples use an array of type <xref:System.ServiceProcess.ServiceBase>, into which each service your application contains can be added, and then all of the services can be run together.</span></span> <span data-ttu-id="a5d7c-133">如果您只會建立單一服務，不過，您可以選擇不使用的陣列，並只宣告新物件繼承自<xref:System.ServiceProcess.ServiceBase>然後加以執行。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-133">If you are only creating a single service, however, you might choose not to use the array and simply declare a new object inheriting from <xref:System.ServiceProcess.ServiceBase> and then run it.</span></span> <span data-ttu-id="a5d7c-134">如需範例，請參閱[如何： 程式設計方式撰寫服務](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-134">For an example, see [How to: Write Services Programmatically](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span></span>  
  
-   <span data-ttu-id="a5d7c-135">一系列的屬性上<xref:System.ServiceProcess.ServiceBase>類別。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-135">A series of properties on the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="a5d7c-136">這些屬性會決定哪種方法可以呼叫您的服務。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-136">These determine what methods can be called on your service.</span></span> <span data-ttu-id="a5d7c-137">例如，當<xref:System.ServiceProcess.ServiceBase.CanStop%2A>屬性設定為`true`、<xref:System.ServiceProcess.ServiceBase.OnStop%2A>可以呼叫您服務上的方法。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-137">For example, when the <xref:System.ServiceProcess.ServiceBase.CanStop%2A> property is set to `true`, the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method on your service can be called.</span></span> <span data-ttu-id="a5d7c-138">當<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>屬性設定為`true`、<xref:System.ServiceProcess.ServiceBase.OnPause%2A>和<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>可以呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-138">When the <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> property is set to `true`, the <xref:System.ServiceProcess.ServiceBase.OnPause%2A> and <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> methods can be called.</span></span> <span data-ttu-id="a5d7c-139">當您設定這些屬性，以其中一項`true`，您應該覆寫，然後定義處理相關聯的方法。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-139">When you set one of these properties to `true`, you should then override and define processing for the associated methods.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a5d7c-140">您的服務必須至少覆寫<xref:System.ServiceProcess.ServiceBase.OnStart%2A>和<xref:System.ServiceProcess.ServiceBase.OnStop%2A>才能發揮作用。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-140">Your service must override at least <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> to be useful.</span></span>  
  
 <span data-ttu-id="a5d7c-141">您也可以使用名為的元件<xref:System.ServiceProcess.ServiceController>進行通訊，並控制現有服務的行為。</span><span class="sxs-lookup"><span data-stu-id="a5d7c-141">You can also use a component called the <xref:System.ServiceProcess.ServiceController> to communicate with and control the behavior of an existing service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5d7c-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5d7c-142">See Also</span></span>  
 [<span data-ttu-id="a5d7c-143">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="a5d7c-143">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="a5d7c-144">如何： 建立 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="a5d7c-144">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
