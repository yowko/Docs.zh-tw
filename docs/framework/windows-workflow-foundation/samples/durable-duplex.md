---
title: "永久性雙工"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1298f150709b48f18de654be2ab17adfdcbf42a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="durable-duplex"></a><span data-ttu-id="d8129-102">永久性雙工</span><span class="sxs-lookup"><span data-stu-id="d8129-102">Durable Duplex</span></span>
<span data-ttu-id="d8129-103">這個範例示範如何透過 [!INCLUDE[wf](../../../../includes/wf-md.md)] 的訊息活動來設定永久性的雙工訊息交換。</span><span class="sxs-lookup"><span data-stu-id="d8129-103">This sample demonstrates how to set up and configure durable duplex message exchange using the messaging activities in [!INCLUDE[wf](../../../../includes/wf-md.md)].</span></span> <span data-ttu-id="d8129-104">永久性的雙工訊息交換是長時間進行的雙向訊息交換。</span><span class="sxs-lookup"><span data-stu-id="d8129-104">A durable duplex message exchange is a two-way message exchange that takes place over a long period of time.</span></span> <span data-ttu-id="d8129-105">此訊息交換的存留期間可能比通訊通道的存留期間以及服務執行個體的記憶體中存留期間還要長。</span><span class="sxs-lookup"><span data-stu-id="d8129-105">The lifetime of the message exchange may be longer than the lifetime of the communication channel and the in-memory lifetime of the service instances.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="d8129-106">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="d8129-106">Sample Details</span></span>  
 <span data-ttu-id="d8129-107">在這個範例中，設定兩個透過 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 實作的 [!INCLUDE[wf2](../../../../includes/wf2-md.md)] 服務，來進行永久性的雙工訊息交換。</span><span class="sxs-lookup"><span data-stu-id="d8129-107">In this sample, two [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services implemented using [!INCLUDE[wf2](../../../../includes/wf2-md.md)] are configured to have a durable duplex message exchange.</span></span> <span data-ttu-id="d8129-108">永久性雙工訊息交換由兩個單向訊息透過 MSMQ 傳送並使用相互關聯[.NET Context Exchange](http://go.microsoft.com/fwlink/?LinkID=166059)。</span><span class="sxs-lookup"><span data-stu-id="d8129-108">The durable duplex message exchange is composed from two one-way messages sent over MSMQ and correlated using [.NET Context Exchange](http://go.microsoft.com/fwlink/?LinkID=166059).</span></span> <span data-ttu-id="d8129-109">訊息是使用 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.Receive> 訊息活動來傳送。</span><span class="sxs-lookup"><span data-stu-id="d8129-109">The messages are sent using the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.Receive> messaging activities.</span></span> <span data-ttu-id="d8129-110">.NET Context Exchange 用來在傳送的訊息上指定回呼位址。</span><span class="sxs-lookup"><span data-stu-id="d8129-110">.NET Context Exchange is use to specify the callback address on the sent messages.</span></span> <span data-ttu-id="d8129-111">兩個服務是透過使用 Windows Process Activation Services (WAS) 所主控，並設定為啟用服務執行個體的持續性。</span><span class="sxs-lookup"><span data-stu-id="d8129-111">Both services are hosted using Windows Process Activation Services (WAS) and are configured to enable persistence of the services instances.</span></span>  
  
 <span data-ttu-id="d8129-112">第一個服務 (Service1.xamlx) 會傳送要求給傳送服務 (Service2.xamlx)，使其做些工作。</span><span class="sxs-lookup"><span data-stu-id="d8129-112">The first service (Service1.xamlx) sends a request to the send service (Service2.xamlx) to do some work.</span></span> <span data-ttu-id="d8129-113">一旦工作完成，Service2.xamlx 會傳回通知給 Service1.xamlx，表示工作已完成。</span><span class="sxs-lookup"><span data-stu-id="d8129-113">Once the work is completed, Service2.xamlx sends a notification back to Service1.xamlx to indicate that the work has been completed.</span></span> <span data-ttu-id="d8129-114">工作流程主控台應用程式會設定這些服務接聽的佇列，並傳送初始開始訊息以啟動 Service1.xamlx。</span><span class="sxs-lookup"><span data-stu-id="d8129-114">A workflow console application sets up the queues that the services are listening on and sends the initial Start message to activate Service1.xamlx.</span></span> <span data-ttu-id="d8129-115">一旦 Service1.xamlx 從 Service2.xamlx 收到所要求工作已完成的通知，Service1.xamlx 會將結果儲存至 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="d8129-115">Once Service1.xamlx receives the notification from Service2.xamlx that the requested work has been completed, Service1.xamlx saves the result to an XML file.</span></span> <span data-ttu-id="d8129-116">在等候回呼訊息時，Service1.xamlx 會使用預設 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> 保存其執行個體狀態。</span><span class="sxs-lookup"><span data-stu-id="d8129-116">While waiting for the callback message, Service1.xamlx persists its instance state using the default <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>.</span></span> <span data-ttu-id="d8129-117">Service2.xamlx 會在完成 Service1.xamlx 所要求工作的過程中保存其執行個體狀態。</span><span class="sxs-lookup"><span data-stu-id="d8129-117">Service2.xamlx persists its instance state as part of completing the work requested by Service1.xamlx.</span></span>  
  
 <span data-ttu-id="d8129-118">若要設定服務以透過 MSMQ 使用 .NET Context Exchange，這兩個服務應設定為使用包含 <xref:System.ServiceModel.Channels.ContextBindingElement> 和 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement> 的自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="d8129-118">To configure the services to use .NET Context Exchange over MSMQ, both services are configured to use a custom binding that consists of the <xref:System.ServiceModel.Channels.ContextBindingElement> and the <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>.</span></span> <span data-ttu-id="d8129-119">回呼位址是以 <xref:System.ServiceModel.Channels.ContextBindingElement> 來指定，包含在所有透過自訂繫結傳送之訊息的回呼內容標頭中。</span><span class="sxs-lookup"><span data-stu-id="d8129-119">A callback address is specified with the <xref:System.ServiceModel.Channels.ContextBindingElement> and is included in a callback context header with all messages sent using a custom binding.</span></span> <span data-ttu-id="d8129-120">下列程式碼範例定義此自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="d8129-120">The following code example defines the custom binding.</span></span>  
  
```xml  
<configuration>  
     <system.serviceModel>  
          …  
          <bindings>  
               <customBinding>  
                    <binding name="netMsmqContextBinding">  
                         <context clientCallbackAddress="net.msmq://localhost/private/DurableDuplex/Service1.xamlx"/>  
                         <msmqTransport exactlyOnce="False">  
                              <msmqTransportSecurity msmqAuthenticationMode="None" msmqProtectionLevel="None"/>  
                         </msmqTransport>  
                    </binding>  
               </customBinding>  
          </bindings>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="d8129-121">這個範例所使用的繫結並不安全。</span><span class="sxs-lookup"><span data-stu-id="d8129-121">The binding used by this sample is not secure.</span></span> <span data-ttu-id="d8129-122">當您部署應用程式時，應該根據應用程式的安全性需求來設定繫結。</span><span class="sxs-lookup"><span data-stu-id="d8129-122">When deploying your application you should configure your binding based on the security requirements of your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8129-123">這個範例所使用的佇列不是異動式。</span><span class="sxs-lookup"><span data-stu-id="d8129-123">The queues used in this sample are not transactional.</span></span> <span data-ttu-id="d8129-124">如需範例，示範如何設定[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]訊息交換使用交易佇列中，請參閱[MSMQ 啟用](../../../../docs/framework/wcf/samples/msmq-activation.md)範例。</span><span class="sxs-lookup"><span data-stu-id="d8129-124">For a sample that shows how to set up [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] message exchanges using transaction queues, see the [MSMQ Activation](../../../../docs/framework/wcf/samples/msmq-activation.md) sample.</span></span>  
  
 <span data-ttu-id="d8129-125">由 Service1.xamlx 傳送至 Service2.xamlx 的訊息是透過設定有 Service2.xamlx 位址和先前定義之自訂繫結的用戶端端點所傳送。</span><span class="sxs-lookup"><span data-stu-id="d8129-125">The message sent by Service1.xamlx to Service2.xamlx is sent using a client endpoint configured with the address of Service2.xamlx and the custom binding defined previously.</span></span> <span data-ttu-id="d8129-126">從 Service2.xamlx 到 Service1.xamlx 的回呼是透過不含明確設定之位址的用戶端端點所傳送，因為位址是取自 Service1.xamlx 所傳送的回呼內容。</span><span class="sxs-lookup"><span data-stu-id="d8129-126">The callback from Service2.xamlx to Service1.xamlx is sent using a client endpoint with no explicitly configured address because the address is taken from the callback context sent by Service1.xamlx.</span></span> <span data-ttu-id="d8129-127">下列程式碼範例定義用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="d8129-127">The following code example defines the client endpoints.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
     <system.serviceModel>  
          …  
          <client>  
               <endpoint address="net.msmq://localhost/private/DurableDuplex/Service2.xamlx" binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="IDoWork"/>  
               <endpoint binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="INotify"/>  
          </client>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="d8129-128">下列程式碼範例將 net.msmq 基底位址的預設通訊協定對應變更為使用此自訂繫結，藉以公開使用此自訂繫結的端點。</span><span class="sxs-lookup"><span data-stu-id="d8129-128">The following code example exposes endpoints using this custom binding by changing the default protocol mapping for net.msmq base addresses to use this custom binding.</span></span>  
  
```xml  
<configuration>  
     <system.serviceModel>  
          <protocolMapping>  
               <add scheme="net.msmq" binding="customBinding" bindingConfiguration="netMsmqContextBinding"/>  
          </protocolMapping>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="d8129-129">下列程式碼範例將 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 行為加入至兩個服務，並指定持續性資料庫的連接字串，藉以啟用兩個服務的持續性。</span><span class="sxs-lookup"><span data-stu-id="d8129-129">The following code example enables persistence for both services by adding the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior to both services and specifying the connection string for the persistence database.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
    <system.serviceModel>  
          …  
          <behaviors>  
               <serviceBehaviors>  
                    <behavior>  
                         <serviceDebug includeExceptionDetailInFaults="True"/>  
                         <serviceMetadata httpGetEnabled="True"/>  
                         <sqlWorkflowInstanceStore connectionString="Data Source=.\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True"/>  
                    </behavior>  
               </serviceBehaviors>  
          </behaviors>  
     </system.serviceModel>  
</configuration>  
```  
  
## <a name="system-requirements"></a><span data-ttu-id="d8129-130">系統需求</span><span class="sxs-lookup"><span data-stu-id="d8129-130">System Requirements</span></span>  
 <span data-ttu-id="d8129-131">本範例需要下列元件。</span><span class="sxs-lookup"><span data-stu-id="d8129-131">This sample requires the following components.</span></span>  
  
1.  <span data-ttu-id="d8129-132">Internet Information Services。</span><span class="sxs-lookup"><span data-stu-id="d8129-132">Internet Information Services.</span></span>  
  
2.  <span data-ttu-id="d8129-133">Internet Information Services -> IIS 6.0 管理相容性 -> IIS Metabase 及 IIS 6.0 設定相容性。</span><span class="sxs-lookup"><span data-stu-id="d8129-133">Internet Information Services -> IIS 6.0 Management Compatibility -> IIS Metabase and IIS 6.0 configuration compatibility.</span></span>  
  
3.  <span data-ttu-id="d8129-134">全球資訊網服務 -> 應用程式開發功能 -> ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="d8129-134">World Wide Web Services -> Application Development Features -> ASP.NET.</span></span>  
  
4.  <span data-ttu-id="d8129-135">Microsoft Message Queues (MSMQ) 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d8129-135">Microsoft Message Queues (MSMQ) Server.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="d8129-136">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="d8129-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="d8129-137">設定持續性資料庫和結果目錄。</span><span class="sxs-lookup"><span data-stu-id="d8129-137">Set up the persistence database and the results directory.</span></span>  
  
    1.  <span data-ttu-id="d8129-138">開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="d8129-138">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="d8129-139">巡覽至這個範例的資料夾，並執行 Setup.cmd。</span><span class="sxs-lookup"><span data-stu-id="d8129-139">Navigate to the folder for this sample and run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="d8129-140">設定虛擬應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8129-140">Set up the virtual application.</span></span>  
  
    1.  <span data-ttu-id="d8129-141">從 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元，執行下列命令註冊 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="d8129-141">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, register ASP.NET by running the following command.</span></span>  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  <span data-ttu-id="d8129-142">執行[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]以管理員權限，以滑鼠右鍵按一下[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="d8129-142">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator permissions by right-clicking [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and selecting **Run as administrator**.</span></span>  
  
    3.  <span data-ttu-id="d8129-143">使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 DurableDuplex.sln 檔案。</span><span class="sxs-lookup"><span data-stu-id="d8129-143">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DurableDuplex.sln file.</span></span>  
  
3.  <span data-ttu-id="d8129-144">設定服務佇列。</span><span class="sxs-lookup"><span data-stu-id="d8129-144">Set up the service queues.</span></span>  
  
    1.  <span data-ttu-id="d8129-145">若要執行 DurableDuplex 用戶端，按下 F5。</span><span class="sxs-lookup"><span data-stu-id="d8129-145">To run the DurableDuplex client, press F5.</span></span>  
  
    2.  <span data-ttu-id="d8129-146">開啟**電腦管理**主控台執行`Compmgmt.msc`從命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="d8129-146">Open the **Computer Management** console by running `Compmgmt.msc` from a command prompt.</span></span>  
  
    3.  <span data-ttu-id="d8129-147">展開**服務和應用程式**，**訊息佇列**。</span><span class="sxs-lookup"><span data-stu-id="d8129-147">Expand **Service and Applications**, **Message Queuing**.</span></span> <span data-ttu-id="d8129-148">**私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="d8129-148">**Private Queues**.</span></span>  
  
    4.  <span data-ttu-id="d8129-149">以滑鼠右鍵按一下 durableduplex/service1.xamlx 和 durableduplex/service2.xamlx 佇列，並選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="d8129-149">Right-click the durableduplex/service1.xamlx and durableduplex/service2.xamlx queues and select **Properties**.</span></span>  
  
    5.  <span data-ttu-id="d8129-150">選取**安全性**索引標籤上，並允許**Everyone 接收訊息**，**查看訊息**和**傳送訊息**這兩個佇列的權限。</span><span class="sxs-lookup"><span data-stu-id="d8129-150">Select the **Security** tab and allow **Everyone Receive Message**, **Peek Message** and **Send Message** permissions for both queues.</span></span>  
  
    6.  <span data-ttu-id="d8129-151">開啟 Internet Information Services (IIS) 管理員。</span><span class="sxs-lookup"><span data-stu-id="d8129-151">Open Internet Information Services (IIS) Manager.</span></span>  
  
    7.  <span data-ttu-id="d8129-152">瀏覽至**伺服器**，**網站**， **Default Web site**，**私人**，**永久性雙工**選取**進階選項**。</span><span class="sxs-lookup"><span data-stu-id="d8129-152">Browse to **Server**, **Sites**, **Default Web site**, **private**, **Durable Duplex** and select **Advanced Options**.</span></span>  
  
    8.  <span data-ttu-id="d8129-153">變更**啟用的通訊協定**至**http，net.msmq**。</span><span class="sxs-lookup"><span data-stu-id="d8129-153">Change the **Enabled Protocols** to **http,net.msmq**.</span></span>  
  
4.  <span data-ttu-id="d8129-154">執行範例。</span><span class="sxs-lookup"><span data-stu-id="d8129-154">Run the sample.</span></span>  
  
    1.  <span data-ttu-id="d8129-155">瀏覽至 http://localhost/private/durableduplex/service1.xamlx 和 http://localhost/private/durableduplex/service2.xamlx，以確保兩個服務執行中。</span><span class="sxs-lookup"><span data-stu-id="d8129-155">Browse to http://localhost/private/durableduplex/service1.xamlx and http://localhost/private/durableduplex/service2.xamlx to ensure that both services are running.</span></span>  
  
    2.  <span data-ttu-id="d8129-156">按下 F5，執行 DurableDuplexClient。</span><span class="sxs-lookup"><span data-stu-id="d8129-156">Press F5 to run DurableDuplexClient.</span></span>  
  
         <span data-ttu-id="d8129-157">當永久性雙工訊息交換完成時，result.xml 檔案會儲存至 C:\Inbox 資料夾，這個檔案包含訊息交換結果。</span><span class="sxs-lookup"><span data-stu-id="d8129-157">When the durable duplex message exchange completes a result.xml file is saved to the C:\Inbox folder and contains the result of the message exchange.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="d8129-158">若要清除 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="d8129-158">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="d8129-159">執行 Cleanup.cmd。</span><span class="sxs-lookup"><span data-stu-id="d8129-159">Run Cleanup.cmd.</span></span>  
  
    1.  <span data-ttu-id="d8129-160">開啟 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="d8129-160">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="d8129-161">巡覽至這個範例的資料夾，並執行 Cleanup.cmd。</span><span class="sxs-lookup"><span data-stu-id="d8129-161">Navigate to the folder for this sample and run Cleanup.cmd.</span></span>  
  
2.  <span data-ttu-id="d8129-162">移除服務的虛擬應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8129-162">Remove the virtual application for the services.</span></span>  
  
    1.  <span data-ttu-id="d8129-163">開啟 網際網路資訊服務 (IIS) 管理員執行`Inetmgr.exe`從命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="d8129-163">Open the Internet Information Services (IIS) Manager by running `Inetmgr.exe` from a command prompt.</span></span>  
  
    2.  <span data-ttu-id="d8129-164">瀏覽至預設的網站，並移除**私人**虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="d8129-164">Browse to the default Web site and remove the **private** virtual directory.</span></span>  
  
3.  <span data-ttu-id="d8129-165">移除此範例中設定的佇列。</span><span class="sxs-lookup"><span data-stu-id="d8129-165">Remove the queues set up for this sample.</span></span>  
  
    1.  <span data-ttu-id="d8129-166">開啟 [電腦管理] 主控台執行`Compmgmt.msc`從命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="d8129-166">Open the Computer Management console by running `Compmgmt.msc` from a command prompt.</span></span>  
  
    2.  <span data-ttu-id="d8129-167">展開**服務和應用程式**，**訊息佇列**，**私用佇列**。</span><span class="sxs-lookup"><span data-stu-id="d8129-167">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
    3.  <span data-ttu-id="d8129-168">刪除 durableduplex/service1.xamlx 和 durableduplex/service2.xamlx 佇列。</span><span class="sxs-lookup"><span data-stu-id="d8129-168">Delete the durableduplex/service1.xamlx and durableduplex/service2.xamlx queues.</span></span>  
  
4.  <span data-ttu-id="d8129-169">移除 C:\Inbox 目錄。</span><span class="sxs-lookup"><span data-stu-id="d8129-169">Remove the C:\Inbox directory.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d8129-170">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="d8129-170">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d8129-171">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="d8129-171">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d8129-172">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="d8129-172">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d8129-173">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="d8129-173">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`