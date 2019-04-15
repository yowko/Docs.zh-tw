---
title: 作法：記錄關於服務的資訊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoLog property
- services, logging information
- Windows Service applications, logging information about
- event logs, service applications
- application event logs, service applications
- logs, service applications
ms.assetid: c0d8140f-c055-4d8e-a2e0-37358a550116
author: ghogen
ms.openlocfilehash: dfcfb7370ffd59a50cf6d0b01e84e581ddc6fc52
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306517"
---
# <a name="how-to-log-information-about-services"></a><span data-ttu-id="4675d-102">作法：記錄關於服務的資訊</span><span class="sxs-lookup"><span data-stu-id="4675d-102">How to: Log Information About Services</span></span>
<span data-ttu-id="4675d-103">根據預設，所有的 Windows 服務專案都能與應用程式事件記錄檔互動，並在其中寫入資訊和例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4675d-103">By default, all Windows Service projects have the ability to interact with the Application event log and write information and exceptions to it.</span></span> <span data-ttu-id="4675d-104">您使用 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 屬性來表示在您的應用程式中是否要這項功能。</span><span class="sxs-lookup"><span data-stu-id="4675d-104">You use the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to indicate whether you want this functionality in your application.</span></span> <span data-ttu-id="4675d-105">根據預設，會為您以 Windows 服務專案範本建立任何服務開啟記錄。</span><span class="sxs-lookup"><span data-stu-id="4675d-105">By default, logging is turned on for any service you create with the Windows Service project template.</span></span> <span data-ttu-id="4675d-106">您可以使用靜態形式的 <xref:System.Diagnostics.EventLog> 類別將服務資訊寫入記錄檔，而不需要建立 <xref:System.Diagnostics.EventLog> 元件的執行個體或手動註冊來源。</span><span class="sxs-lookup"><span data-stu-id="4675d-106">You can use a static form of the <xref:System.Diagnostics.EventLog> class to write service information to a log without having to create an instance of an <xref:System.Diagnostics.EventLog> component or manually register a source.</span></span>  
  
 <span data-ttu-id="4675d-107">您的服務安裝程式會自動在專案中註冊每個服務，做為開啟記錄功能時，服務安裝所在電腦上的應用程式記錄檔的有效事件來源。</span><span class="sxs-lookup"><span data-stu-id="4675d-107">The installer for your service automatically registers each service in your project as a valid source of events with the Application log on the computer where the service is installed, when logging is turned on.</span></span> <span data-ttu-id="4675d-108">服務會在每次服務啟動、停止、暫停、繼續、安裝或解除安裝時記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="4675d-108">The service logs information each time the service is started, stopped, paused, resumed, installed, or uninstalled.</span></span> <span data-ttu-id="4675d-109">它也會記錄發生的任何失敗。</span><span class="sxs-lookup"><span data-stu-id="4675d-109">It also logs any failures that occur.</span></span> <span data-ttu-id="4675d-110">使用預設行為時，您不需要撰寫任何程式碼，以將項目寫入記錄檔；服務會自動為您處理。</span><span class="sxs-lookup"><span data-stu-id="4675d-110">You do not need to write any code to write entries to the log when using the default behavior; the service handles this for you automatically.</span></span>  
  
 <span data-ttu-id="4675d-111">如果您想要寫入應用程式記錄檔以外的事件記錄檔，您必須將 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 屬性設為 `false`、在您的服務程式碼內建立自己的自訂事件記錄檔，然後將您的服務註冊為該記錄檔項目的有效來源。</span><span class="sxs-lookup"><span data-stu-id="4675d-111">If you want to write to an event log other than the Application log, you must set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`, create your own custom event log within your services code, and register your service as a valid source of entries for that log.</span></span> <span data-ttu-id="4675d-112">接著，您必須撰寫程式碼，每當您感興趣的動作發生時，就將項目記錄至記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4675d-112">You must then write code to record entries to the log whenever an action you're interested in occurs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4675d-113">如果您使用自訂的事件記錄檔，並設定服務應用程式寫入其中，則在您的程式碼中設定服務的 <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> 屬性之前，不得嘗試存取事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4675d-113">If you use a custom event log and configure your service application to write to it, you must not attempt to access the event log before setting the service's <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property in your code.</span></span> <span data-ttu-id="4675d-114">事件記錄檔需要此屬性的值才能將您的服務註冊為有效的事件來源。</span><span class="sxs-lookup"><span data-stu-id="4675d-114">The event log needs this property's value to register your service as a valid source of events.</span></span>  
  
### <a name="to-enable-default-event-logging-for-your-service"></a><span data-ttu-id="4675d-115">啟用服務的預設事件記錄</span><span class="sxs-lookup"><span data-stu-id="4675d-115">To enable default event logging for your service</span></span>  
  
-   <span data-ttu-id="4675d-116">將您的元件 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 屬性設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="4675d-116">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `true`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4675d-117">根據預設，這個屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="4675d-117">By default, this property is set to `true`.</span></span> <span data-ttu-id="4675d-118">您不需要明確地設定這個屬性，除非您正在建置更複雜的處理，例如評估條件，然後根據該條件的結果設定 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4675d-118">You do not need to set this explicitly unless you are building more complex processing, such as evaluating a condition and then setting the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property based on the result of that condition.</span></span>  
  
### <a name="to-disable-event-logging-for-your-service"></a><span data-ttu-id="4675d-119">停用服務的事件記錄</span><span class="sxs-lookup"><span data-stu-id="4675d-119">To disable event logging for your service</span></span>  
  
-   <span data-ttu-id="4675d-120">將您的元件 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 屬性設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="4675d-120">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property for your component to `false`.</span></span>  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a><span data-ttu-id="4675d-121">設定記錄至自訂的記錄檔</span><span class="sxs-lookup"><span data-stu-id="4675d-121">To set up logging to a custom log</span></span>  
  
1. <span data-ttu-id="4675d-122">將 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="4675d-122">Set the <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> property to `false`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4675d-123">您必須將 <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> 設為 false 以使用自訂的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4675d-123">You must set <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> to false in order to use a custom log.</span></span>  
  
2. <span data-ttu-id="4675d-124">在 Windows 服務應用程式中，設定 <xref:System.Diagnostics.EventLog> 元件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4675d-124">Set up an instance of an <xref:System.Diagnostics.EventLog> component in your Windows Service application.</span></span>  
  
3. <span data-ttu-id="4675d-125">藉由呼叫 <xref:System.Diagnostics.EventLog.CreateEventSource%2A> 方法並指定來源字串和您要建立之記錄檔的名稱，建立自訂的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4675d-125">Create a custom log by calling the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method and specifying the source string and the name of the log file you want to create.</span></span>  
  
4. <span data-ttu-id="4675d-126">將 <xref:System.Diagnostics.EventLog.Source%2A> 元件執行個體上的 <xref:System.Diagnostics.EventLog> 屬性設為您在步驟 3 中建立的來源字串。</span><span class="sxs-lookup"><span data-stu-id="4675d-126">Set the <xref:System.Diagnostics.EventLog.Source%2A> property on the <xref:System.Diagnostics.EventLog> component instance to the source string you created in step 3.</span></span>  
  
5. <span data-ttu-id="4675d-127">藉由存取 <xref:System.Diagnostics.EventLog.WriteEntry%2A> 元件執行個體上的 <xref:System.Diagnostics.EventLog> 方法，撰寫您的項目。</span><span class="sxs-lookup"><span data-stu-id="4675d-127">Write your entries by accessing the <xref:System.Diagnostics.EventLog.WriteEntry%2A> method on the <xref:System.Diagnostics.EventLog> component instance.</span></span>  
  
     <span data-ttu-id="4675d-128">下列程式碼示範如何設定記錄至自訂的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="4675d-128">The following code shows how to set up logging to a custom log.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4675d-129">在此程式碼範例中， <xref:System.Diagnostics.EventLog> 元件的執行個體命名為 `eventLog1` (在 Visual Basic 中為`EventLog1` )。</span><span class="sxs-lookup"><span data-stu-id="4675d-129">In this code example, an instance of an <xref:System.Diagnostics.EventLog> component is named `eventLog1` (`EventLog1` in Visual Basic).</span></span> <span data-ttu-id="4675d-130">如果您在步驟 2 中以另一個名稱建立執行個體，請跟著變更程式碼。</span><span class="sxs-lookup"><span data-stu-id="4675d-130">If you created an instance with another name in step 2, change the code accordingly.</span></span>  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="4675d-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4675d-131">See also</span></span>

- [<span data-ttu-id="4675d-132">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="4675d-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
