---
title: <add> 的 <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: a0f68717f765482f53e675458fae63d1a374d6fb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850325"
---
# <a name="add-of-serviceactivations"></a>\<add> 的 \<serviceActivations>

一種 configuration 專案，可讓您定義虛擬服務啟用設定，以對應至您的 Windows Communication Foundation （WCF）服務類型。 如此一來，不需 .svc 檔案也能啟動裝載於 WAS/IIS 中的服務。

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceActivations>**](serviceactivations.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  

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

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|工廠|字串，指定產生服務啟動項目之處理站的 CLR 型別名稱。|
|服務|實作服務的 ServiceType 可以是完整 Typename 或簡短 Typename (置於 App_Code 資料夾時)。|
|relativeAddress|在目前 IIS 應用程式中的相對位址，例如 "Service.svc"。 在 WCF 4.0 中，此相對位址必須包含其中一個已知副檔名（.svc、. service1.xamlx、...）。RelativeUrl 不存在任何實體檔案|

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|描述啟動設定的組態區段。|

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

請注意，`<serviceHostingEnvironment>` 是應用程式層級的組態。 您必須將包含該組態的 `web.config` 置於虛擬應用程式的根之下。 此外， `serviceHostingEnvironment` 是可繼承的 machineToApplication 區段。 如果在電腦的根中註冊單一服務，則應用程式中的每個服務都會繼承這個服務。

以組態為主的啟動支援透過 HTTP 和非 HTTP 通訊協定啟動。 它需要 relativeAddress 中的延伸模組，也就是 .svc、. xoml 或. service1.xamlx。 您可以將自己的擴充對應至已知的 buildProvider，這樣您就可以透過任何擴充啟動服務。 發生衝突時，`<serviceActivations>` 區段會覆寫 .svc 註冊。

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
