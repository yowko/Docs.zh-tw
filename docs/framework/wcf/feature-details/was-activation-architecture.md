---
title: "WAS 啟動架構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5cfbda764984305c141fd416baea8efa6aef4591
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="was-activation-architecture"></a><span data-ttu-id="dba38-102">WAS 啟動架構</span><span class="sxs-lookup"><span data-stu-id="dba38-102">WAS Activation Architecture</span></span>
<span data-ttu-id="dba38-103">本主題將條列說明並討論 Windows Process Activation Service (亦稱為 WAS) 的元件。</span><span class="sxs-lookup"><span data-stu-id="dba38-103">This topic itemizes and discusses the components of the Windows Process Activation Service (also known as WAS).</span></span>  
  
## <a name="activation-components"></a><span data-ttu-id="dba38-104">啟動元件</span><span class="sxs-lookup"><span data-stu-id="dba38-104">Activation Components</span></span>  
 <span data-ttu-id="dba38-105">WAS 包含好幾個架構元件：</span><span class="sxs-lookup"><span data-stu-id="dba38-105">WAS consists of several architectural components:</span></span>  
  
-   <span data-ttu-id="dba38-106">接聽項配接器：</span><span class="sxs-lookup"><span data-stu-id="dba38-106">Listener adapters.</span></span> <span data-ttu-id="dba38-107">Windows 服務，可在特定網路通訊協定上接收訊息，並與 WAS 通訊以將傳入訊息路由至正確的背景工作處理序。</span><span class="sxs-lookup"><span data-stu-id="dba38-107">Windows services that receive messages on specific network protocols and communicate with WAS to route incoming messages to the correct worker process.</span></span>  
  
-   <span data-ttu-id="dba38-108">WAS：</span><span class="sxs-lookup"><span data-stu-id="dba38-108">WAS.</span></span> <span data-ttu-id="dba38-109">Windows 服務，可管理背景工作處理序的建立與存留期。</span><span class="sxs-lookup"><span data-stu-id="dba38-109">The Windows service that manages the creation and lifetime of worker processes.</span></span>  
  
-   <span data-ttu-id="dba38-110">泛型背景工作處理序可執行檔 (w3wp.exe)。</span><span class="sxs-lookup"><span data-stu-id="dba38-110">The generic worker process executable (w3wp.exe).</span></span>  
  
-   <span data-ttu-id="dba38-111">應用程式管理員：</span><span class="sxs-lookup"><span data-stu-id="dba38-111">Application manager.</span></span> <span data-ttu-id="dba38-112">針對可在背景工作處理序中裝載應用程式的應用程式定義域，管理其建立與存留期。</span><span class="sxs-lookup"><span data-stu-id="dba38-112">Manages the creation and lifetime of application domains that host applications within the worker process.</span></span>  
  
-   <span data-ttu-id="dba38-113">通訊協定處理常式：</span><span class="sxs-lookup"><span data-stu-id="dba38-113">Protocol handlers.</span></span> <span data-ttu-id="dba38-114">特定於通訊協定的元件，可在背景工作處理序中執行並管理背景工作處理序與個別接聽項配接器之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="dba38-114">Protocol-specific components that run in the worker process and manage communication between the worker process and the individual listener adapters.</span></span> <span data-ttu-id="dba38-115">通訊協定處理常式共有兩種類型：處理序通訊協定處理常式和 AppDomain 通訊協定處理常式。</span><span class="sxs-lookup"><span data-stu-id="dba38-115">Two types of protocol handlers exist: process protocol handlers and AppDomain protocol handlers.</span></span>  
  
 <span data-ttu-id="dba38-116">當 WAS 啟動背景工作處理序執行個體時，會將所需的處理序通訊協定處理常式載入背景工作處理序，然後透過應用程式管理員建立可裝載應用程式的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="dba38-116">When WAS activates a worker process instance, it loads the process protocol handlers required into the worker process and uses the application manager to create an application domain to host the application.</span></span> <span data-ttu-id="dba38-117">應用程式定義域會依據應用程式需求，同時載入應用程式的程式碼與使用的 AppDomain 通訊協定處理常式。</span><span class="sxs-lookup"><span data-stu-id="dba38-117">The application domain loads the application’s code as well as the AppDomain protocol handlers that the network protocols used by the application require.</span></span>  
  
 <span data-ttu-id="dba38-118">![WAS 架構](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")</span><span class="sxs-lookup"><span data-stu-id="dba38-118">![WAS Architecture](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")</span></span>  
  
### <a name="listener-adapters"></a><span data-ttu-id="dba38-119">接聽項配接器</span><span class="sxs-lookup"><span data-stu-id="dba38-119">Listener Adapters</span></span>  
 <span data-ttu-id="dba38-120">接聽項配接器是個別的 Windows 服務，可實作網路通訊邏輯以透過所接聽的網路通訊協定來接收訊息。</span><span class="sxs-lookup"><span data-stu-id="dba38-120">Listener adapters are individual Windows services that implement the network communication logic used to receive messages using the network protocol on which they listen.</span></span> <span data-ttu-id="dba38-121">下表列出 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 通訊協定的接聽項配接器。</span><span class="sxs-lookup"><span data-stu-id="dba38-121">The following table lists the listener adapters for [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] protocols.</span></span>  
  
|<span data-ttu-id="dba38-122">接聽項配接器服務名稱</span><span class="sxs-lookup"><span data-stu-id="dba38-122">Listener adapter service name</span></span>|<span data-ttu-id="dba38-123">通訊協定</span><span class="sxs-lookup"><span data-stu-id="dba38-123">Protocol</span></span>|<span data-ttu-id="dba38-124">備註</span><span class="sxs-lookup"><span data-stu-id="dba38-124">Notes</span></span>|  
|-----------------------------------|--------------|-----------|  
|<span data-ttu-id="dba38-125">W3SVC</span><span class="sxs-lookup"><span data-stu-id="dba38-125">W3SVC</span></span>|<span data-ttu-id="dba38-126">http</span><span class="sxs-lookup"><span data-stu-id="dba38-126">http</span></span>|<span data-ttu-id="dba38-127">同時為 IIS 7.0 和 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 提供 HTTP 啟動的通用元件。</span><span class="sxs-lookup"><span data-stu-id="dba38-127">Common component that provides HTTP activation for both IIS 7.0 and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>|  
|<span data-ttu-id="dba38-128">NetTcpActivator</span><span class="sxs-lookup"><span data-stu-id="dba38-128">NetTcpActivator</span></span>|<span data-ttu-id="dba38-129">net.tcp</span><span class="sxs-lookup"><span data-stu-id="dba38-129">net.tcp</span></span>|<span data-ttu-id="dba38-130">取決於 NetTcpPortSharing 服務。</span><span class="sxs-lookup"><span data-stu-id="dba38-130">Depends on the NetTcpPortSharing service.</span></span>|  
|<span data-ttu-id="dba38-131">NetPipeActivator</span><span class="sxs-lookup"><span data-stu-id="dba38-131">NetPipeActivator</span></span>|<span data-ttu-id="dba38-132">net.pipe</span><span class="sxs-lookup"><span data-stu-id="dba38-132">net.pipe</span></span>||  
|<span data-ttu-id="dba38-133">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="dba38-133">NetMsmqActivator</span></span>|<span data-ttu-id="dba38-134">net.msmq</span><span class="sxs-lookup"><span data-stu-id="dba38-134">net.msmq</span></span>|<span data-ttu-id="dba38-135">搭配使用以 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 為基礎的訊息佇列應用程式。</span><span class="sxs-lookup"><span data-stu-id="dba38-135">For use with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-based Message Queuing applications.</span></span>|  
|<span data-ttu-id="dba38-136">NetMsmqActivator</span><span class="sxs-lookup"><span data-stu-id="dba38-136">NetMsmqActivator</span></span>|<span data-ttu-id="dba38-137">msmq.formatname</span><span class="sxs-lookup"><span data-stu-id="dba38-137">msmq.formatname</span></span>|<span data-ttu-id="dba38-138">提供與現有的訊息佇列應用程式的回溯相容性 (Backward Compatibility)。</span><span class="sxs-lookup"><span data-stu-id="dba38-138">Provides backwards compatibility with existing Message Queuing applications.</span></span>|  
  
 <span data-ttu-id="dba38-139">特定通訊協定的接聽項配接器會在安裝期間於 applicationHost.config 檔案中註冊，如下列 XML 範例所示。</span><span class="sxs-lookup"><span data-stu-id="dba38-139">Listener adapters for specific protocols are registered during installation in the applicationHost.config file, as shown in the following XML example.</span></span>  
  
```xml  
<system.applicationHost>  
    <listenerAdapters>  
        <add name="http" />  
        <add name="net.tcp"   
          identity="S-1-5-80-3579033775-2824656752-1522793541-1960352512-462907086" />  
         <add name="net.pipe"   
           identity="S-1-5-80-2943419899-937267781-4189664001-1229628381-3982115073" />  
          <add name="net.msmq"   
            identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
           <add name="msmq.formatname"   
             identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
    </listenerAdapters>  
</system.applicationHost>  
```  
  
### <a name="protocol-handlers"></a><span data-ttu-id="dba38-140">通訊協定處理常式</span><span class="sxs-lookup"><span data-stu-id="dba38-140">Protocol Handlers</span></span>  
 <span data-ttu-id="dba38-141">特定通訊協定的處理序通訊協定處理常式和 AppDomain 通訊協定處理常式會在電腦層級的 Web.config 檔案中註冊。</span><span class="sxs-lookup"><span data-stu-id="dba38-141">Process and AppDomain protocol handlers for specific protocols are registered in the machine-level Web.config file.</span></span>  
  
```xml  
<system.web>  
   <protocols>  
      <add name="net.tcp"   
        processHandlerType=  
         "System.ServiceModel.WasHosting.TcpProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.TcpAppDomainProtocolHandler"  
        validate="false" />  
      <add name="net.pipe"   
        processHandlerType=  
         "System.ServiceModel.WasHosting.NamedPipeProcessProtocolHandler"  
          appDomainHandlerType=  
           "System.ServiceModel.WasHosting.NamedPipeAppDomainProtocolHandler"/>  
      <add name="net.msmq"  
        processHandlerType=  
         "System.ServiceModel.WasHosting.MsmqProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.MsmqAppDomainProtocolHandler"  
        validate="false" />  
   </protocols>  
</system.web>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dba38-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dba38-142">See Also</span></span>  
 [<span data-ttu-id="dba38-143">設定用於 WCF 的 WAS</span><span class="sxs-lookup"><span data-stu-id="dba38-143">Configuring WAS for Use with WCF</span></span>](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [<span data-ttu-id="dba38-144">Windows Server App Fabric 裝載功能</span><span class="sxs-lookup"><span data-stu-id="dba38-144">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
