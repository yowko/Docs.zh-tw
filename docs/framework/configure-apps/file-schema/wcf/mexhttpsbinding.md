---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 30d1aa27ce29b6aa4091c3e7be05746ad462102a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931274"
---
# <a name="mexhttpsbinding"></a>\<mexHttpsBinding>
指定用於 HTTPS 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。  
  
 \<system.ServiceModel>  
\<bindings>  
\<mexHttpsBinding>  
  
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
  
|屬性|說明|  
|---------------|-----------------|  
|`closeTimeout`|<xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|`name`|包含繫結之組態名稱的字串。 這個值應該是唯一的，因為它會當做繫結的識別使用。 每一個繫結都有一個 `name` 和 `namespace` 屬性，兩者結合在一起便可在服務的中繼資料中唯一識別各個繫結。 此外，這個名稱在相同型別的繫結中也是唯一的。 從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。 如需預設設定和無相關系結和行為的詳細資訊, 請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。|  
|`openTimeout`|<xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
|`receiveTimeout`|<xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:10:00。|  
|`sendTimeout`|<xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。 這個值應該大於或等於 <xref:System.TimeSpan.Zero>。 預設為 00:01:00。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|這個項目會保存標準和自訂繫結的集合。|  
  
## <a name="remarks"></a>備註  
 這個繫結實質上為 `WSHttpBinding` 繫結，其支援使用憑證的傳輸層級安全性。 如需設定和使用這類中繼資料端點的詳細資訊[, 請參閱如何:設定自訂的 WS 中繼資料交換](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)系[結, how to:透過非 MEX](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)系結取得中繼資料, 以及範例[自訂安全中繼資料端點](../../../wcf/samples/custom-secure-metadata-endpoint.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [如何：使用設定檔發佈服務的中繼資料](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [發行與擷取自訂繫結上的中繼資料](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [如何：設定自訂的 WS 中繼資料交換系結](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [如何：透過非 MEX 系結取得中繼資料](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [自訂安全中繼資料端點](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [中繼資料](../../../wcf/feature-details/metadata.md)
- [繫結](../../../wcf/bindings.md)
- [設定系統提供的繫結](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [使用繫結設定服務與用戶端](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
