---
title: HOW TO：使用 MetadataExchangeClient 來擷取中繼資料
ms.date: 03/30/2017
ms.assetid: 0754e9dc-13c5-45c2-81b5-f3da466e5a87
ms.openlocfilehash: 32acef65ee30d7b80b37c11bdd024e3c09a935ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038762"
---
# <a name="how-to-use-metadataexchangeclient-to-retrieve-metadata"></a>HOW TO：使用 MetadataExchangeClient 來擷取中繼資料
使用 <xref:System.ServiceModel.Description.MetadataExchangeClient> 類別，即可使用 WS-MetadataExchange (MEX) 通訊協定來下載中繼資料。 所擷取的中繼資料檔案會當做 <xref:System.ServiceModel.Description.MetadataSet> 物件傳回。 傳回的 <xref:System.ServiceModel.Description.MetadataSet> 物件包含 <xref:System.ServiceModel.Description.MetadataSection> 物件的集合，其中每一個都會包含特定的中繼資料方言和識別項。 您可以將傳回的中繼資料寫入至檔案，或者當傳回的中繼資料含有 Web 服務描述語言 (WSDL) 文件時，您便可以使用 <xref:System.ServiceModel.Description.WsdlImporter> 來匯入中繼資料。  
  
 接受位址的 <xref:System.ServiceModel.Description.MetadataExchangeClient> 建構函式 (Constructor)，而這種建構函式會使用符合該位址之統一資源識別項 (URI) 配置之 <xref:System.ServiceModel.Description.MetadataExchangeBindings> 靜態類別上的繫結。 或者，您也可以使用允許明確指定要使用之繫結的 <xref:System.ServiceModel.Description.MetadataExchangeClient> 建構函式。 指定的繫結可用來解析所有的中繼資料參考。  
  
 就像任何其他 Windows Communication Foundation (WCF) 用戶端<xref:System.ServiceModel.Description.MetadataExchangeClient>類型提供的建構函式來載入用戶端端點組態使用的端點組態名稱。 指定的端點組態必須指定 <xref:System.ServiceModel.Description.IMetadataExchange> 合約。 在端點組態中的位址並不會載入，因此您必須使用會接收位址的其中一個 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> 多載。 當您使用 <xref:System.ServiceModel.EndpointAddress> 執行個體指定中繼資料位址時，<xref:System.ServiceModel.Description.MetadataExchangeClient> 會假設該位址指向 MEX 端點。 如果指定中繼資料位址做為 URL，您就必須同時指定要使用的 <xref:System.ServiceModel.Description.MetadataExchangeClientMode> 為 MEX 或 HTTP GET。  
  
> [!IMPORTANT]
>  根據預設，<xref:System.ServiceModel.Description.MetadataExchangeClient> 會解析您所有的參考，包括 WSDL 和 XML 結構描述 Import 和 Include。 您可以透過將 <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> 屬性設定為 `false`，停用這項功能。 您可以使用 <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> 屬性來控制要解析之參考的最大數目。 您可以使用此屬性配合繫結上的 `MaxReceivedMessageSize` 屬性來控制要擷取的中繼資料數目。  
  
### <a name="to-use-metadataexchangeclient-to-obtain-metadata"></a>使用 MetadataExchangeClient 來擷取中繼資料  
  
1. 透過明確指定繫結、端點組態名稱或中繼資料位址的方式，即可建立新的 <xref:System.ServiceModel.Description.MetadataExchangeClient> 物件。  
  
2. 視您的需要設定 <xref:System.ServiceModel.Description.MetadataExchangeClient>。 例如，您可以指定在要求中繼資料時所要使用的認證、控制中繼資料的解析方式，以及設定 <xref:System.ServiceModel.Description.MetadataExchangeClient.OperationTimeout%2A> 屬性來控制中繼資料要求必須在逾時前多久傳回。  
  
3. 取得 <xref:System.ServiceModel.Description.MetadataSet> 物件，這個物件包含透過呼叫其中一個 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> 方法而擷取到的中繼資料。 請注意，如果已經在建構 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> 時明確指定了位址，您就只能使用不接受任何引數的 <xref:System.ServiceModel.Description.MetadataExchangeClient> 多載。  
  
## <a name="example"></a>範例  
 下列程式碼範例會示範如何使用 <xref:System.ServiceModel.Description.MetadataExchangeClient> 來下載並列舉中繼資料檔案。  

 [!code-csharp[MetadataResolver#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/metadataresolver/cs/client.cs#3)]  

## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯這個程式碼範例，您必須參考 System.ServiceModel.dll 組件並匯入 <xref:System.ServiceModel.Description> 命名空間 (Namespace)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Description.MetadataResolver>
- <xref:System.ServiceModel.Description.MetadataExchangeClient>
- <xref:System.ServiceModel.Description.WsdlImporter>
