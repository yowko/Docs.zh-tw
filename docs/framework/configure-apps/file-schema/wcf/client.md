---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7aa3755be97a839cb576d53852b75cfe50e39276
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "72773939"
---
# \<client>
`client` 項目會定義用戶端可連線的端點清單。

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**

## <a name="syntax"></a>語法

```xml
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a>屬性和項目
 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性
 無

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[\<endpoint>](endpoint-of-client.md)|包含端點元素的集合，這些專案會指定此用戶端可連接的端點。|
|[\<metadata>](metadata.md)|包含處理中繼資料的設定。|

### <a name="parent-elements"></a>父項目

|元素|描述|
|-------------|-----------------|
|[\<system.serviceModel>](system-servicemodel.md)|所有 Windows Communication Foundation (WCF) 組態項目的根項目。|

## <a name="remarks"></a>備註
 `client` 區段會定義用戶端可連線的端點清單。 在用戶端區段中定義的每個端點會定義它自己的繫結、行為和合約。 它是以 `name` 和 `contract` 屬性的組合唯一識別的。 用戶端程式碼指定 `name` 以連線至用戶端所實作服務的端點。 如果省略 `name` 屬性，則端點會做為它所實作合約的預設端點。

 此外，本區段也會指定處理中繼資料的設定。

## <a name="example"></a>範例

```xml
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [WCF 用戶端組態](../../../wcf/feature-details/client-configuration.md)
- [用戶端](../../../wcf/feature-details/clients.md)
