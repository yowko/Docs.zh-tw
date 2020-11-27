---
title: 發行與擷取自訂繫結上的中繼資料
ms.date: 03/30/2017
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
ms.openlocfilehash: 2c88ab92bb9cbe2fc07240d0934d246fa4de5cc0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262758"
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>發行與擷取自訂繫結上的中繼資料

<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> 提供新增中繼資料端點到服務的支援。 這些中繼資料端點可以在具有查詢字串的 URL 上回應 HTTP GET 要求 `?wsdl` ，並在 WS-MetadataExchange (MEX) 規格中定義 WS-Transfer get 要求。 MEX 端點會實作 <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> 合約。  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>發行自訂繫結上的中繼資料  

 只要將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> 或 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> 屬性設定為 `true`，便可啟用 HTTP GET 中繼資料端點和 HTTPS GET 中繼資料端點。 這些端點的繫結無法設定。  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>不過，合約可搭配任何端點使用，包括使用自訂系結的端點，因為 <xref:System.ServiceModel.Description.IMetadataExchange> 端點與任何其他 WINDOWS COMMUNICATION FOUNDATION (WCF) 服務端點相同。 如果您知道如何修改系統提供之繫結的組態，或者知道如何設定 <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>，則可設定繫結以搭配 <xref:System.ServiceModel.Description.IMetadataExchange> 端點使用。  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>擷取自訂繫結上的中繼資料  

 您可以使用標準 HTTP 或 HTTPS GET 要求，從 HTTP Get 與 HTTPS Get 中繼資料端點擷取中繼資料。  
  
 若要從 MEX 中繼資料端點取出中繼資料，您通常可以使用 WCF 所支援的其中一個標準 MEX 系結。 如需詳細資訊，請參閱<xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>。 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> 型別與 Svcutil.exe 工具會根據指定中繼資料端點的位址，自動選取其中一個標準 MEX 繫結。  
  
 如果 MEX 中繼資料端點使用的繫結異於其中一個標準 MEX 繫結，您可以使用程式碼或提供 <xref:System.ServiceModel.Description.MetadataExchangeClient> 用戶端端點組態，設定 <xref:System.ServiceModel.Description.IMetadataExchange> 所使用的繫結。 Svcutil.exe 工具會自動從其組態檔載入 <xref:System.ServiceModel.Description.IMetadataExchange> 用戶端端點組態，此組態與中繼資料端點位址之 URI 配置的名稱相同。  
  
## <a name="security"></a>安全性  

 發行自訂繫結上的中繼資料時，繫結務必要提供您中繼資料所需的安全性支援。 例如，若要避免資訊洩漏，並且確定您的用戶端有權限可取得中繼資料，您可將 <xref:System.ServiceModel.Description.IMetadataExchange> 端點設為需要驗證和加密，讓中繼資料和應用程式更安全。 [自訂安全中繼資料端點](../samples/custom-secure-metadata-endpoint.md)範例會示範此案例。  
  
## <a name="see-also"></a>另請參閱

- [保護服務的安全](../securing-services.md)
- [WS-MetadataExchange 繫結](ws-metadataexchange-bindings.md)
- [作法：設定自訂 WS-Metadata Exchange 繫結](how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [作法：透過非 MEX 繫結擷取中繼資料](how-to-retrieve-metadata-over-a-non-mex-binding.md)
