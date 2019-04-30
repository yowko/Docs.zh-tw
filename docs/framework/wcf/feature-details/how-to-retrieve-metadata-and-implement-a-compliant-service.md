---
title: HOW TO：擷取中繼資料並實作相容性服務
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: edf8fe2f174202d19b075ec218f059ea9b988843
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000788"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>HOW TO：擷取中繼資料並實作相容性服務
服務通常不會由同一個人設計並實作。 在重視應用程式之間互通性的環境中，可以使用 Web 服務描述語言 (WSDL) 來設計或描述合約，而開發人員則必須實作符合所提供合約的服務。 您也可以將現有服務移轉至 Windows Communication Foundation (WCF)，但是保留 wire 格式。 此外，雙工合約還會要求呼叫端也必須實作回呼合約。  
  
 在這些情況下，您必須使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) （或對等的工具） 來產生服務合約介面在 managed 語言中，您可以實作以滿足的需求合約。 通常[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)可用來取得與通道處理站或 WCF 用戶端類型以及正確的繫結會設定用戶端組態檔使用的服務合約和地址。 若要使用產生的組態檔，您必須將它變更為服務組態檔。 您可能還需要修改服務合約。  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>若要擷取資料並實作相容服務  
  
1. 使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)針對中繼資料檔或產生的程式碼檔案的中繼資料端點。  
  
2. 搜尋輸出程式碼檔案中包含標示有 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 屬性之所需介面 (如果有一個以上) 的部分。 下列程式碼範例會顯示所產生的兩個介面[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 第一個 (`ISampleService`) 是您為了建立相容服務而實作的服務合約介面。 第二個 (`ISampleServiceChannel`) 是供用戶端使用的 Helper 介面，這個介面會擴充服務合約介面及 <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>，而且可以在用戶端應用程式中使用。  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3. 如果 WSDL 沒有為所有的作業指定回覆動作，則產生的作業合約可能會將 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 屬性設定為萬用字元 (*)。 請移除這個屬性設定。 否則，當您實作服務合約中繼資料時，就無法匯出這些作業的中繼資料。  
  
4. 在類別上實作介面並裝載服務。 如需範例，請參閱[如何：實作服務合約](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)，或請參閱下方範例 > 一節中的簡單實作。  
  
5. 在用戶端組態檔[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)產生時，變更[\<用戶端 >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md)的組態區段[ \<服務 >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)組態區段。 (如需所產生之用戶端應用程式組態檔的範例，請參閱下列＜範例＞一節)。  
  
6. 內[ \<services >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)組態區段中，建立`name`屬性中[\<服務 >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)組態區段，為您的服務實作。  
  
7. 將服務的 `name` 屬性設定為服務實作的組態名稱。  
  
8. 將使用實作服務合約的端點組態項目加入至服務組態區段。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範執行所產生的程式碼檔案的大部分[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)依據中繼資料檔案。  
  
 下列程式碼顯示：  
  
- 服務合約介面，這個介面會在實作之後符合合約需求 (`ISampleService`)。  
  
- 供用戶端使用的 Helper 介面，這個介面會擴充服務合約介面及 <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>，而且可以在用戶端應用程式中 (`ISampleServiceChannel`) 使用。  
  
- Helper 類別，這個類別會擴充 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>，而且可以在用戶端應用程式 (`SampleServiceClient`) 中使用。  
  
- 從服務產生的組態檔。  
  
- 簡易 `ISampleService` 服務實作。  
  
- 用戶端組態檔轉換為服務端版。  
  
[!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]

[!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]     

[!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]    

[!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]    
  
## <a name="see-also"></a>另請參閱

- [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
