---
title: "如何：自訂搭配 Entity Framework 提供者使用的摘要 (WCF 資料服務)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 44dfa0a8371ff8184462e15da71f8a9f0f9767d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>如何：自訂搭配 Entity Framework 提供者使用的摘要 (WCF 資料服務)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可讓您自訂資料服務回應中的 Atom 序列化，因此可以將實體的屬性對應至在 AtomPub 通訊協定中定義的未使用項目。 本主題說明如何使用 Entity Framework 提供者，針對資料模型中於 .edmx 檔中定義的實體類型定義對應屬性。 如需詳細資訊，請參閱[摘要自訂](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)。  
  
 在本主題中，您將手動修改工具產生的 .edmx 檔 (其中包含資料模型)。 您必須手動修改此檔案，因為 Entity Designer 不支援資料模型的副檔名。 如需 Entity Data Model 工具產生的.edmx 檔案的詳細資訊，請參閱[.edmx 檔案概觀](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)。 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成建立此服務和用戶端資料類別[WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>手動修改 Northwind.edmx 檔以加入摘要自訂屬性  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下`Northwind.edmx`檔案，然後再按一下**開啟**。  
  
2.  在**開啟方式-Northwind.edmx**對話方塊中，選取**XML 編輯器**，然後按一下 **確定**。  
  
3.  找出 `ConceptualModels` 項目，並以下列包含摘要自訂對應屬性的項目取代現有的 `Customers` 實體類型：  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4.  儲存變更並關閉 Northwind.edmx 檔。  
  
5.  （選擇性）以滑鼠右鍵按一下 Northwind.edmx 檔，然後按一下 **執行自訂工具**。  
  
     這樣將會重新產生您可能需要的物件層檔案。  
  
6.  重新編譯專案。  
  
## <a name="example"></a>範例  
 上一個範例會傳回以下 URI `http://myservice/``Northwind.svc/Customers('ALFKI')` 的結果。  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## <a name="see-also"></a>另請參閱  
 [Entity Framework 提供者](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
