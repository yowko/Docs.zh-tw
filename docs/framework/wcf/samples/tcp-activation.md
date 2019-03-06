---
title: TCP 啟用
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: 065c4706d0a52414c4abed85044ce06ad3efe35c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374917"
---
# <a name="tcp-activation"></a><span data-ttu-id="bbaba-102">TCP 啟用</span><span class="sxs-lookup"><span data-stu-id="bbaba-102">TCP Activation</span></span>

<span data-ttu-id="bbaba-103">這個範例會示範裝載使用 Windows Process Activation Service (WAS) 的服務，以便啟用透過 net.tcp 通訊協定進行通訊的服務。</span><span class="sxs-lookup"><span data-stu-id="bbaba-103">This sample demonstrates hosting a service that uses Windows Process Activation Services (WAS) to activate a service that communicates over the net.tcp protocol.</span></span> <span data-ttu-id="bbaba-104">此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="bbaba-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>

> [!NOTE]
> <span data-ttu-id="bbaba-105">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="bbaba-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bbaba-106">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="bbaba-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bbaba-107">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="bbaba-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="bbaba-108">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="bbaba-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bbaba-109">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="bbaba-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`

<span data-ttu-id="bbaba-110">這個範例包括用戶端主控台程式 (.exe)，以及透過 WAS 啟用之背景工作處理序所裝載的服務程式庫 (.dll)。</span><span class="sxs-lookup"><span data-stu-id="bbaba-110">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by WAS.</span></span> <span data-ttu-id="bbaba-111">您可以在主控台視窗中看到用戶端活動。</span><span class="sxs-lookup"><span data-stu-id="bbaba-111">Client activity is visible in the console window.</span></span>

<span data-ttu-id="bbaba-112">服務會實作定義要求-回覆通訊模式的合約。</span><span class="sxs-lookup"><span data-stu-id="bbaba-112">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="bbaba-113">合約是由 `ICalculator` 介面所定義，這個介面會公開數學運算 (加、減、乘、除)，如下列範例程式碼中所示：</span><span class="sxs-lookup"><span data-stu-id="bbaba-113">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code:</span></span>

```csharp
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

<span data-ttu-id="bbaba-114">服務實作會計算並傳回適當結果：</span><span class="sxs-lookup"><span data-stu-id="bbaba-114">The service implementation calculates and returns the appropriate result:</span></span>

```csharp
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

<span data-ttu-id="bbaba-115">此範例會使用 net.tcp 繫結的變化，其 TCP 連接埠共用已啟用，而安全性已關閉。</span><span class="sxs-lookup"><span data-stu-id="bbaba-115">The sample uses a variant of the net.tcp binding with TCP port sharing enabled and security turned off.</span></span> <span data-ttu-id="bbaba-116">如果您想要使用安全的 TCP 繫結，請將伺服器的安全性模式變更為需要的設定，並在用戶端上重新執行 Svcutil.exe 以產生更新的用戶端組態檔。</span><span class="sxs-lookup"><span data-stu-id="bbaba-116">If you want to use a secured TCP binding, change the server's security mode to the desired setting and re-run Svcutil.exe on the client to generate an update client configuration file.</span></span>

<span data-ttu-id="bbaba-117">下列範例會示範此服務的組態：</span><span class="sxs-lookup"><span data-stu-id="bbaba-117">The following sample shows the configuration for the service:</span></span>

```xml
<system.serviceModel>

    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexTcpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netTcpBinding>
        <binding name="PortSharingBinding" portSharingEnabled="true">
          <security mode="None" />
        </binding>
      </netTcpBinding>
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

<span data-ttu-id="bbaba-118">用戶端的端點設定如下列範例程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="bbaba-118">The client's endpoint is configured as shown in the following sample code:</span></span>

```xml
<system.serviceModel>
    <bindings>
        <netTcpBinding>
          <binding name="NetTcpBinding_ICalculator">
            <security mode="None"/>
          </binding>
        </netTcpBinding>
    </bindings>
    <client>
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />
    </client>
</system.serviceModel>
```

<span data-ttu-id="bbaba-119">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="bbaba-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bbaba-120">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="bbaba-120">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bbaba-121">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="bbaba-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="bbaba-122">請確定已安裝 [!INCLUDE[iisver](../../../../includes/iisver-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bbaba-122">Ensure that [!INCLUDE[iisver](../../../../includes/iisver-md.md)] is installed.</span></span> <span data-ttu-id="bbaba-123">因為 WAS 啟用時需要 [!INCLUDE[iisver](../../../../includes/iisver-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bbaba-123">[!INCLUDE[iisver](../../../../includes/iisver-md.md)] is required for WAS activation.</span></span>

2. <span data-ttu-id="bbaba-124">確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="bbaba-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="bbaba-125">此外，您必須安裝 WCF 非 HTTP 啟動元件：</span><span class="sxs-lookup"><span data-stu-id="bbaba-125">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="bbaba-126">在 [開始] 功能表內選擇 [控制台]。</span><span class="sxs-lookup"><span data-stu-id="bbaba-126">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="bbaba-127">選取 **程式和功能**。</span><span class="sxs-lookup"><span data-stu-id="bbaba-127">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="bbaba-128">按一下 **開啟或關閉 Windows 元件**。</span><span class="sxs-lookup"><span data-stu-id="bbaba-128">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="bbaba-129">依序展開**Microsoft.NET Framework 3.0**節點，並檢查**Windows Communication Foundation 非 HTTP 啟動**功能。</span><span class="sxs-lookup"><span data-stu-id="bbaba-129">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="bbaba-130">設定 WAS 成支援 TCP 啟動。</span><span class="sxs-lookup"><span data-stu-id="bbaba-130">Configure WAS to support TCP activation.</span></span>

    <span data-ttu-id="bbaba-131">為了方便起見，下列兩個步驟會以範例目錄中名為 AddNetTcpSiteBinding.cmd 的批次檔來加以實作。</span><span class="sxs-lookup"><span data-stu-id="bbaba-131">As a convenience, the following two steps are implemented in a batch file called AddNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="bbaba-132">若要支援 net.tcp 啟動，預設的網站必須先繫結至 net.tcp 連接埠。</span><span class="sxs-lookup"><span data-stu-id="bbaba-132">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="bbaba-133">使用 Internet Information Services 7.0 (IIS) 管理工具組所安裝的 Appcmd.exe，便可做到這點。</span><span class="sxs-lookup"><span data-stu-id="bbaba-133">This can be done using Appcmd.exe, which is installed with the Internet Information Services 7.0 (IIS) management toolset.</span></span> <span data-ttu-id="bbaba-134">從系統管理員層級的命令提示字元執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="bbaba-134">From an administrator-level command prompt, run the following command:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!TIP]
        > <span data-ttu-id="bbaba-135">這個命令是單行文字。</span><span class="sxs-lookup"><span data-stu-id="bbaba-135">This command is a single line of text.</span></span> <span data-ttu-id="bbaba-136">這個命令會將 net.tcp 網站繫結新增至預設網站，此網站會接聽含有任何主機名稱的 TCP 連接埠 808。</span><span class="sxs-lookup"><span data-stu-id="bbaba-136">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any hostname.</span></span>

    2. <span data-ttu-id="bbaba-137">雖然網站中的所有應用程式共用常見的 net.tcp 繫結，但每個應用程式都可以個別啟用 net.tcp 支援。</span><span class="sxs-lookup"><span data-stu-id="bbaba-137">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="bbaba-138">若要為 /servicemodelsamples 應用程式啟用 net.tcp，請從系統管理員層級命令提示字元中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="bbaba-138">To enable net.tcp for the /servicemodelsamples application, run the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp
        ```

        > [!NOTE]
        > <span data-ttu-id="bbaba-139">這個命令是單行文字。</span><span class="sxs-lookup"><span data-stu-id="bbaba-139">This command is a single line of text.</span></span> <span data-ttu-id="bbaba-140">此命令會啟用 /servicemodelsamples 應用程式使用兩者來存取`http://localhost/servicemodelsamples`和`net.tcp://localhost/servicemodelsamples`。</span><span class="sxs-lookup"><span data-stu-id="bbaba-140">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="bbaba-141">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="bbaba-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

5. <span data-ttu-id="bbaba-142">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="bbaba-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    <span data-ttu-id="bbaba-143">移除您為此範例新增的 net.tcp 網站繫結。</span><span class="sxs-lookup"><span data-stu-id="bbaba-143">Remove the net.tcp site binding you added for this sample.</span></span>

    <span data-ttu-id="bbaba-144">為了方便起見，下列兩個步驟會以範例目錄中名為 RemoveNetTcpSiteBinding.cmd 的批次檔來加以實作。</span><span class="sxs-lookup"><span data-stu-id="bbaba-144">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="bbaba-145">從啟用的通訊協定清單中移除 net.tcp，方法是從系統管理員層級命令提示字元中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="bbaba-145">Remove net.tcp from the list of enabled protocols by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="bbaba-146">這個命令必須輸入為單行文字。</span><span class="sxs-lookup"><span data-stu-id="bbaba-146">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="bbaba-147">移除 net.tcp 網站繫結，方法是從系統管理員層級命令提示字元中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="bbaba-147">Remove the net.tcp site binding by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="bbaba-148">這個命令必須輸入為單行文字。</span><span class="sxs-lookup"><span data-stu-id="bbaba-148">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbaba-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbaba-149">See also</span></span>

- [<span data-ttu-id="bbaba-150">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="bbaba-150">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
