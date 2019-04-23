---
title: 使用標準端點
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 4ef0714acad12db1414e34fbb476b4ae7d1d9fb2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977076"
---
# <a name="usage-of-standard-endpoints"></a><span data-ttu-id="d8b2b-102">使用標準端點</span><span class="sxs-lookup"><span data-stu-id="d8b2b-102">Usage of Standard Endpoints</span></span>

<span data-ttu-id="d8b2b-103">這個範例示範如何在服務組態檔中使用標準端點。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-103">This sample demonstrates how to use standard endpoints in service configuration files.</span></span> <span data-ttu-id="d8b2b-104">標準端點可讓使用者透過使用單一屬性描述位址、繫結和合約組合，並且將其他屬性與該屬性產生關聯的方式簡化端點定義。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-104">A standard endpoint allows the user to simplify endpoint definitions by using a single property to describe an address, binding and contract combination with additional properties associated to it.</span></span> <span data-ttu-id="d8b2b-105">這個範例示範如何定義及實作自訂標準端點，以及如何定義端點中的特定屬性。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-105">This sample demonstrates how to define and implement a custom standard endpoint and how to define specific properties in the endpoint.</span></span>

## <a name="sample-details"></a><span data-ttu-id="d8b2b-106">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="d8b2b-106">Sample Details</span></span>

<span data-ttu-id="d8b2b-107">服務端點可以透過提供三個參數指定：位址、繫結和合約。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-107">Service endpoints can be specified by supplying three parameters: address, binding and contract.</span></span> <span data-ttu-id="d8b2b-108">其他可提供的參數包括行為組態、標頭和接聽 URI 等。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-108">Other parameters that can be supplied include behavior configuration, headers, listen URI, and so on.</span></span> <span data-ttu-id="d8b2b-109">在某些情況下，任何或所有位址、繫結和合約會有無法變更的值。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-109">In some cases, any or all of addresses, bindings and contracts have values that cannot change.</span></span> <span data-ttu-id="d8b2b-110">因此可以使用標準端點。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-110">For this reason, it is possible to use standard endpoints.</span></span> <span data-ttu-id="d8b2b-111">這類端點的範例包括中繼資料交換端點和探索端點。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-111">Some examples of such endpoints include metadata exchange endpoints and discovery endpoints.</span></span> <span data-ttu-id="d8b2b-112">標準端點還可透過允許設定服務端點，而不需提供固定特質的資訊或建立自己的標準端點，藉此改善可用性，例如透過提供一組合理的預設值，因而降低組態檔的詳細程度，達到改善可用性的目的。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-112">Standard endpoints also improve usability by allowing configuration of service endpoints without having to provide information of a fixed nature or to create their own standard endpoints, for example to improve usability by supplying a reasonable set of default values and thus reducing the verbosity of configuration files.</span></span>

<span data-ttu-id="d8b2b-113">這個範例包括兩個專案：定義兩個標準端點的服務，以及與該服務進行通訊的用戶端。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-113">This sample consists of two projects: the service that defines two standard endpoints and the client that communicates with the service.</span></span> <span data-ttu-id="d8b2b-114">在組態檔中為服務定義標準端點的方式如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-114">The way the standard endpoints are defined for the service in the configuration file is show in the following example.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <extensions>
      <endpointExtensions>
        <add name="customEndpoint" type="Microsoft.Samples.StandardEndpoints.CustomEndpointCollectionElement, service" />
      </endpointExtensions>
    </extensions>
    <services>
      <service name="Microsoft.Samples.StandardEndpoints.CalculatorService">
        <endpoint address="http://localhost:8000/Samples/Service.svc/customEndpoint" contract="Microsoft.Samples.StandardEndpoints.ICalculator" kind="customEndpoint" />
        <endpoint kind="mexEndpoint" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="True"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <standardEndpoints>
      <customEndpoint>
        <standardEndpoint property="True" />
      </customEndpoint>
    </standardEndpoints>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="d8b2b-115">為服務定義的第一個端點為 `customEndpoint` 類型，其定義可以在 `<standardEndpoints>` 區段中看見，其中 `property` 屬性的值會指定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-115">The first endpoint defined for the service is of kind `customEndpoint`, whose definition can be seen in the `<standardEndpoints>` section, in which the property `property` is given the value `true`.</span></span> <span data-ttu-id="d8b2b-116">這個案例中，端點擁有自訂的新屬性。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-116">This is the case of an endpoint customized with a new property.</span></span> <span data-ttu-id="d8b2b-117">第二個端點會對應至中繼資料端點，其中位址、繫結和合約的值是固定的。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-117">The second endpoint corresponds to a metadata endpoint, in which the values for address, binding and contract are fixed.</span></span>

<span data-ttu-id="d8b2b-118">若要定義標準端點項目，則必須建立衍生自 `StandardEndpointElement` 的類別。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-118">To define the standard endpoint element, a class that derives from `StandardEndpointElement` must be created.</span></span> <span data-ttu-id="d8b2b-119">在這個範例中已定義 `CustomEndpointElement` 類別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-119">In the case of this sample, the `CustomEndpointElement` class has been defined as shown in the following example.</span></span>

```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```

<span data-ttu-id="d8b2b-120">在 `CreateServiceEndpoint` 函式中會建立 `CustomEndpoint` 物件。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-120">In the `CreateServiceEndpoint` function, a `CustomEndpoint` object is created.</span></span> <span data-ttu-id="d8b2b-121">其定義如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d8b2b-121">Its definition is shown in the following example:</span></span>

```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    {
    }

    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    {
    }

    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }

    public bool Property
    {
        get;
        set;
    }
}
```

 <span data-ttu-id="d8b2b-122">為了在服務和用戶端之間進行通訊，用戶端中會建立對服務的服務參考。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-122">To perform the communication between service and client, a service reference is created in the client to the service.</span></span> <span data-ttu-id="d8b2b-123">範例建立完成並執行時，服務就會執行且用戶端會與該服務通訊。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-123">When the sample is built and executed, the service executes and the client communicates with it.</span></span> <span data-ttu-id="d8b2b-124">請注意，服務參考應該在每次服務中有變更時更新。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-124">Note that the service reference should be updated every time there is some change in the service.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="d8b2b-125">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="d8b2b-125">To use this sample</span></span>

1. <span data-ttu-id="d8b2b-126">使用 Visual Studio 2012，請開啟 [standardendpoints.sln] 檔案。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-126">Using Visual Studio 2012, open the StandardEndpoints.sln file.</span></span>

2. <span data-ttu-id="d8b2b-127">讓多個專案啟動。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-127">Enable multiple projects to start up.</span></span>

    1.  <span data-ttu-id="d8b2b-128">在 **方案總管**，以滑鼠右鍵按一下 標準端點 方案，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-128">In **Solution Explorer**, right-click the Standard Endpoints solution and then select **Properties**.</span></span>

    2.  <span data-ttu-id="d8b2b-129">在 **通用屬性**，選取**啟始專案**，然後按一下**多個啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-129">In **Common Properties**, select **Startup Project**, and then click **Multiple Startup Projects**.</span></span>

    3.  <span data-ttu-id="d8b2b-130">移至清單中，開頭的服務專案，具有**動作**設為**開始**。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-130">Move the Service project to the beginning of the list, with the **Action** set to **Start**.</span></span>

    4.  <span data-ttu-id="d8b2b-131">用戶端專案在之後移動服務專案中，也與**動作**設為**開始**。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-131">Move the Client project after the Service project, also with the **Action** set to **Start**.</span></span>

         <span data-ttu-id="d8b2b-132">這樣會指定 [用戶端] 專案在 [服務] 專案之後執行。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-132">This specifies that the Client project is executed after the Service project.</span></span>

3. <span data-ttu-id="d8b2b-133">若要執行此方案，請按 F5。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-133">To run the solution, press F5.</span></span>

> [!NOTE]
> <span data-ttu-id="d8b2b-134">如果這些步驟沒有作用，請確定，您的環境已正確設定，使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d8b2b-134">If these steps don't work, then make sure that your environment has been properly set up, using the following steps:</span></span>
>
> 1. <span data-ttu-id="d8b2b-135">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>
> 2. <span data-ttu-id="d8b2b-136">若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-136">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>
> 3. <span data-ttu-id="d8b2b-137">若要執行單一或多個電腦組態中的範例，請遵循中的指示[執行 Windows Communication Foundation 範例](running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-137">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8b2b-138">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d8b2b-139">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d8b2b-140">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-140">If this directory doesn't exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d8b2b-141">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="d8b2b-141">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
