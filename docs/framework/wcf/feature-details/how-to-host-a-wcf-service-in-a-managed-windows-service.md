---
title: "HOW TO：在 Managed Windows 服務中裝載 WCF 服務"
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
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 01f6ce27a05c11ddf4662609bf98730df5ddfda3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a><span data-ttu-id="42592-102">HOW TO：在 Managed Windows 服務中裝載 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="42592-102">How to: Host a WCF Service in a Managed Windows Service</span></span>
<span data-ttu-id="42592-103">本主題概要說明建立可由 Windows 服務裝載的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務時，必要的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="42592-103">This topic outlines the basic steps required to create a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service that is hosted by a Windows Service.</span></span> <span data-ttu-id="42592-104">此案例是由 Managed Windows 服務裝載選項所啟用，就是在非訊息啟動的安全環境中由網際網路資訊服務 (IIS) 外部所裝載的長期執行之 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="42592-104">The scenario is enabled by the managed Windows service hosting option that is a long-running [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted outside of Internet Information Services (IIS) in a secure environment that is not message activated.</span></span> <span data-ttu-id="42592-105">服務的存留期會改由作業系統來控制。</span><span class="sxs-lookup"><span data-stu-id="42592-105">The lifetime of the service is controlled instead by the operating system.</span></span> <span data-ttu-id="42592-106">所有 Windows 版本都提供這個裝載選項。</span><span class="sxs-lookup"><span data-stu-id="42592-106">This hosting option is available in all versions of Windows.</span></span>  
  
 <span data-ttu-id="42592-107">Windows 服務可以透過 Microsoft Management Console (MMC) 中的 Microsoft.ManagementConsole.SnapIn 嵌入式管理單元進行管理，並設定成系統啟動時自動啟動。</span><span class="sxs-lookup"><span data-stu-id="42592-107">Windows services can be managed with the Microsoft.ManagementConsole.SnapIn in Microsoft Management Console (MMC) and can be configured to start up automatically when the system boots up.</span></span> <span data-ttu-id="42592-108">這個裝載選項包含可將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務裝載為 Managed Windows 服務的註冊應用程式定義域 (AppDomain)，如此一來便可透過 Windows 服務的服務控制管理員 (SCM) 來控制服務的處理序存留期。</span><span class="sxs-lookup"><span data-stu-id="42592-108">This hosting option consists of registering the application domain (AppDomain) that hosts a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service as a managed Windows service so that the process lifetime of the service is controlled by the Service Control Manager (SCM) for Windows services.</span></span>  
  
 <span data-ttu-id="42592-109">服務程式碼包含服務合約的服務實作、Windows 服務類別以及安裝程式類別。</span><span class="sxs-lookup"><span data-stu-id="42592-109">The service code includes a service implementation of the service contract, a Windows Service class, and an installer class.</span></span> <span data-ttu-id="42592-110">服務實作類別 `CalculatorService` 是一項 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="42592-110">The service implementation class, `CalculatorService`, is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="42592-111">`CalculatorWindowsService` 是一項 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="42592-111">The `CalculatorWindowsService` is a Windows service.</span></span> <span data-ttu-id="42592-112">為了限定為 Windows 服務，此類別會繼承自 `ServiceBase`，並且實作 `OnStart` 和 `OnStop` 方法。</span><span class="sxs-lookup"><span data-stu-id="42592-112">To qualify as a Windows service, the class inherits from `ServiceBase` and implements the `OnStart` and `OnStop` methods.</span></span> <span data-ttu-id="42592-113">在 `OnStart` 中，會為 <xref:System.ServiceModel.ServiceHost> 型別建立並開啟 `CalculatorService`。</span><span class="sxs-lookup"><span data-stu-id="42592-113">In `OnStart`, a <xref:System.ServiceModel.ServiceHost> is created for the `CalculatorService` type and opened.</span></span> <span data-ttu-id="42592-114">使用 `OnStop` 時，則會停止與處置服務。</span><span class="sxs-lookup"><span data-stu-id="42592-114">In `OnStop`, the service is stopped and disposed.</span></span> <span data-ttu-id="42592-115">主機也會負責提供服務主機的基底位址，該位址必須設定在應用程式設定中。</span><span class="sxs-lookup"><span data-stu-id="42592-115">The host is also responsible for providing a base address to the service host, which has been configured in application settings.</span></span> <span data-ttu-id="42592-116">繼承自 <xref:System.Configuration.Install.Installer> 的安裝程式類別，會允許 Installutil.exe 工具將程式當做 Windows 服務進行安裝。</span><span class="sxs-lookup"><span data-stu-id="42592-116">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as a Windows service by the Installutil.exe tool.</span></span>  
  
### <a name="construct-the-service-and-provide-the-hosting-code"></a><span data-ttu-id="42592-117">建構服務並提供裝載程式碼</span><span class="sxs-lookup"><span data-stu-id="42592-117">Construct the service and provide the hosting code</span></span>  
  
1.  <span data-ttu-id="42592-118">建立新的 Visual Studio 主控台應用程式專案，名為 "Service"。</span><span class="sxs-lookup"><span data-stu-id="42592-118">Create a new Visual Studio Console Application project called "Service".</span></span>  
  
2.  <span data-ttu-id="42592-119">將 Program.cs 重新命名為 Service.cs。</span><span class="sxs-lookup"><span data-stu-id="42592-119">Rename Program.cs to Service.cs.</span></span>  
  
3.  <span data-ttu-id="42592-120">將命名空間變更為 Microsoft.ServiceModel.Samples。</span><span class="sxs-lookup"><span data-stu-id="42592-120">Change the namespace to Microsoft.ServiceModel.Samples.</span></span>  
  
4.  <span data-ttu-id="42592-121">加入下列組件的參考。</span><span class="sxs-lookup"><span data-stu-id="42592-121">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="42592-122">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="42592-122">System.ServiceModel.dll</span></span>  
  
    -   <span data-ttu-id="42592-123">System.ServiceProcess.dll</span><span class="sxs-lookup"><span data-stu-id="42592-123">System.ServiceProcess.dll</span></span>  
  
    -   <span data-ttu-id="42592-124">System.Configuration.Install.dll</span><span class="sxs-lookup"><span data-stu-id="42592-124">System.Configuration.Install.dll</span></span>  
  
5.  <span data-ttu-id="42592-125">使用陳述式將下列內容加入至 Service.cs。</span><span class="sxs-lookup"><span data-stu-id="42592-125">Add the following using statements to Service.cs.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]  
  
6.  <span data-ttu-id="42592-126">定義 `ICalculator` 服務合約，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="42592-126">Define the `ICalculator` service contract as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]  
  
7.  <span data-ttu-id="42592-127">在 `CalculatorService` 類別中實作服務合約，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="42592-127">Implement the service contract in a class called `CalculatorService` as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]  
  
8.  <span data-ttu-id="42592-128">建立繼承自 `CalculatorWindowsService` 類別的新類別，名為 <xref:System.ServiceProcess.ServiceBase>。</span><span class="sxs-lookup"><span data-stu-id="42592-128">Create a new class called `CalculatorWindowsService` that inherits from the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="42592-129">加入名為 `serviceHost` 的區域變數，以參考 <xref:System.ServiceModel.ServiceHost> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="42592-129">Add a local variable called `serviceHost` to reference the <xref:System.ServiceModel.ServiceHost> instance.</span></span> <span data-ttu-id="42592-130">定義 `Main` 方法來呼叫 `ServiceBase.Run(new CalculatorWindowsService)`。</span><span class="sxs-lookup"><span data-stu-id="42592-130">Define the `Main` method that calls `ServiceBase.Run(new CalculatorWindowsService)`</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]  
  
9. <span data-ttu-id="42592-131">建立並開啟新的 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 執行個體，以覆寫 <xref:System.ServiceModel.ServiceHost> 方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="42592-131">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> method by creating and opening a new <xref:System.ServiceModel.ServiceHost> instance as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]  
  
10. <span data-ttu-id="42592-132">覆寫用來關閉 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 的 <xref:System.ServiceModel.ServiceHost> 方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="42592-132">Override the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method closing the <xref:System.ServiceModel.ServiceHost> as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]  
  
11. <span data-ttu-id="42592-133">建立繼承自 `ProjectInstaller` 且其 <xref:System.Configuration.Install.Installer> 標記設為 <xref:System.ComponentModel.RunInstallerAttribute> 的新類別，名為 `true`。</span><span class="sxs-lookup"><span data-stu-id="42592-133">Create a new class called `ProjectInstaller` that inherits from <xref:System.Configuration.Install.Installer> and that is marked with the <xref:System.ComponentModel.RunInstallerAttribute> set to `true`.</span></span> <span data-ttu-id="42592-134">這樣 Installutil.exe 工具就能安裝此 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="42592-134">This allows the Windows service to be installed by the Installutil.exe tool.</span></span>  
  
     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]  
  
12. <span data-ttu-id="42592-135">移除您在建立專案時所產生的 `Service` 類別。</span><span class="sxs-lookup"><span data-stu-id="42592-135">Remove the `Service` class that was generated when you created the project.</span></span>  
  
13. <span data-ttu-id="42592-136">將應用程式組態檔加入至專案。</span><span class="sxs-lookup"><span data-stu-id="42592-136">Add an application configuration file to the project.</span></span> <span data-ttu-id="42592-137">以下列組態 XML 取代該檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="42592-137">Replace the contents of the file with the following configuration XML.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>    <services>  
          <!-- This section is optional with the new configuration model  
               introduced in .NET Framework 4. -->  
          <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                   behaviorConfiguration="CalculatorServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
            <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->  
            <endpoint address=""  
                      binding="wsHttpBinding"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->  
            <endpoint address="mex"  
                      binding="mexHttpBinding"  
                      contract="IMetadataExchange" />  
          </service>  
        </services>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="CalculatorServiceBehavior">  
              <serviceMetadata httpGetEnabled="true"/>  
              <serviceDebug includeExceptionDetailInFaults="False"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="42592-138">以滑鼠右鍵按一下 App.config 檔案中的**方案總管 中**選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="42592-138">Right click the App.config file in the **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="42592-139">在下**複製到輸出目錄**選取**更新時才複製**。</span><span class="sxs-lookup"><span data-stu-id="42592-139">Under **Copy to Output Directory** select **Copy if Newer**.</span></span>  
  
     <span data-ttu-id="42592-140">此範例會在組態檔中明確地指定端點。</span><span class="sxs-lookup"><span data-stu-id="42592-140">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="42592-141">如果您沒有將任何端點加入至服務中，執行階段會為您加入預設端點。</span><span class="sxs-lookup"><span data-stu-id="42592-141">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="42592-142">在這個範例中，由於服務將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 設定為 `true`，表示您的服務也已啟用中繼資料發行。</span><span class="sxs-lookup"><span data-stu-id="42592-142">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, your service also has publishing metadata enabled.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="42592-143">預設端點、 繫結和行為，請參閱[簡化的組態](../../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="42592-143"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
### <a name="install-and-run-the-service"></a><span data-ttu-id="42592-144">安裝並執行服務</span><span class="sxs-lookup"><span data-stu-id="42592-144">Install and run the service</span></span>  
  
1.  <span data-ttu-id="42592-145">建置方案以建立 `Service.exe` 可執行檔。</span><span class="sxs-lookup"><span data-stu-id="42592-145">Build the solution to create the `Service.exe` executable.</span></span>  
  
2.  <span data-ttu-id="42592-146">開啟 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元，巡覽至專案目錄。</span><span class="sxs-lookup"><span data-stu-id="42592-146">Open the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt and navigate to the project directory.</span></span> <span data-ttu-id="42592-147">在命令提示字元中輸入 `installutil bin\service.exe` 以安裝 Windows 服務 </span><span class="sxs-lookup"><span data-stu-id="42592-147">Type `installutil bin\service.exe` at the command prompt to install the Windows service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="42592-148">如果您不是使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元，請確認 `%WinDir%\Microsoft.NET\Framework\v4.0.<current version>` 目錄位於系統路徑。</span><span class="sxs-lookup"><span data-stu-id="42592-148">If you do not use the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt, make sure that the `%WinDir%\Microsoft.NET\Framework\v4.0.<current version>` directory is in the system path.</span></span>  
  
     <span data-ttu-id="42592-149">在命令提示字元中輸入 `services.msc` 以存取服務控制管理員 (SCM)。</span><span class="sxs-lookup"><span data-stu-id="42592-149">Type `services.msc` at the command prompt to access the Service Control Manager (SCM).</span></span> <span data-ttu-id="42592-150">Windows 服務應該會在 [服務] 中顯示為 "WCFWindowsServiceSample"。</span><span class="sxs-lookup"><span data-stu-id="42592-150">The Windows service should appear in Services as "WCFWindowsServiceSample".</span></span> <span data-ttu-id="42592-151">只有當 Windows 服務正在執行的情況下，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務才會回應用戶端。</span><span class="sxs-lookup"><span data-stu-id="42592-151">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service can only respond to clients if the Windows service is running.</span></span> <span data-ttu-id="42592-152">若要啟動服務，以滑鼠右鍵按一下它的 SCM 和 [啟動]，選取或類型**net 啟動 WCFWindowsServiceSample**在命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="42592-152">To start the service, right-click it in the SCM and select "Start", or type **net start WCFWindowsServiceSample** at the command prompt.</span></span>  
  
3.  <span data-ttu-id="42592-153">若要變更服務，必須先加以停止並解除安裝。</span><span class="sxs-lookup"><span data-stu-id="42592-153">If you make changes to the service, you must first stop it and uninstall it.</span></span> <span data-ttu-id="42592-154">若要停止服務，以滑鼠右鍵按一下 SCM 中的服務並選取 [停止] 或**輸入 net stop WCFWindowsServiceSample**在命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="42592-154">To stop the service, right-click the service in the SCM and select "Stop", or **type net stop WCFWindowsServiceSample** at the command prompt.</span></span> <span data-ttu-id="42592-155">請注意，如果您在停止 Windows 服務後執行用戶端，則當用戶端嘗試存取此服務時將會發生 <xref:System.ServiceModel.EndpointNotFoundException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="42592-155">Note that if you stop the Windows service and then run a client, an <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="42592-156">若要解除安裝 Windows 服務類型**installutil /u bin\service.exe**在命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="42592-156">To uninstall the Windows service type **installutil /u bin\service.exe** at the command prompt.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42592-157">範例</span><span class="sxs-lookup"><span data-stu-id="42592-157">Example</span></span>  
 <span data-ttu-id="42592-158">以下是這個主題使用過的程式碼完整清單。</span><span class="sxs-lookup"><span data-stu-id="42592-158">The following is a complete listing of the code used by this topic.</span></span>  
  
 [!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
 [!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]  
  
 <span data-ttu-id="42592-159">就像「自我裝載」選項一樣，Windows 服務裝載環境要求將某些裝載程式碼撰寫成應用程式的一部分。</span><span class="sxs-lookup"><span data-stu-id="42592-159">Like the "Self-Hosting" option, the Windows service hosting environment requires that some hosting code be written as part of the application.</span></span> <span data-ttu-id="42592-160">服務會實作成為主控台應用程式並包含專屬的裝載程式碼。</span><span class="sxs-lookup"><span data-stu-id="42592-160">The service is implemented as a console application and contains its own hosting code.</span></span> <span data-ttu-id="42592-161">在其他裝載環境中，例如 Internet Information Services (IIS) 所裝載的 Windows 處理序啟用服務 (WAS)，開發人員就不需要撰寫裝載程式碼。</span><span class="sxs-lookup"><span data-stu-id="42592-161">In other hosting environments, such as Windows Process Activation Service (WAS) hosting in Internet Information Services (IIS), it is not necessary for developers to write hosting code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42592-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42592-162">See Also</span></span>  
 [<span data-ttu-id="42592-163">簡化設定</span><span class="sxs-lookup"><span data-stu-id="42592-163">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="42592-164">受管理的應用程式中裝載</span><span class="sxs-lookup"><span data-stu-id="42592-164">Hosting in a Managed Application</span></span>](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)  
 [<span data-ttu-id="42592-165">裝載服務</span><span class="sxs-lookup"><span data-stu-id="42592-165">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="42592-166">Windows Server App Fabric 裝載功能</span><span class="sxs-lookup"><span data-stu-id="42592-166">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)
