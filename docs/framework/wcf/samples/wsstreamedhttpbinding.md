---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: aa2acc7228f802f69e8692ed747af0382345c1d6
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016068"
---
# <a name="wsstreamedhttpbinding"></a><span data-ttu-id="4ec54-102">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="4ec54-102">WSStreamedHttpBinding</span></span>

<span data-ttu-id="4ec54-103">本範例會示範如何建立可在使用 HTTP 傳輸時支援資料流案例的繫結。</span><span class="sxs-lookup"><span data-stu-id="4ec54-103">The sample demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>

> [!NOTE]
> <span data-ttu-id="4ec54-104">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="4ec54-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4ec54-105">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4ec54-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4ec54-106">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="4ec54-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="4ec54-107">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="4ec54-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4ec54-108">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="4ec54-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`

 <span data-ttu-id="4ec54-109">建立與設定新標準繫結的步驟如下所示。</span><span class="sxs-lookup"><span data-stu-id="4ec54-109">The steps to create and configure a new standard binding are as follows.</span></span>

1. <span data-ttu-id="4ec54-110">建立新標準繫結</span><span class="sxs-lookup"><span data-stu-id="4ec54-110">Create a new standard binding</span></span>

    <span data-ttu-id="4ec54-111">Windows Communication Foundation (WCF) 中的標準系結 (例如 basicHttpBinding) 和 netTcpBinding 會設定特定需求的基礎傳輸與通道堆疊。</span><span class="sxs-lookup"><span data-stu-id="4ec54-111">The standard bindings in Windows Communication Foundation (WCF) such as basicHttpBinding, and netTcpBinding configure the underlying transports and channel stack for specific requirements.</span></span> <span data-ttu-id="4ec54-112">在這個範例中，`WSStreamedHttpBinding` 會將通道堆疊設定成支援資料流。</span><span class="sxs-lookup"><span data-stu-id="4ec54-112">In this sample, `WSStreamedHttpBinding` configures the channel stack to support streaming.</span></span> <span data-ttu-id="4ec54-113">根據預設，WS-Security 和可信賴傳訊不會新增至通道堆疊中，因為資料流並不支援這兩項功能。</span><span class="sxs-lookup"><span data-stu-id="4ec54-113">By default, WS-Security and reliable messaging are not added to the channel stack because both features are not supported by streaming.</span></span> <span data-ttu-id="4ec54-114">新繫結是透過衍生自 `WSStreamedHttpBinding` 的 <xref:System.ServiceModel.Channels.Binding> 類別所實作的。</span><span class="sxs-lookup"><span data-stu-id="4ec54-114">The new binding is implemented in the class `WSStreamedHttpBinding` that derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="4ec54-115">`WSStreamedHttpBinding` 包含下列繫結項目：<xref:System.ServiceModel.Channels.HttpTransportBindingElement>、<xref:System.ServiceModel.Channels.HttpsTransportBindingElement>、<xref:System.ServiceModel.Channels.TransactionFlowBindingElement> 和 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="4ec54-115">The `WSStreamedHttpBinding` contains the following binding elements: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, and <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span> <span data-ttu-id="4ec54-116">類別會提供 `CreateBindingElements()` 方法以設定結果繫結堆疊，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4ec54-116">The class provides a `CreateBindingElements()` method to configure the resulting binding stack, as shown in the following sample code.</span></span>

    ```csharp
    public override BindingElementCollection CreateBindingElements()
    {
        // return collection of BindingElements
        BindingElementCollection bindingElements = new BindingElementCollection();

        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by
        // the message encoder, and finally the transport at the end
        if (flowTransactions)
        {
            bindingElements.Add(transactionFlow);
        }
        bindingElements.Add(textEncoding);

        // add transport (http or https)
        bindingElements.Add(transport);
        return bindingElements.Clone();
    }
    ```

2. <span data-ttu-id="4ec54-117">新增組態支援</span><span class="sxs-lookup"><span data-stu-id="4ec54-117">Add configuration support</span></span>

    <span data-ttu-id="4ec54-118">為了透過組態公開傳輸，此範例會實作兩個額外的類別：`WSStreamedHttpBindingConfigurationElement` 和 `WSStreamedHttpBindingSection`。</span><span class="sxs-lookup"><span data-stu-id="4ec54-118">To expose the transport through configuration the sample implements two more classes—`WSStreamedHttpBindingConfigurationElement` and `WSStreamedHttpBindingSection`.</span></span> <span data-ttu-id="4ec54-119">類別`WSStreamedHttpBindingSection` `WSStreamedHttpBinding`是,它會公開至WCF設定系統。<xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602></span><span class="sxs-lookup"><span data-stu-id="4ec54-119">The class `WSStreamedHttpBindingSection` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `WSStreamedHttpBinding` to the WCF configuration system.</span></span> <span data-ttu-id="4ec54-120">大量實作會委派至衍生自 `WSStreamedHttpBindingConfigurationElement` 的 <xref:System.ServiceModel.Configuration.StandardBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="4ec54-120">The bulk of the implementation is delegated to `WSStreamedHttpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="4ec54-121">類別 `WSStreamedHttpBindingConfigurationElement` 有對應至 `WSStreamedHttpBinding` 之屬性的屬性，以及將每個組態項目對應至繫結的功能。</span><span class="sxs-lookup"><span data-stu-id="4ec54-121">The class `WSStreamedHttpBindingConfigurationElement` has properties that correspond to the properties of `WSStreamedHttpBinding`, and functions to map each configuration element to a binding.</span></span>

    <span data-ttu-id="4ec54-122">向組態系統註冊此處理常式的方式是，將下列區段新增至服務的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="4ec54-122">Register the handler with the configuration system, by adding the following section to the service's configuration file.</span></span>

    ```xml
    <configuration>
      <system.serviceModel>
        <extensions>
          <bindingExtensions>
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />
          </bindingExtensions>
        </extensions>
      </system.serviceModel>
    </configuration>
    ```

    <span data-ttu-id="4ec54-123">這樣就能夠從 serviceModel 組態區段參考該處理常式。</span><span class="sxs-lookup"><span data-stu-id="4ec54-123">The handler can then be referenced from the serviceModel configuration section.</span></span>

    ```xml
    <configuration>
      <system.serviceModel>
        <client>
          <endpoint
                    address="https://localhost/servicemodelsamples/service.svc"
                    bindingConfiguration="Binding"
                    binding="wsStreamedHttpBinding"
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>
        </client>
      </system.serviceModel>
    </configuration>
    ```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4ec54-124">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="4ec54-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="4ec54-125">使用下列命令安裝 ASP.NET 4.0。</span><span class="sxs-lookup"><span data-stu-id="4ec54-125">Install ASP.NET 4.0 using the following command.</span></span>

    ```
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="4ec54-126">請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)中所列的步驟。</span><span class="sxs-lookup"><span data-stu-id="4ec54-126">Ensure that you have performed the steps listed in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="4ec54-127">請確定您已執行[Internet Information Services (IIS) 伺服器憑證安裝指示](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)。</span><span class="sxs-lookup"><span data-stu-id="4ec54-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>

4. <span data-ttu-id="4ec54-128">若要建立方案, 請依照[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="4ec54-128">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

5. <span data-ttu-id="4ec54-129">若要在跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="4ec54-129">To run the sample in a cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

6. <span data-ttu-id="4ec54-130">當用戶端視窗顯示時，請輸入 "Sample.txt"。</span><span class="sxs-lookup"><span data-stu-id="4ec54-130">When the client window displays, type "Sample.txt".</span></span> <span data-ttu-id="4ec54-131">您應該會在目錄中找到「複製 - Sample.txt」。</span><span class="sxs-lookup"><span data-stu-id="4ec54-131">You should find a "Copy of Sample.txt" in your directory.</span></span>

## <a name="the-wsstreamedhttpbinding-sample-service"></a><span data-ttu-id="4ec54-132">WSStreamedHttpBinding 範例服務</span><span class="sxs-lookup"><span data-stu-id="4ec54-132">The WSStreamedHttpBinding Sample Service</span></span>

<span data-ttu-id="4ec54-133">使用 `WSStreamedHttpBinding` 的範例服務位於服務子目錄中。</span><span class="sxs-lookup"><span data-stu-id="4ec54-133">The sample service that uses `WSStreamedHttpBinding` is located in the service subdirectory.</span></span> <span data-ttu-id="4ec54-134">`OperationContract` 的實作會先使用 `MemoryStream` 從傳入資料流擷取所有資料，接著再傳回 `MemoryStream`。</span><span class="sxs-lookup"><span data-stu-id="4ec54-134">The implementation of `OperationContract` uses a `MemoryStream` to first retrieve all data from the incoming stream before returning the `MemoryStream`.</span></span> <span data-ttu-id="4ec54-135">此範例服務是由網際網路資訊服務 (IIS) 裝載。</span><span class="sxs-lookup"><span data-stu-id="4ec54-135">The sample service is hosted by Internet Information Services (IIS).</span></span>

```csharp
[ServiceContract]
public interface IStreamedEchoService
{
    [OperationContract]
    Stream Echo(Stream data);
}

public class StreamedEchoService : IStreamedEchoService
{
    public Stream Echo(Stream data)
    {
        MemoryStream dataStorage = new MemoryStream();
        byte[] byteArray = new byte[8192];
        int bytesRead = data.Read(byteArray, 0, 8192);
        while (bytesRead > 0)
        {
            dataStorage.Write(byteArray, 0, bytesRead);
            bytesRead = data.Read(byteArray, 0, 8192);
        }
        data.Close();
        dataStorage.Seek(0, SeekOrigin.Begin);

        return dataStorage;
    }
}
```

## <a name="the-wsstreamedhttpbinding-sample-client"></a><span data-ttu-id="4ec54-136">WSStreamedHttpBinding 範例用戶端</span><span class="sxs-lookup"><span data-stu-id="4ec54-136">The WSStreamedHttpBinding Sample Client</span></span>

<span data-ttu-id="4ec54-137">透過 `WSStreamedHttpBinding` 與服務互動時所使用的用戶端位於用戶端子目錄中。</span><span class="sxs-lookup"><span data-stu-id="4ec54-137">The client that is used to interact with the service using `WSStreamedHttpBinding` is located in the client subdirectory.</span></span> <span data-ttu-id="4ec54-138">因為此範例中使用的憑證是使用 Makecert 建立的測試憑證, 所以當您嘗試存取瀏覽器中的 HTTPS 位址 (例如) https://localhost/servicemodelsamples/service.svc 時, 會顯示安全性警示。</span><span class="sxs-lookup"><span data-stu-id="4ec54-138">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert displays when you attempt to access an HTTPS address in your browser such as https://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="4ec54-139">為了讓 WCF 用戶端能夠使用測試憑證, 已將一些額外的程式碼新增至用戶端, 以隱藏安全性警示。</span><span class="sxs-lookup"><span data-stu-id="4ec54-139">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="4ec54-140">使用實際執行憑證時，不需要這個程式碼及伴隨的類別。</span><span class="sxs-lookup"><span data-stu-id="4ec54-140">The code and the accompanying class are not required when using production certificates.</span></span>

```csharp
// WARNING: This code is only required for test certificates such as those created by makecert. It is
// not recommended for production code.
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");
```
