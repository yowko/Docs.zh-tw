---
title: 服務應用程式的程式設計架構
ms.date: 03/30/2017
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
author: ghogen
ms.openlocfilehash: df969a634c84a7bccb048542cb768c920203e423
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599284"
---
# <a name="service-application-programming-architecture"></a><span data-ttu-id="3fc72-102">服務應用程式的程式設計架構</span><span class="sxs-lookup"><span data-stu-id="3fc72-102">Service Application Programming Architecture</span></span>
<span data-ttu-id="3fc72-103">Windows 服務應用程式會以繼承自 <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> 類別的類別為基礎。</span><span class="sxs-lookup"><span data-stu-id="3fc72-103">Windows Service applications are based on a class that inherits from the <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="3fc72-104">您會覆寫來自這個類別的方法，並定義適用於它們的功能以決定服務的行為方式。</span><span class="sxs-lookup"><span data-stu-id="3fc72-104">You override methods from this class and define functionality for them to determine how your service behaves.</span></span>  
  
 <span data-ttu-id="3fc72-105">以下是涉及服務建立的主要類別：</span><span class="sxs-lookup"><span data-stu-id="3fc72-105">The main classes involved in service creation are:</span></span>  
  
- <span data-ttu-id="3fc72-106"><xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>：您會在建立服務並定義程式碼以決定服務如何在此繼承類別中運作時，覆寫來自 <xref:System.ServiceProcess.ServiceBase> 類別的方法。</span><span class="sxs-lookup"><span data-stu-id="3fc72-106"><xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> — You override methods from the <xref:System.ServiceProcess.ServiceBase> class when creating a service and define the code to determine how your service functions in this inherited class.</span></span>  
  
- <span data-ttu-id="3fc72-107"><xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType> 和 <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType>：您會使用這些類別來安裝和解除安裝服務。</span><span class="sxs-lookup"><span data-stu-id="3fc72-107"><xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType> and <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> —You use these classes to install and uninstall your service.</span></span>  
  
 <span data-ttu-id="3fc72-108">此外，名為 <xref:System.ServiceProcess.ServiceController> 的類別可用來操作服務本身。</span><span class="sxs-lookup"><span data-stu-id="3fc72-108">In addition, a class named <xref:System.ServiceProcess.ServiceController> can be used to manipulate the service itself.</span></span> <span data-ttu-id="3fc72-109">這個類別並未涉及服務的建立，但可用來啟動和停止服務、將命令傳遞到其中，以及傳回一連串的列舉。</span><span class="sxs-lookup"><span data-stu-id="3fc72-109">This class is not involved in the creation of a service, but can be used to start and stop the service, pass commands to it, and return a series of enumerations.</span></span>  
  
## <a name="defining-your-services-behavior"></a><span data-ttu-id="3fc72-110">定義服務行為</span><span class="sxs-lookup"><span data-stu-id="3fc72-110">Defining Your Service's Behavior</span></span>  
 <span data-ttu-id="3fc72-111">在服務類別中，您會覆寫基底類別函式，以決定在服務控制管理員中變更服務狀態時會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="3fc72-111">In your service class, you override base class functions that determine what happens when the state of your service is changed in the Services Control Manager.</span></span> <span data-ttu-id="3fc72-112"><xref:System.ServiceProcess.ServiceBase> 類別會公開下列方法，您可以覆寫這些方法以加入自訂行為。</span><span class="sxs-lookup"><span data-stu-id="3fc72-112">The <xref:System.ServiceProcess.ServiceBase> class exposes the following methods, which you can override to add custom behavior.</span></span>  
  
|<span data-ttu-id="3fc72-113">方法</span><span class="sxs-lookup"><span data-stu-id="3fc72-113">Method</span></span>|<span data-ttu-id="3fc72-114">覆寫到</span><span class="sxs-lookup"><span data-stu-id="3fc72-114">Override to</span></span>|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|<span data-ttu-id="3fc72-115">表示當服務開始執行時應該採取的動作。</span><span class="sxs-lookup"><span data-stu-id="3fc72-115">Indicate what actions should be taken when your service starts running.</span></span> <span data-ttu-id="3fc72-116">您必須在此程序中為服務撰寫程式碼以執行有用的工作。</span><span class="sxs-lookup"><span data-stu-id="3fc72-116">You must write code in this procedure for your service to perform useful work.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|<span data-ttu-id="3fc72-117">表示服務暫停時應該會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="3fc72-117">Indicate what should happen when your service is paused.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|<span data-ttu-id="3fc72-118">表示服務停止執行時應該會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="3fc72-118">Indicate what should happen when your service stops running.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|<span data-ttu-id="3fc72-119">表示當服務在暫停之後繼續正常運作時應該會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="3fc72-119">Indicate what should happen when your service resumes normal functioning after being paused.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|<span data-ttu-id="3fc72-120">表示如果服務在系統關機時正在執行，則在系統關機之前應該會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="3fc72-120">Indicate what should happen just prior to your system shutting down, if your service is running at that time.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|<span data-ttu-id="3fc72-121">表示當服務接收到自訂命令時應該會發生什麼事。</span><span class="sxs-lookup"><span data-stu-id="3fc72-121">Indicate what should happen when your service receives a custom command.</span></span> <span data-ttu-id="3fc72-122">如需自訂命令的詳細資訊，請參閱 MSDN Online。</span><span class="sxs-lookup"><span data-stu-id="3fc72-122">For more information on custom commands, see MSDN online.</span></span>|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|<span data-ttu-id="3fc72-123">表示在接收到電源管理事件 (例如電力偏低或暫停作業) 時服務應如何回應。</span><span class="sxs-lookup"><span data-stu-id="3fc72-123">Indicate how the service should respond when a power management event is received, such as a low battery or suspended operation.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="3fc72-124">這些方法表示服務在其存留期間行進的狀態；服務會從某個狀態轉換到下一個狀態。</span><span class="sxs-lookup"><span data-stu-id="3fc72-124">These methods represent states that the service moves through in its lifetime; the service transitions from one state to the next.</span></span> <span data-ttu-id="3fc72-125">例如，您絕對不會讓服務在呼叫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 之前回應 <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> 命令。</span><span class="sxs-lookup"><span data-stu-id="3fc72-125">For example, you will never get the service to respond to an <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> command before <xref:System.ServiceProcess.ServiceBase.OnStart%2A> has been called.</span></span>  
  
 <span data-ttu-id="3fc72-126">還有其他數個感興趣的屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="3fc72-126">There are several other properties and methods that are of interest.</span></span> <span data-ttu-id="3fc72-127">它們包括：</span><span class="sxs-lookup"><span data-stu-id="3fc72-127">These include:</span></span>  
  
- <span data-ttu-id="3fc72-128"><xref:System.ServiceProcess.ServiceBase> 類別上的 <xref:System.ServiceProcess.ServiceBase.Run%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="3fc72-128">The <xref:System.ServiceProcess.ServiceBase.Run%2A> method on the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="3fc72-129">這是服務的主要進入點。</span><span class="sxs-lookup"><span data-stu-id="3fc72-129">This is the main entry point for the service.</span></span> <span data-ttu-id="3fc72-130">當您使用 Windows 服務範本建立服務時，會將程式碼插入應用程式的 `Main` 方法來執行服務。</span><span class="sxs-lookup"><span data-stu-id="3fc72-130">When you create a service using the Windows Service template, code is inserted in your application's `Main` method to run the service.</span></span> <span data-ttu-id="3fc72-131">此程式碼如下所示：</span><span class="sxs-lookup"><span data-stu-id="3fc72-131">This code looks like this:</span></span>  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    >  <span data-ttu-id="3fc72-132">這些範例會使用 <xref:System.ServiceProcess.ServiceBase> 類型的陣列，應用程式所包含的每個服務均可加入到此陣列，接著可一起執行所有服務。</span><span class="sxs-lookup"><span data-stu-id="3fc72-132">These examples use an array of type <xref:System.ServiceProcess.ServiceBase>, into which each service your application contains can be added, and then all of the services can be run together.</span></span> <span data-ttu-id="3fc72-133">不過，如果您只建立單一服務，則可以選擇不使用陣列，而只宣告繼承自 <xref:System.ServiceProcess.ServiceBase> 的新物件，然後加以執行。</span><span class="sxs-lookup"><span data-stu-id="3fc72-133">If you are only creating a single service, however, you might choose not to use the array and simply declare a new object inheriting from <xref:System.ServiceProcess.ServiceBase> and then run it.</span></span> <span data-ttu-id="3fc72-134">如需範例，請參閱[如何：以程式設計方式撰寫服務](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="3fc72-134">For an example, see [How to: Write Services Programmatically](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span></span>  
  
- <span data-ttu-id="3fc72-135"><xref:System.ServiceProcess.ServiceBase> 類別上的一系列屬性。</span><span class="sxs-lookup"><span data-stu-id="3fc72-135">A series of properties on the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="3fc72-136">這些屬性會決定可在您的服務上呼叫哪些方法。</span><span class="sxs-lookup"><span data-stu-id="3fc72-136">These determine what methods can be called on your service.</span></span> <span data-ttu-id="3fc72-137">例如，將 <xref:System.ServiceProcess.ServiceBase.CanStop%2A> 屬性設定為 `true` 時，可以呼叫服務上的 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="3fc72-137">For example, when the <xref:System.ServiceProcess.ServiceBase.CanStop%2A> property is set to `true`, the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method on your service can be called.</span></span> <span data-ttu-id="3fc72-138">將 <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> 屬性設定為 `true` 時，可以呼叫 <xref:System.ServiceProcess.ServiceBase.OnPause%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="3fc72-138">When the <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> property is set to `true`, the <xref:System.ServiceProcess.ServiceBase.OnPause%2A> and <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> methods can be called.</span></span> <span data-ttu-id="3fc72-139">當您將這其中一個屬性設定為 `true` 時，接著應該覆寫並定義適用於相關聯方法的處理。</span><span class="sxs-lookup"><span data-stu-id="3fc72-139">When you set one of these properties to `true`, you should then override and define processing for the associated methods.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3fc72-140">您的服務至少必須覆寫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnStop%2A>，才能發揮作用。</span><span class="sxs-lookup"><span data-stu-id="3fc72-140">Your service must override at least <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> to be useful.</span></span>  
  
 <span data-ttu-id="3fc72-141">您也可以使用名為 <xref:System.ServiceProcess.ServiceController> 的元件進行通訊，並控制現有服務的行為。</span><span class="sxs-lookup"><span data-stu-id="3fc72-141">You can also use a component called the <xref:System.ServiceProcess.ServiceController> to communicate with and control the behavior of an existing service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fc72-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fc72-142">See also</span></span>

- [<span data-ttu-id="3fc72-143">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="3fc72-143">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="3fc72-144">如何：建立 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="3fc72-144">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
