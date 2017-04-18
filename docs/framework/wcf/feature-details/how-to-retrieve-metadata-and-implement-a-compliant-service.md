---
title: "HOW TO：擷取中繼資料並實作相容性服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# HOW TO：擷取中繼資料並實作相容性服務
服務通常不會由同一個人設計並實作。 在重視應用程式之間互通性的環境中，可以使用 Web 服務描述語言 (WSDL) 來設計或描述合約，而開發人員則必須實作符合所提供合約的服務。 您也可能想要將現有服務移轉至 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]，但是保留 Wire 格式。 此外，雙工合約還會要求呼叫端也必須實作回呼合約。  
  
 在這些情況下，您必須使用[ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) （或對等的工具） 來產生服務合約介面在 managed 語言中，您可以實作以滿足需求的合約。 通常[ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)可用來取得與通道處理站使用的服務合約或[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]連同用戶端組態檔，以設定正確的繫結和位址的用戶端類型。 若要使用產生的組態檔，您必須將它變更為服務組態檔。 您可能還需要修改服務合約。  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>若要擷取資料並實作相容服務  
  
1.  使用[ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)對中繼資料檔案或產生的程式碼檔案的中繼資料端點。  
  
2.  搜尋輸出程式碼檔案，其中包含感興趣的 （如果有一個以上） 介面都會標示的部分<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=fullName>屬性。 下列程式碼範例顯示所產生的兩個介面[ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 第一個 (`ISampleService`) 是您為了建立相容服務而實作的服務合約介面。 第二個 (`ISampleServiceChannel`) 是供擴充服務合約介面的用戶端使用的 helper 介面和<xref:System.ServiceModel.IClientChannel?displayProperty=fullName>而且可供用戶端應用程式中使用。  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3.  如果 WSDL 沒有指定的所有作業的回覆動作，產生的作業合約可能<xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A>屬性設定為萬用字元 （*）。 請移除這個屬性設定。 否則，當您實作服務合約中繼資料時，就無法匯出這些作業的中繼資料。  
  
4.  在類別上實作介面並裝載服務。 如需範例，請參閱[How to︰ 實作服務合約](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)，或請參閱下面範例 > 一節中的簡單實作。  
  
5.  在用戶端組態檔中的[ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)產生時，變更[ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/client.md)的組態區段[ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)組態區段。 (如需所產生之用戶端應用程式組態檔的範例，請參閱下列＜範例＞一節)。  
  
6.  內[ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)組態區段中，建立`name`屬性中[ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)服務實作的組態區段。  
  
7.  將服務的 `name` 屬性設定為服務實作的組態名稱。  
  
8.  將使用實作服務合約的端點組態項目加入至服務組態區段。  
  
## <a name="example"></a>範例  
 下列程式碼範例會顯示大部分的執行所產生的程式碼檔案[ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)依據中繼資料檔案。  
  
 下列程式碼顯示：  
  
-   服務合約介面，這個介面會在實作之後符合合約需求 (`ISampleService`)。  
  
-   擴充服務合約介面的用戶端使用的 helper 介面和<xref:System.ServiceModel.IClientChannel?displayProperty=fullName>而且可供用戶端應用程式中使用 (`ISampleServiceChannel`)。  
  
-   擴充的協助程式類別<xref:System.ServiceModel.ClientBase%601?displayProperty=fullName>而且可供用戶端應用程式中使用 (`SampleServiceClient`)。  
  
-   從服務產生的組態檔。  
  
-   簡易 `ISampleService` 服務實作。  
  
-   用戶端組態檔轉換為服務端版。  
  
 [!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]  
  
 [!code[ClientProxyCodeSample#10](../../../../samples/snippets/common/VS_Snippets_CFX/clientproxycodesample/common/client.exe.config#10)]
 [!code-csharp[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]  
  
 [!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]  
  
 [!code[ClientProxyCodeSample#20](../../../../samples/snippets/common/VS_Snippets_CFX/clientproxycodesample/common/hostapplication.exe.config#20)]
 [!code-csharp[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]  
  
## <a name="see-also"></a>另請參閱  
 [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)