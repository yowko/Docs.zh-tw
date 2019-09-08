---
title: 作法：使用 Entity Framework 提供者（WCF Data Services）自訂摘要
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
ms.openlocfilehash: 8f994065ea42d6fc522fa297cafa8c46a8164e67
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780159"
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>HOW TO：使用 Entity Framework 提供者（WCF Data Services）自訂摘要
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可讓您自訂資料服務回應中的 Atom 序列化，因此可以將實體的屬性對應至在 AtomPub 通訊協定中定義的未使用項目。 本主題說明如何使用 Entity Framework 提供者，針對資料模型中於 .edmx 檔中定義的實體類型定義對應屬性。 如需詳細資訊，請參閱摘要[自訂](feed-customization-wcf-data-services.md)。  
  
 在本主題中，您將手動修改工具產生的 .edmx 檔 (其中包含資料模型)。 您必須手動修改此檔案，因為 Entity Designer 不支援資料模型的副檔名。 如需實體資料模型工具產生之 .edmx 檔案的詳細資訊，請參閱[.edmx 檔案總覽（Entity Framework）](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))。 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成[WCF Data Services 快速入門](quickstart-wcf-data-services.md)時，會建立此服務和用戶端資料類別。  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>手動修改 Northwind.edmx 檔以加入摘要自訂屬性  
  
1. 在**方案總管**中，以滑鼠右鍵`Northwind.edmx`按一下檔案，然後按一下 [**開啟方式**]。  
  
2. 在 [**開啟方式-Northwind .edmx** ] 對話方塊中，選取 [ **XML 編輯器**]，然後按一下 **[確定]** 。  
  
3. 找出 `ConceptualModels` 項目，並以下列包含摘要自訂對應屬性的項目取代現有的 `Customers` 實體類型：  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4. 儲存變更並關閉 Northwind.edmx 檔。  
  
5. 選擇性以滑鼠右鍵按一下 [Northwind] 檔案，然後按一下 [**執行自訂工具**]。  
  
     這樣將會重新產生您可能需要的物件層檔案。  
  
6. 重新編譯專案。  
  
## <a name="example"></a>範例  
 上一個範例會傳回以下 URI `http://myservice/Northwind.svc/Customers('ALFKI')` 的結果。  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## <a name="see-also"></a>另請參閱

- [Entity Framework 提供者](entity-framework-provider-wcf-data-services.md)
