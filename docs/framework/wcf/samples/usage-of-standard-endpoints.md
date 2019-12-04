---
title: 使用標準端點
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 2b210bfe683669aeebf54a1701f07d492e6abdb4
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715337"
---
# <a name="usage-of-standard-endpoints"></a>使用標準端點

這個範例示範如何在服務組態檔中使用標準端點。 標準端點可讓使用者透過使用單一屬性描述位址、繫結和合約組合，並且將其他屬性與該屬性產生關聯的方式簡化端點定義。 這個範例示範如何定義及實作自訂標準端點，以及如何定義端點中的特定屬性。

## <a name="sample-details"></a>範例詳細資料

服務端點可以透過提供三個參數指定：位址、繫結和合約。 其他可提供的參數包括行為組態、標頭和接聽 URI 等。 在某些情況下，任何或所有位址、繫結和合約會有無法變更的值。 因此可以使用標準端點。 這類端點的範例包括中繼資料交換端點和探索端點。 標準端點還可透過允許設定服務端點，而不需提供固定特質的資訊或建立自己的標準端點，藉此改善可用性，例如透過提供一組合理的預設值，因而降低組態檔的詳細程度，達到改善可用性的目的。

這個範例包括兩個專案：定義兩個標準端點的服務，以及與該服務進行通訊的用戶端。 在組態檔中為服務定義標準端點的方式如下列範例所示。

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

為服務定義的第一個端點為 `customEndpoint` 類型，其定義可以在 `<standardEndpoints>` 區段中看見，其中 `property` 屬性的值會指定為 `true`。 這個案例中，端點擁有自訂的新屬性。 第二個端點會對應至中繼資料端點，其中位址、繫結和合約的值是固定的。

若要定義標準端點項目，則必須建立衍生自 `StandardEndpointElement` 的類別。 在這個範例中已定義 `CustomEndpointElement` 類別，如下列範例所示。

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

在 `CreateServiceEndpoint` 函式中會建立 `CustomEndpoint` 物件。 其定義如下列範例所示：

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

 為了在服務和用戶端之間進行通訊，用戶端中會建立對服務的服務參考。 範例建立完成並執行時，服務就會執行且用戶端會與該服務通訊。 請注意，服務參考應該在每次服務中有變更時更新。

#### <a name="to-use-this-sample"></a>若要使用這個範例

1. 使用 Visual Studio 2012，開啟 [StandardEndpoints] 檔案。

2. 讓多個專案啟動。

    1. 在**方案總管**中，以滑鼠右鍵按一下 [標準端點] 解決方案，然後選取 [**屬性**]。

    2. 在 [**通用屬性**] 中，選取 [**啟始專案**]，然後按一下 [**多個啟始專案**]。

    3. 將 [服務] 專案移至清單的開頭，並將 [**動作**] 設定為 [**啟動**]。

    4. 將用戶端專案移至服務專案之後，同時將**動作**設定為 [**啟動**]。

         這樣會指定 [用戶端] 專案在 [服務] 專案之後執行。

3. 若要執行此方案，請按 F5。

> [!NOTE]
> 如果這些步驟沒有作用，請使用下列步驟，確定您的環境已正確設定：
>
> 1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。
> 2. 若要建立方案，請依照[建立 Windows Communication Foundation 範例](building-the-samples.md)中的指示進行。
> 3. 若要在單一或多個電腦設定中執行範例，請遵循執行[Windows Communication Foundation 範例](running-the-samples.md)中的指示。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
