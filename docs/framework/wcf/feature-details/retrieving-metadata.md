---
title: 擷取中繼資料
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], retrieving
ms.assetid: 18d8ba4c-af0f-4827-a50b-4202d767bacc
ms.openlocfilehash: 1f0665b4f0fb91b102ef1d5b75a5433992f5a6e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493597"
---
# <a name="retrieving-metadata"></a>擷取中繼資料
中繼資料擷取程序會要求和擷取中繼資料端點內的中繼資料，這些端點包括像是 WS-MetadataExchange (MEX) 中繼資料端點或 HTTP/GET 中繼資料端點。  
  
## <a name="retrieving-metadata-from-the-command-line-using-svcutilexe"></a>使用 Svcutil.exe 來從命令列擷取中繼資料  
 您可以擷取服務中繼資料使用 Ws-metadataexchange 或 HTTP/GET 要求來使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具，並傳遞`/target:metadata`交換器和位址。 Svcutil.exe 會在指定的位址下載中繼資料，並將檔案儲存到磁碟中。 Svcutil.exe 會在內部使用 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> 執行個體 (Instance)，而且會從 <xref:System.ServiceModel.Description.IMetadataExchange> 端點組態 (其名稱與傳遞至 Svcutil.exe 做為輸入的位址配置相同) 載入。  
  
## <a name="retrieving-metadata-programmatically-using-the-metadataexchangeclient"></a>使用 MetadataExchangeClient 來以程式設計方式擷取中繼資料  
 Windows Communication Foundation (WCF) 可以擷取使用標準化的通訊協定，像是 Ws-metadataexchange 和 HTTP/GET 要求的服務中繼資料。 這兩種通訊協定都由 <xref:System.ServiceModel.Description.MetadataExchangeClient> 型別所支援。 您可以藉由提供中繼資料端點的位址及選擇性繫結，來擷取使用 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> 型別的服務中繼資料。 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> 執行個體使用的繫結可以是以下預設繫結之一：<xref:System.ServiceModel.Description.MetadataExchangeBindings> 靜態類別、使用者提供的繫結，或是從 `IMetadataExchange` 合約的端點組態載入的繫結。 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> 也可以使用 <xref:System.Net.HttpWebRequest> 型別將 HTTP URL 參照解析為中繼資料。  
  
 根據預設，<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> 執行個體與單一的 <xref:System.ServiceModel.ChannelFactory> 執行個體有密切的關係。 您可以透過覆寫 <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> 虛擬方法，以變更或取代 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> 所使用的 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> 執行個體。 同樣地，您可以覆寫 <xref:System.Net.HttpWebRequest> 虛擬方法，以變更或取代由 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> 使用的 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> 執行個體。  
  
## <a name="in-this-section"></a>本節內容  
 [如何：使用 Svcutil.exe 來下載中繼資料文件](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)  
 判斷如何使用 Svcutil.exe 來下載中繼資料文件。  
  
 [如何：使用 MetadataResolver 來動態取得繫結中繼資料](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)  
 示範如何使用 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> 在執行階段動態地取得中繼資料。  
  
 [如何：使用 MetadataExchangeClient 來擷取中繼資料](../../../../docs/framework/wcf/feature-details/how-to-use-metadataexchangeclient-to-retrieve-metadata.md)  
 示範如何使用 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> 類別將中繼資料檔案下載到包含 <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> 物件的 <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> 物件，以供寫入至檔案或其他用途。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Description.MetadataExchangeClient>
