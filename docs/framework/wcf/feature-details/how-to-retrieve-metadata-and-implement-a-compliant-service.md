---
title: HOW TO：擷取中繼資料並實作相容性服務
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: 0a13d504b1c7c38ec13fee58c36913a75119271b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184865"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>HOW TO：擷取中繼資料並實作相容性服務
服務通常不會由同一個人設計並實作。 在重視應用程式之間互通性的環境中，可以使用 Web 服務描述語言 (WSDL) 來設計或描述合約，而開發人員則必須實作符合所提供合約的服務。 您可能還希望將現有服務遷移到 Windows 通信基礎 （WCF），但保留線格式。 此外，雙工合約還會要求呼叫端也必須實作回呼合約。  
  
 在這些情況下，您必須使用[ServiceModel 中繼資料實用程式工具 （Svcutil.exe）（](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)或等效工具）以託管語言生成服務協定介面，您可以實現該語言以滿足協定的要求。 通常[，ServiceModel 中繼資料實用程式工具 （Svcutil.exe）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)用於獲取與通道工廠或 WCF 用戶端類型以及設置正確綁定和位址的用戶端設定檔一起使用的服務協定。 若要使用產生的組態檔，您必須將它變更為服務組態檔。 您可能還需要修改服務合約。  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>若要擷取資料並實作相容服務  
  
1. 使用[服務模型中繼資料實用程式工具 （Svcutil.exe）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)針對元資料檔案或中繼資料終結點生成代碼檔。  
  
2. 搜尋輸出程式碼檔案中包含標示有 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 屬性之所需介面 (如果有一個以上) 的部分。 下面的代碼示例顯示了[服務模型中繼資料實用程式工具 （Svcutil.exe）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)生成的兩個介面。 第一個 (`ISampleService`) 是您為了建立相容服務而實作的服務合約介面。 第二個 (`ISampleServiceChannel`) 是供用戶端使用的 Helper 介面，這個介面會擴充服務合約介面及 <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>，而且可以在用戶端應用程式中使用。  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3. 如果 WSDL 沒有為所有的作業指定回覆動作，則產生的作業合約可能會將 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 屬性設定為萬用字元 (*)。 請移除這個屬性設定。 否則，當您實作服務合約中繼資料時，就無法匯出這些作業的中繼資料。  
  
4. 在類別上實作介面並裝載服務。 例如，請參閱[如何：實現服務協定](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)，或請參閱下面的示例部分中的簡單實現。  
  
5. 在[ServiceModel 中繼資料實用程式工具 （Svcutil.exe）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)生成的用戶端設定檔中，將[\<用戶端>](../../../../docs/framework/configure-apps/file-schema/wcf/client.md)配置部分更改為[\<服務>](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)配置部分。 (如需所產生之用戶端應用程式組態檔的範例，請參閱下列＜範例＞一節)。  
  
6. 在[\<服務>](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)配置部分中，在[\<服務>](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)配置部分中為服務實現創建屬性。 `name`  
  
7. 將服務的 `name` 屬性設定為服務實作的組態名稱。  
  
8. 將使用實作服務合約的端點組態項目加入至服務組態區段。  
  
## <a name="example"></a>範例  
 以下代碼示例顯示了通過針對元資料檔案運行[ServiceModel 中繼資料實用程式工具 （Svcutil.exe）](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)生成的大多數代碼檔。  
  
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
