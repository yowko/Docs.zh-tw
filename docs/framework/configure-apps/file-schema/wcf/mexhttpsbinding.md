---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 924d68dd828622b74c5e424a695f80874391b453
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430334"
---
# <a name="mexhttpsbinding"></a>\<mexHttpsBinding>
指定用於 HTTPS 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpsBinding>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<mexHttpsBinding>
  <binding closeTimeout="TimeSpan"
            name="string"
            openTimeout="TimeSpan"
            receiveTimeout="TimeSpan"
            sendTimeout="TimeSpan">
  </binding>
</mexHttpsBinding>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`closeTimeout`|<xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|`name`|包含繫結之組態名稱的字串。 這個值應該是唯一的，因為它會當做繫結的識別使用。 Starting with .NET Framework 4, bindings and behaviors are not required to have a name. For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|<xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|`receiveTimeout`|<xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:10:00。|  
|`sendTimeout`|<xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|這個項目會保存標準和自訂繫結的集合。|  
  
## <a name="remarks"></a>備註  
 這個繫結實質上為 `WSHttpBinding` 繫結，其支援使用憑證的傳輸層級安全性。 For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).  
  
## <a name="see-also"></a>請參閱

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [如何：使用組態檔發行服務的中繼資料](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [發行與擷取自訂繫結上的中繼資料](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [如何：設定自訂 WS-Metadata Exchange 繫結](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [如何：透過非 MEX 繫結擷取中繼資料](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [自訂安全中繼資料端點](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [中繼資料](../../../wcf/feature-details/metadata.md)
- [繫結](../../../wcf/bindings.md)
- [設定系統提供的繫結](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
