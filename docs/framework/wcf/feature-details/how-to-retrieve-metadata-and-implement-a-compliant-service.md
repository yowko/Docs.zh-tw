---
title: HOW TO：擷取中繼資料並實作相容性服務
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: 6bd67ec8dcc0e73d097796b44974dce00b9a4eb2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601214"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>HOW TO：擷取中繼資料並實作相容性服務
服務通常不會由同一個人設計並實作。 在重視應用程式之間互通性的環境中，可以使用 Web 服務描述語言 (WSDL) 來設計或描述合約，而開發人員則必須實作符合所提供合約的服務。 您可能也會想要將現有的服務遷移至 Windows Communication Foundation （WCF），但保留電傳格式。 此外，雙工合約還會要求呼叫端也必須實作回呼合約。  
  
 在這些情況下，您必須使用[System.servicemodel 中繼資料公用程式工具（Svcutil）](../servicemodel-metadata-utility-tool-svcutil-exe.md) （或對等工具），以您可以執行以滿足合約需求的 managed 語言來產生服務合約介面。 通常會使用[System.servicemodel 中繼資料公用程式工具（Svcutil）](../servicemodel-metadata-utility-tool-svcutil-exe.md)來取得與通道處理站或 WCF 用戶端類型，以及設定正確系結和位址的用戶端設定檔所搭配使用的服務合約。 若要使用產生的組態檔，您必須將它變更為服務組態檔。 您可能還需要修改服務合約。  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>若要擷取資料並實作相容服務  
  
1. 對中繼資料檔案或中繼資料端點使用[System.servicemodel 中繼資料公用程式工具（Svcutil）](../servicemodel-metadata-utility-tool-svcutil-exe.md) ，以產生程式碼檔案。  
  
2. 搜尋輸出程式碼檔案中包含標示有 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 屬性之所需介面 (如果有一個以上) 的部分。 下列程式碼範例顯示[System.servicemodel 中繼資料公用程式工具（Svcutil）](../servicemodel-metadata-utility-tool-svcutil-exe.md)所產生的兩個介面。 第一個 (`ISampleService`) 是您為了建立相容服務而實作的服務合約介面。 第二個 (`ISampleServiceChannel`) 是供用戶端使用的 Helper 介面，這個介面會擴充服務合約介面及 <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>，而且可以在用戶端應用程式中使用。  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3. 如果 WSDL 沒有為所有的作業指定回覆動作，則產生的作業合約可能會將 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 屬性設定為萬用字元 (*)。 請移除這個屬性設定。 否則，當您實作服務合約中繼資料時，就無法匯出這些作業的中繼資料。  
  
4. 在類別上實作介面並裝載服務。 如需範例，請參閱範例一節中的[如何：執行服務合約](../how-to-implement-a-wcf-contract.md)或查看下列簡單的執行方式。  
  
5. 在 [配置[中繼資料公用程式工具（Svcutil）](../servicemodel-metadata-utility-tool-svcutil-exe.md) ] 產生的用戶端設定檔中，將 [設定] 區段變更為 [設定] [\<client>](../../configure-apps/file-schema/wcf/client.md) [\<services>](../../configure-apps/file-schema/wcf/services.md) 區段。 (如需所產生之用戶端應用程式組態檔的範例，請參閱下列＜範例＞一節)。  
  
6. 在 [設定] [\<services>](../../configure-apps/file-schema/wcf/services.md) 區段內，于 `name` 服務執行的 [設定] 區段中建立屬性 [\<services>](../../configure-apps/file-schema/wcf/services.md) 。  
  
7. 將服務的 `name` 屬性設定為服務實作的組態名稱。  
  
8. 將使用實作服務合約的端點組態項目加入至服務組態區段。  
  
## <a name="example"></a>範例  
 下列程式碼範例顯示透過對中繼資料檔案執行[System.servicemodel 中繼資料公用程式工具（Svcutil）](../servicemodel-metadata-utility-tool-svcutil-exe.md)所產生的大部分程式碼檔案。  
  
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
  
## <a name="see-also"></a>請參閱

- [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
