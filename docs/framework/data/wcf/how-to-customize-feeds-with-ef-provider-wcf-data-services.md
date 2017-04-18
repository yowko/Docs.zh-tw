---
title: "HOW TO：透過 Entity Framework 提供者自訂摘要 (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, 自訂"
  - "WCF Data Services, 自訂摘要"
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# HOW TO：透過 Entity Framework 提供者自訂摘要 (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可讓您自訂資料服務回應中的 Atom 序列化，因此可以將實體的屬性對應至在 AtomPub 通訊協定中定義的未使用項目。  本主題說明如何使用 Entity Framework 提供者，針對資料模型中於 .edmx 檔中定義的實體類型定義對應屬性。  如需詳細資訊，請參閱[摘要自訂](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)。  
  
 在本主題中，您將手動修改工具產生的 .edmx 檔 \(其中包含資料模型\)。  您必須手動修改此檔案，因為 Entity Designer 不支援資料模型的副檔名。  如需實體資料模型工具產生之 .edmx 檔案的詳細資訊，請參閱 [.edmx File Overview](http://msdn.microsoft.com/zh-tw/f4c8e7ce-1db6-417e-9759-15f8b55155d4)。  本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。  此服務和用戶端資料類別會在您完成 [WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)時建立。  
  
### 手動修改 Northwind.edmx 檔以加入摘要自訂屬性  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 `Northwind.edmx` 檔案，然後按一下 \[**開啟方式**\]。  
  
2.  選取 \[**開啟方式 \- Northwind.edmx**\] 對話方塊中的 \[**XML 編輯器**\]，然後按一下 \[**確定**\]。  
  
3.  找出 `ConceptualModels` 項目，並以下列包含摘要自訂對應屬性的項目取代現有的 `Customers` 實體類型：  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4.  儲存變更並關閉 Northwind.edmx 檔。  
  
5.  \(選擇性\) 以滑鼠右鍵按一下 Northwind.edmx 檔，然後按一下 \[**執行自訂工具**\]。  
  
     這樣將會重新產生您可能需要的物件層檔案。  
  
6.  重新編譯專案。  
  
## 範例  
 上一個範例會傳回下列 URI 結果`http://myservice/` `Northwind.svc/Customers('ALFKI')`。  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## 請參閱  
 [Entity Framework 提供者](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)