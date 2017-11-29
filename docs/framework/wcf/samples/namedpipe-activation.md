---
title: "NamedPipe 啟用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 55594e1505e60ede8d7c6abcbd8a9cf9a1f739bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="namedpipe-activation"></a><span data-ttu-id="0d63a-102">NamedPipe 啟用</span><span class="sxs-lookup"><span data-stu-id="0d63a-102">NamedPipe Activation</span></span>
<span data-ttu-id="0d63a-103">此範例示範裝載服務，該服務使用 Windows Process Activation Service (WAS) 啟用透過名稱管道通訊的服務。</span><span class="sxs-lookup"><span data-stu-id="0d63a-103">This sample demonstrates hosting a service that uses Windows Process Activation Service (WAS) to activate a service that communicates over names pipes.</span></span> <span data-ttu-id="0d63a-104">這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)且需要[!INCLUDE[wv](../../../../includes/wv-md.md)]執行。</span><span class="sxs-lookup"><span data-stu-id="0d63a-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and requires [!INCLUDE[wv](../../../../includes/wv-md.md)] to run.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d63a-105">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="0d63a-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0d63a-106">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="0d63a-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0d63a-107">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="0d63a-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0d63a-108">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="0d63a-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0d63a-109">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="0d63a-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`  
  
## <a name="sample-details"></a><span data-ttu-id="0d63a-110">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="0d63a-110">Sample Details</span></span>  
 <span data-ttu-id="0d63a-111">此範例由用戶端主控台程式 (.exe) 和 Windows Process Activation Services (WAS) 啟動的工作處理序中裝載的服務程式庫 (.dll) 所組成。</span><span class="sxs-lookup"><span data-stu-id="0d63a-111">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by the Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="0d63a-112">您可以在主控台視窗中看到用戶端活動。</span><span class="sxs-lookup"><span data-stu-id="0d63a-112">Client activity is visible in the console window.</span></span>  
  
 <span data-ttu-id="0d63a-113">服務會實作定義要求-回覆通訊模式的合約。</span><span class="sxs-lookup"><span data-stu-id="0d63a-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="0d63a-114">合約是由 `ICalculator` 介面所定義，這個介面會公開數學運算 (加、減、乘、除)，如下列範例程式碼中所示。</span><span class="sxs-lookup"><span data-stu-id="0d63a-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="0d63a-115">用戶端會對指定的數學運算提出同步要求，然後服務實作計算並傳回適當結果。</span><span class="sxs-lookup"><span data-stu-id="0d63a-115">The client makes synchronous requests to a given math operation and the service implementation calculates and returns the appropriate result.</span></span>  
  
```  
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 <span data-ttu-id="0d63a-116">範例使用沒有安全性且經過修改的 `netNamedPipeBinding` 繫結。</span><span class="sxs-lookup"><span data-stu-id="0d63a-116">The sample uses a modified `netNamedPipeBinding` binding with no security.</span></span> <span data-ttu-id="0d63a-117">用戶端和服務的組態檔中會指定繫結。</span><span class="sxs-lookup"><span data-stu-id="0d63a-117">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="0d63a-118">服務的繫結類型在端點項目的 `binding` 屬性中指定，如下列範例組態中所示。</span><span class="sxs-lookup"><span data-stu-id="0d63a-118">The binding type for the service is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
 <span data-ttu-id="0d63a-119">如果您要使用安全的具名管理繫結，請將伺服器的安全性模式變更為需要的安全性設定，並在用戶端上再次執行 svcutil.exe 以取得更新的用戶端組態檔。</span><span class="sxs-lookup"><span data-stu-id="0d63a-119">If you want use a secured named pipe binding, change the server's security mode to the desired security setting and run svcutil.exe again on the client to obtain an updated client configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
        <services>  
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
  
        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->  
        <endpoint address=""   
                  binding="netNamedPipeBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is explosed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->  
        <endpoint address="mex"  
                  binding="mexNamedPipeBinding"  
                  contract="IMetadataExchange" />  
      </service>  
        </services>      
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="Binding1" >  
                    <security mode = "None">  
                    </security>  
                </binding >  
            </netNamedPipeBinding>  
        </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="0d63a-120">用戶端的端點資訊設定如下列範例程式碼中所示。</span><span class="sxs-lookup"><span data-stu-id="0d63a-120">The client’s endpoint information is configured as shown in the following sample code.</span></span>  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <endpoint name=""  
                          address="net.pipe://localhost/servicemodelsamples/service.svc"   
                          binding="netNamedPipeBinding"   
                          bindingConfiguration="Binding1"   
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
    <bindings>  
  
      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.  
            Each property is configured with the default value.   -->  
  
      <netNamedPipeBinding>  
        <binding name="Binding1"   
                         maxBufferSize="65536"  
                         maxConnections="10">  
          <security mode = "None">  
          </security>  
        </binding >  
  
      </netNamedPipeBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="0d63a-121">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="0d63a-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0d63a-122">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="0d63a-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0d63a-123">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="0d63a-123">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0d63a-124">請確定已安裝 [!INCLUDE[iisver](../../../../includes/iisver-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0d63a-124">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed.</span></span> <span data-ttu-id="0d63a-125">因為 WAS 啟用時需要 [!INCLUDE[iisver](../../../../includes/iisver-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0d63a-125">[!INCLUDE[iisver](../../../../includes/iisver-md.md)] is required for WAS activation.</span></span>  
  
2.  <span data-ttu-id="0d63a-126">確認您已經執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0d63a-126">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
     <span data-ttu-id="0d63a-127">此外，您必須安裝 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 非 HTTP 啟動元件：</span><span class="sxs-lookup"><span data-stu-id="0d63a-127">In addition, you must install the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] non-HTTP activation components:</span></span>  
  
    1.  <span data-ttu-id="0d63a-128">從**啟動**功能表上，選擇**控制台**。</span><span class="sxs-lookup"><span data-stu-id="0d63a-128">From the **Start** menu, choose **Control Panel**.</span></span>  
  
    2.  <span data-ttu-id="0d63a-129">選取**程式和功能**。</span><span class="sxs-lookup"><span data-stu-id="0d63a-129">Select **Programs and Features**.</span></span>  
  
    3.  <span data-ttu-id="0d63a-130">按一下**開啟或關閉 Windows 元件**。</span><span class="sxs-lookup"><span data-stu-id="0d63a-130">Click **Turn Windows Components on or Off**.</span></span>  
  
    4.  <span data-ttu-id="0d63a-131">展開**Microsoft.NET Framework 3.0**節點，然後核取**Windows Communication Foundation 非 HTTP 啟動**功能。</span><span class="sxs-lookup"><span data-stu-id="0d63a-131">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>  
  
3.  <span data-ttu-id="0d63a-132">設定 Windows Process Activation Service (WAS) 以支援具名管道啟動。</span><span class="sxs-lookup"><span data-stu-id="0d63a-132">Configure the Windows Process Activation Service (WAS) to support named pipe activation.</span></span>  
  
     <span data-ttu-id="0d63a-133">為了方便起見，在位於範例目錄中稱為 AddNetPipeSiteBinding.cmd 的批次檔中實作下列兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="0d63a-133">As a convenience, the following two steps are implemented in a batch file called AddNetPipeSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="0d63a-134">若要支援 net.pipe 啟動，預設的網站必須先繫結至 net.pipe 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="0d63a-134">To support net.pipe activation, the default Web site must first be bound to the net.pipe protocol.</span></span> <span data-ttu-id="0d63a-135">使用以 IIS 7.0 管理工具集安裝的 appcmd.exe 完成此操作。</span><span class="sxs-lookup"><span data-stu-id="0d63a-135">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="0d63a-136">從提高權限的 (系統管理員) 命令提示字元中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="0d63a-136">From an elevated (administrator) command prompt, run the following command.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="0d63a-137">這個命令是單行文字。</span><span class="sxs-lookup"><span data-stu-id="0d63a-137">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="0d63a-138">此命令新增繫結至預設網站的 net.pipe 網站。</span><span class="sxs-lookup"><span data-stu-id="0d63a-138">This command adds a net.pipe site binding to the default Web site.</span></span>  
  
    2.  <span data-ttu-id="0d63a-139">雖然網站中的所有應用程式共用常見的 net.pipe 繫結，但每個應用程式都可以個別啟用 net.pipe 支援。</span><span class="sxs-lookup"><span data-stu-id="0d63a-139">Although all applications within a site share a common net.pipe binding, each application can enable net.pipe support individually.</span></span> <span data-ttu-id="0d63a-140">若要啟用 /servicemodelsamples 應用程式的 net.pipe，請從提高權限的命令提示字元中執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="0d63a-140">To enable net.pipe for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="0d63a-141">這個命令是單行文字。</span><span class="sxs-lookup"><span data-stu-id="0d63a-141">This command is a single line of text.</span></span>  
  
         <span data-ttu-id="0d63a-142">這個命令可讓您使用 http://localhost/servicemodelsamples 和 net.tcp://localhost/servicemodelsamples 存取 /servicemodelsamples 應用程式。</span><span class="sxs-lookup"><span data-stu-id="0d63a-142">This command enables the /servicemodelsamples application to be accessed using both http://localhost/servicemodelsamples and net.tcp://localhost/servicemodelsamples.</span></span>  
  
4.  <span data-ttu-id="0d63a-143">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="0d63a-143">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="0d63a-144">移除您為此範例新增的 net.pipe 網站繫結。</span><span class="sxs-lookup"><span data-stu-id="0d63a-144">Remove the net.pipe site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="0d63a-145">為了方便起見，下列兩個步驟會以位於範例目錄中的 RemoveNetPipeSiteBinding.cmd 批次檔實作：</span><span class="sxs-lookup"><span data-stu-id="0d63a-145">As a convenience, the following two steps are implemented in a batch file called RemoveNetPipeSiteBinding.cmd located in the sample directory:</span></span>  
  
    1.  <span data-ttu-id="0d63a-146">從提高權限的命令提示字元中執行下列命令，以從啟用的通訊協定清單中移除 net.tcp。</span><span class="sxs-lookup"><span data-stu-id="0d63a-146">Remove net.tcp from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="0d63a-147">這個命令必須輸入為單行文字。</span><span class="sxs-lookup"><span data-stu-id="0d63a-147">This command must be entered as a single line of text.</span></span>  
  
    2.  <span data-ttu-id="0d63a-148">從提高權限的命令提示字元中執行下列命令以移除 net.tcp 網站繫結。</span><span class="sxs-lookup"><span data-stu-id="0d63a-148">Remove the net.tcp site binding by running the following command from an elevated command prompt.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="0d63a-149">這個命令必須輸入為單行文字。</span><span class="sxs-lookup"><span data-stu-id="0d63a-149">This command must be typed in as a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d63a-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d63a-150">See Also</span></span>  
 [<span data-ttu-id="0d63a-151">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="0d63a-151">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
