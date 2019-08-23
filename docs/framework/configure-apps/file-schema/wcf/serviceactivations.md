---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: fb7c699612ef12aae39aaeadaf170d0e8f2553cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936438"
---
# <a name="serviceactivations"></a>\<serviceActivations>

一種 configuration 專案, 可讓您新增設定, 以定義對應至您的 Windows Communication Foundation (WCF) 服務類型的虛擬服務啟用設定。 如此一來，不需 .svc 檔案也能啟動裝載於 WAS/IIS 中的服務。

\<system.ServiceModel>\
\<serviceHostingEnvironment > \
\<serviceActivations>

## <a name="syntax"></a>語法

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|項目|說明|
|-------------|-----------------|
|[\<add>](add-of-serviceactivations.md)|加入組態項目，此項目指定服務應用程式的啟動。|

### <a name="parent-elements"></a>父項目

|項目|說明|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|定義服務裝載環境為特定傳輸產生的類型。|

## <a name="remarks"></a>備註

下列範例示範如何在您的 web.config 檔案中設定啟動設定。

```xml
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```

使用這個組態時，您不需要使用 .svc 檔案也可以啟動 GreetingService。

請注意，`<serviceHostingEnvironment>` 是應用程式層級的組態。 您必須將包含該組態的 `web.config` 置於虛擬應用程式的根之下。 此外, `serviceHostingEnvironment`是可繼承的 machineToApplication 區段。 如果在電腦的根中註冊單一服務，則應用程式中的每個服務都會繼承這個服務。

以組態為主的啟動支援透過 HTTP 和非 HTTP 通訊協定啟動。 它需要 relativeAddress 中的延伸模組, 例如 .svc、. xoml 或. service1.xamlx。 您可以將自己的擴充對應至已知的 buildProvider，這樣您就可以透過任何擴充啟動服務。 發生衝突時，`<serviceActivations>` 區段會覆寫 .svc 註冊。

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
