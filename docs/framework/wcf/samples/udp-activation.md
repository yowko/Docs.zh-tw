---
title: UDP 啟用
ms.date: 03/30/2017
ms.assetid: 4b0ccd10-0dfb-4603-93f9-f0857c581cb7
ms.openlocfilehash: 9f7600bff17c015f28c3fb94ed5360561d45c65b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="udp-activation"></a><span data-ttu-id="7ba79-102">UDP 啟用</span><span class="sxs-lookup"><span data-stu-id="7ba79-102">UDP Activation</span></span>
<span data-ttu-id="7ba79-103">這個範例根據[傳輸： UDP](../../../../docs/framework/wcf/samples/transport-udp.md)範例。</span><span class="sxs-lookup"><span data-stu-id="7ba79-103">This sample is based on the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="7ba79-104">它會擴充[傳輸： UDP](../../../../docs/framework/wcf/samples/transport-udp.md)範例以支援使用 Windows Process Activation Service (WAS) 的處理序啟用。</span><span class="sxs-lookup"><span data-stu-id="7ba79-104">It extends the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample to support process activation using the Windows Process Activation Service (WAS).</span></span>  
  
 <span data-ttu-id="7ba79-105">此範例包含三個主要部分：</span><span class="sxs-lookup"><span data-stu-id="7ba79-105">The sample consists of three major pieces:</span></span>  
  
-   <span data-ttu-id="7ba79-106">UDP 通訊協定啟動程式，這是代表要啟動之應用程式接收 UDP 訊息的獨立處理序。</span><span class="sxs-lookup"><span data-stu-id="7ba79-106">A UDP Protocol Activator, a standalone process that receives UDP messages on behalf of applications that are to be activated.</span></span>  
  
-   <span data-ttu-id="7ba79-107">用戶端，會使用 UDP 自訂傳輸以傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="7ba79-107">A client that uses the UDP custom transport to send messages.</span></span>  
  
-   <span data-ttu-id="7ba79-108">服務 (在 WAS 啟動的背景工作處理序中裝載)，會透過 UDP 自訂傳輸來接收訊息。</span><span class="sxs-lookup"><span data-stu-id="7ba79-108">A service (hosted in a worker process activated by WAS) that receives messages over the UDP custom transport.</span></span>  
  
## <a name="udp-protocol-activator"></a><span data-ttu-id="7ba79-109">UDP 通訊協定啟動程式</span><span class="sxs-lookup"><span data-stu-id="7ba79-109">UDP Protocol Activator</span></span>  
 <span data-ttu-id="7ba79-110">UDP 通訊協定啟動程式是 WCF 用戶端與 WCF 服務之間的橋樑。</span><span class="sxs-lookup"><span data-stu-id="7ba79-110">The UDP Protocol Activator is a bridge between the WCF client and the WCF service.</span></span> <span data-ttu-id="7ba79-111">可提供在傳輸層中，透過 UDP 通訊協定進行資料通訊。</span><span class="sxs-lookup"><span data-stu-id="7ba79-111">It provides data communication through the UDP protocol at the transport layer.</span></span> <span data-ttu-id="7ba79-112">這個啟動程式有兩個主要功能：</span><span class="sxs-lookup"><span data-stu-id="7ba79-112">It has two major functions:</span></span>  
  
-   <span data-ttu-id="7ba79-113">WAS 接聽程式配接器 (LA)，會與 WAS 共同作業以啟動處理序，進而回應傳入訊息。</span><span class="sxs-lookup"><span data-stu-id="7ba79-113">WAS Listener Adapter (LA), which collaborates with WAS to activate processes in response to incoming messages.</span></span>  
  
-   <span data-ttu-id="7ba79-114">UDP 通訊協定接聽程式，代表要啟動的應用程式接受 UDP 訊息。</span><span class="sxs-lookup"><span data-stu-id="7ba79-114">UDP Protocol Listener, which accepts UDP messages on behalf of applications that are to be activated.</span></span>  
  
 <span data-ttu-id="7ba79-115">啟動程式必須當做伺服器電腦上的獨立程式來執行。</span><span class="sxs-lookup"><span data-stu-id="7ba79-115">The activator must be running as a standalone program on the server machine.</span></span> <span data-ttu-id="7ba79-116">一般來說，WAS 接聽程式配接器 (例如 NetTcpActivator 和 NetPipeActivator) 會在長時間執行的 Windows 服務中實作。</span><span class="sxs-lookup"><span data-stu-id="7ba79-116">Normally, WAS listener adapters (such as the NetTcpActivator and the NetPipeActivator) are implemented in long-running Windows services.</span></span> <span data-ttu-id="7ba79-117">不過，為了簡化和避免困擾，這個範例會實作通訊協定啟動程式以做為獨立應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ba79-117">However, for simplicity and clarity, this sample implements the protocol activator as a standalone application.</span></span>  
  
### <a name="was-listener-adapter"></a><span data-ttu-id="7ba79-118">WAS 接聽程式配接器</span><span class="sxs-lookup"><span data-stu-id="7ba79-118">WAS Listener Adapter</span></span>  
 <span data-ttu-id="7ba79-119">會在 `UdpListenerAdapter` 類別中實作 UDP 的 WAS 接聽程式配接器。</span><span class="sxs-lookup"><span data-stu-id="7ba79-119">The WAS Listener Adapter for UDP is implemented in the `UdpListenerAdapter` class.</span></span> <span data-ttu-id="7ba79-120">這是與 WAS 互動的模組，可對 UDP 通訊協定執行應用程式啟動。</span><span class="sxs-lookup"><span data-stu-id="7ba79-120">It is the module that interacts with WAS to perform application activation for the UDP protocol.</span></span> <span data-ttu-id="7ba79-121">呼叫下列 Webhost API 即可達到此作用：</span><span class="sxs-lookup"><span data-stu-id="7ba79-121">This is achieved by calling the following Webhost APIs:</span></span>  
  
-   `WebhostRegisterProtocol`  
  
-   `WebhostUnregisterProtocol`  
  
-   `WebhostOpenListenerChannelInstance`  
  
-   `WebhostCloseAllListenerChannelInstances`  
  
 <span data-ttu-id="7ba79-122">初始呼叫 `WebhostRegisterProtocol` 之後，接聽程式配接器會針對 applicationHost.config (位於 %windir%\system32\inetsrv) 中註冊的所有應用程式，從 WAS 中接收回呼 `ApplicationCreated`。</span><span class="sxs-lookup"><span data-stu-id="7ba79-122">After initially calling `WebhostRegisterProtocol`, the listener adapter receives the callback `ApplicationCreated` from WAS for all of the applications registered in applicationHost.config (located in %windir%\system32\inetsrv).</span></span> <span data-ttu-id="7ba79-123">在此範例中，只會處理已啟用 UDP 通訊協定 (通訊協定識別碼為 "net.udp") 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7ba79-123">In this sample, we only handle the applications with the UDP protocol (with the protocol id as "net.udp") enabled.</span></span> <span data-ttu-id="7ba79-124">如果實作回應至應用程式的動態組態變更 (例如，應用程式從已停用轉換為已啟用)，則可能會以不同的方式處理這類實作。</span><span class="sxs-lookup"><span data-stu-id="7ba79-124">Other implementations may handle this differently if such implementations respond to dynamic configuration changes to the application (for example, an application transition from disabled to enabled).</span></span>  
  
 <span data-ttu-id="7ba79-125">接收回呼 `ConfigManagerInitializationCompleted` 時，會指出 WAS 已完成初始化通訊協定的所有告知。</span><span class="sxs-lookup"><span data-stu-id="7ba79-125">When the callback `ConfigManagerInitializationCompleted` is received, it indicates that WAS has finished all of the notifications for the initialization of the protocol.</span></span> <span data-ttu-id="7ba79-126">此時，接聽程式配接器便準備處理啟動要求。</span><span class="sxs-lookup"><span data-stu-id="7ba79-126">At this time, the listener adapter is ready to process activation requests.</span></span>  
  
 <span data-ttu-id="7ba79-127">第一次有應用程式的新要求時，接聽程式配接器會在 WAS 中呼叫 `WebhostOpenListenerChannelInstance`，而若尚未啟動背景工作處理序，則 WAS 會啟動該處理序。</span><span class="sxs-lookup"><span data-stu-id="7ba79-127">When a new request comes in the first time for an application, the listener adapter calls `WebhostOpenListenerChannelInstance` into WAS, which starts the worker process if it is not started yet.</span></span> <span data-ttu-id="7ba79-128">接著會載入通訊協定處理常式，便可已啟動接聽程式配接器和虛擬應用程式之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="7ba79-128">Then the protocol handlers are loaded and the communication between the listener adapter and the virtual application can start.</span></span>  
  
 <span data-ttu-id="7ba79-129">接聽程式配接器在 %SystemRoot%\System32\inetsrv\ApplicationHost.config 中註冊 <`listenerAdapters`> 區段如下所示：</span><span class="sxs-lookup"><span data-stu-id="7ba79-129">The listener adapter is registered in the %SystemRoot%\System32\inetsrv\ApplicationHost.config in the <`listenerAdapters`> section as following:</span></span>  
  
```xml  
<add name="net.udp" identity="S-1-5-21-2127521184-1604012920-1887927527-387045" />  
```  
  
### <a name="protocol-listener"></a><span data-ttu-id="7ba79-130">通訊協定接聽程式</span><span class="sxs-lookup"><span data-stu-id="7ba79-130">Protocol Listener</span></span>  
 <span data-ttu-id="7ba79-131">UDP 通訊協定接聽程式是通訊協定啟動程式內部的模組，會代表虛擬應用程式接聽 UDP 端點。</span><span class="sxs-lookup"><span data-stu-id="7ba79-131">The UDP protocol listener is a module inside the protocol activator that listens at a UDP endpoint on behalf of the virtual application.</span></span> <span data-ttu-id="7ba79-132">會在類別 `UdpSocketListener` 中實作此項。</span><span class="sxs-lookup"><span data-stu-id="7ba79-132">It is implemented in the class `UdpSocketListener`.</span></span> <span data-ttu-id="7ba79-133">端點會表示為 `IPEndpoint`，而這是針對站台從通訊協定繫結擷取的連接埠號。</span><span class="sxs-lookup"><span data-stu-id="7ba79-133">The endpoint is represented as `IPEndpoint` for which the port number is extracted from the binding of the protocol for the site.</span></span>  
  
### <a name="control-service"></a><span data-ttu-id="7ba79-134">控制服務</span><span class="sxs-lookup"><span data-stu-id="7ba79-134">Control Service</span></span>  
 <span data-ttu-id="7ba79-135">在此範例中，我們會使用 WCF 啟動程式和 WAS 背景工作處理序之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="7ba79-135">In this sample, we use WCF to communicate between the activator and the WAS worker process.</span></span> <span data-ttu-id="7ba79-136">常駐在啟動程式中的服務稱為「控制服務」。</span><span class="sxs-lookup"><span data-stu-id="7ba79-136">The service that resides in the activator is called the Control Service.</span></span>  
  
## <a name="protocol-handlers"></a><span data-ttu-id="7ba79-137">通訊協定處理常式</span><span class="sxs-lookup"><span data-stu-id="7ba79-137">Protocol Handlers</span></span>  
 <span data-ttu-id="7ba79-138">在接聽程式配接器呼叫 `WebhostOpenListenerChannelInstance` 之後，WAS 處理序管理員就會啟動背景工作處理序 (如果尚未啟動)。</span><span class="sxs-lookup"><span data-stu-id="7ba79-138">After the listener adapter calls `WebhostOpenListenerChannelInstance`, the WAS process manager starts the worker process if it is not started.</span></span> <span data-ttu-id="7ba79-139">背景工作處理序內的應用程式管理員接著會載入 UDP 處理序通訊協定處理常式 (PPH)，以及針對該 `ListenerChannelId` 所發出的要求。</span><span class="sxs-lookup"><span data-stu-id="7ba79-139">The application manager inside the worker process then loads the UDP Process Protocol Handler (PPH) with the request for that `ListenerChannelId`.</span></span> <span data-ttu-id="7ba79-140">Pph 接著會呼叫`IAdphManager`。`StartAppDomainProtocolListenerChannel`</span><span class="sxs-lookup"><span data-stu-id="7ba79-140">The PPH in turns calls `IAdphManager`.`StartAppDomainProtocolListenerChannel`</span></span> <span data-ttu-id="7ba79-141">若要啟動 UDP AppDomain 通訊協定處理常式 (ADPH)。</span><span class="sxs-lookup"><span data-stu-id="7ba79-141">to start the UDP AppDomain Protocol Handler (ADPH).</span></span>  
  
## <a name="hostedudptransportconfiguration"></a><span data-ttu-id="7ba79-142">HostedUDPTransportConfiguration</span><span class="sxs-lookup"><span data-stu-id="7ba79-142">HostedUDPTransportConfiguration</span></span>  
 <span data-ttu-id="7ba79-143">會在 Web.config 中註冊相關資訊，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7ba79-143">The information is registered in the Web.config as follows:</span></span>  
  
```xml  
<serviceHostingEnvironment>  
<add name="net.udp" transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />  
</serviceHostingEnvironment>  
```  
  
## <a name="special-setup-for-this-sample"></a><span data-ttu-id="7ba79-144">針對本範例的特殊安裝</span><span class="sxs-lookup"><span data-stu-id="7ba79-144">Special Setup for This Sample</span></span>  
 <span data-ttu-id="7ba79-145">此範例只能在 Windows Vista、Windows Server 2008 或 Windows 7 上建立和執行。</span><span class="sxs-lookup"><span data-stu-id="7ba79-145">This sample can be only built and run on Windows Vista, Windows Server 2008, or Windows 7.</span></span> <span data-ttu-id="7ba79-146">若要執行範例，您必須先正確設定所有元件。</span><span class="sxs-lookup"><span data-stu-id="7ba79-146">To run the sample, you must first get all of the components set up correctly.</span></span> <span data-ttu-id="7ba79-147">請使用下列步驟來安裝範例。</span><span class="sxs-lookup"><span data-stu-id="7ba79-147">Use the following steps to install the sample.</span></span>  
  
#### <a name="to-set-up-this-sample"></a><span data-ttu-id="7ba79-148">若要安裝這個範例</span><span class="sxs-lookup"><span data-stu-id="7ba79-148">To set up this sample</span></span>  
  
1.  <span data-ttu-id="7ba79-149">使用下列命令安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0。</span><span class="sxs-lookup"><span data-stu-id="7ba79-149">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="7ba79-150">在 Windows Vista 上建置專案。</span><span class="sxs-lookup"><span data-stu-id="7ba79-150">Build the project on Windows Vista.</span></span> <span data-ttu-id="7ba79-151">進行編譯之後，也會在建置後階段中執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="7ba79-151">After compilation, it also performs the following operations in the post-build phase:</span></span>  
  
    -   <span data-ttu-id="7ba79-152">將 UDP 繫結安裝至「預設的網站」這個站台。</span><span class="sxs-lookup"><span data-stu-id="7ba79-152">Installs the UDP binding to the site "Default Web Site".</span></span>  
  
    -   <span data-ttu-id="7ba79-153">建立虛擬應用程式 "ServiceModelSamples" 以指向實際路徑："%SystemDrive%\inetpub\wwwroot\servicemodelsamples"。</span><span class="sxs-lookup"><span data-stu-id="7ba79-153">Creates the virtual application "ServiceModelSamples" to point to the physical path: "%SystemDrive%\inetpub\wwwroot\servicemodelsamples".</span></span>  
  
    -   <span data-ttu-id="7ba79-154">也會對此虛擬應用程式啟用 "net.udp" 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="7ba79-154">It also enables "net.udp" protocol for this virtual application.</span></span>  
  
3.  <span data-ttu-id="7ba79-155">啟動使用者介面應用程式 "WasNetActivator.exe"。</span><span class="sxs-lookup"><span data-stu-id="7ba79-155">Start the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="7ba79-156">按一下**安裝**索引標籤上，檢查下列核取方塊，然後按一下**安裝**安裝它們：</span><span class="sxs-lookup"><span data-stu-id="7ba79-156">Click the **Setup** tab, check the following check boxes and then click **Install** to install them:</span></span>  
  
    -   <span data-ttu-id="7ba79-157">UDP 接聽程式配接器</span><span class="sxs-lookup"><span data-stu-id="7ba79-157">UDP Listener Adapter</span></span>  
  
    -   <span data-ttu-id="7ba79-158">UDP 通訊協定處理常式</span><span class="sxs-lookup"><span data-stu-id="7ba79-158">UDP Protocol Handlers</span></span>  
  
4.  <span data-ttu-id="7ba79-159">按一下**啟用**的使用者介面應用程式"WasNetActivator.exe"的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7ba79-159">Click the **Activation** tab of the user interface application "WasNetActivator.exe".</span></span> <span data-ttu-id="7ba79-160">按一下**啟動**按鈕以啟動接聽程式介面卡。</span><span class="sxs-lookup"><span data-stu-id="7ba79-160">Click the **Start** button to start the listener adapter.</span></span> <span data-ttu-id="7ba79-161">您現在可以準備執行程式。</span><span class="sxs-lookup"><span data-stu-id="7ba79-161">Now you are ready to run the program.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7ba79-162">完成這個範例時，必須執行 Cleanup.bat 以移除「預設的網站」的 net.udp 繫結。</span><span class="sxs-lookup"><span data-stu-id="7ba79-162">When you are finished with this sample, you must run Cleanup.bat to remove the net.udp binding from the "Default Web Site".</span></span>  
  
## <a name="sample-usage"></a><span data-ttu-id="7ba79-163">範例用法</span><span class="sxs-lookup"><span data-stu-id="7ba79-163">Sample Usage</span></span>  
 <span data-ttu-id="7ba79-164">進行編譯之後，會產生四個不同的二進位碼檔案：</span><span class="sxs-lookup"><span data-stu-id="7ba79-164">After compilation, there are four different binaries generated:</span></span>  
  
-   <span data-ttu-id="7ba79-165">Client.exe：用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="7ba79-165">Client.exe: The client code.</span></span> <span data-ttu-id="7ba79-166">App.config 會編譯至用戶端的 Client.exe.config 組態檔。</span><span class="sxs-lookup"><span data-stu-id="7ba79-166">The App.config is compiled into the client configuration file Client.exe.config.</span></span>  
  
-   <span data-ttu-id="7ba79-167">UDPActivation.dll：包含所有主要 UDP 實作的程式庫。</span><span class="sxs-lookup"><span data-stu-id="7ba79-167">UDPActivation.dll: the library that contains all of the major UDP implementations.</span></span>  
  
-   <span data-ttu-id="7ba79-168">Service.dll：服務程式碼。</span><span class="sxs-lookup"><span data-stu-id="7ba79-168">Service.dll: The service code.</span></span> <span data-ttu-id="7ba79-169">這個檔案會複製至虛擬應用程式 ServiceModelSamples 的 \bin 目錄。</span><span class="sxs-lookup"><span data-stu-id="7ba79-169">This is copied to the \bin directory of the virtual application ServiceModelSamples.</span></span> <span data-ttu-id="7ba79-170">服務檔為 Service.svc，而組態檔為 Web.config。進行編譯之後，會將這些檔案複製至下列位置：%SystemDrive%\Inetpub\wwwroot\ServiceModelSamples。</span><span class="sxs-lookup"><span data-stu-id="7ba79-170">The service file is Service.svc and the configuration file is Web.config. After compilation, they are copied to the following location: %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples.</span></span>  
  
-   <span data-ttu-id="7ba79-171">WasNetActivator：UDP 啟動器。</span><span class="sxs-lookup"><span data-stu-id="7ba79-171">WasNetActivator: The UDP activator program.</span></span>  
  
-   <span data-ttu-id="7ba79-172">請確定已正確安裝所有必要的部分。</span><span class="sxs-lookup"><span data-stu-id="7ba79-172">Ensure that all of the required pieces are installed correctly.</span></span> <span data-ttu-id="7ba79-173">下列步驟會顯示如何執行範例：</span><span class="sxs-lookup"><span data-stu-id="7ba79-173">The following steps show how to run the sample:</span></span>  
  
1.  <span data-ttu-id="7ba79-174">請確定已啟動下列 Windows 服務：</span><span class="sxs-lookup"><span data-stu-id="7ba79-174">Ensure that the following Windows services have been started:</span></span>  
  
    -   <span data-ttu-id="7ba79-175">Windows Process Activation Service (WAS)。</span><span class="sxs-lookup"><span data-stu-id="7ba79-175">Windows Process Activation Service (WAS).</span></span>  
  
    -   <span data-ttu-id="7ba79-176">Internet Information Services (IIS)：W3SVC。</span><span class="sxs-lookup"><span data-stu-id="7ba79-176">Internet Information Services (IIS): W3SVC.</span></span>  
  
2.  <span data-ttu-id="7ba79-177">接著啟動啟動程式：WasNetActivator.exe。</span><span class="sxs-lookup"><span data-stu-id="7ba79-177">Then start the activator, WasNetActivator.exe.</span></span> <span data-ttu-id="7ba79-178">在下**啟用**索引標籤，唯一的通訊協定， **UDP**，下拉式清單中選取。</span><span class="sxs-lookup"><span data-stu-id="7ba79-178">Under the **Activation** tab, the only protocol, **UDP**, is selected in the drop down list.</span></span> <span data-ttu-id="7ba79-179">按一下**啟動**按鈕來開始啟動程式。</span><span class="sxs-lookup"><span data-stu-id="7ba79-179">Click the **Start** button to start the activator.</span></span>  
  
3.  <span data-ttu-id="7ba79-180">一旦開始執行啟動程式，就可以從命令視窗中執行 Client.exe 以執行用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="7ba79-180">Once the activator is started, you can run the client code by running Client.exe from a command window.</span></span> <span data-ttu-id="7ba79-181">下列是範例輸出：</span><span class="sxs-lookup"><span data-stu-id="7ba79-181">The following is the sample output:</span></span>  
  
    ```  
    Testing Udp Activation.  
    Start the status service.  
    Sending UDP datagrams.  
    Type a word that you want to say to the server: Hello, world!  
        Sending datagram: Hello, world![0]  
        Sending datagram: Hello, world![1]  
        Sending datagram: Hello, world![2]  
        Sending datagram: Hello, world![3]  
        Sending datagram: Hello, world![4]  
    Calling UDP duplex contract (ICalculatorContract).  
        0 + 0 = 0  
        1 + 2 = 3  
        2 + 4 = 6  
        3 + 6 = 9  
        4 + 8 = 12  
    Getting status and dump server traces:  
        Operation 'Hello' is called: Hello, world![0]  
        Operation 'Hello' is called: Hello, world![1]  
        Operation 'Hello' is called: Hello, world![2]  
        Operation 'Hello' is called: Hello, world![3]  
        Operation 'Hello' is called: Hello, world![4]  
        Operation 'Add' is called: 0 + 0  
        Operation 'Add' is called: 1 + 2  
        Operation 'Add' is called: 2 + 4  
        Operation 'Add' is called: 3 + 6  
        Operation 'Add' is called: 4 + 8  
    Press <ENTER> to complete test.  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="7ba79-182">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7ba79-182">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7ba79-183">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="7ba79-183">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7ba79-184">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="7ba79-184">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7ba79-185">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="7ba79-185">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\UdpActivation`  
  
## <a name="see-also"></a><span data-ttu-id="7ba79-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ba79-186">See Also</span></span>
