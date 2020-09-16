---
title: 產生資料服務用戶端程式庫 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: a6a388f837d00d63a39212843c3fa88b28482b26
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545803"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>產生資料服務用戶端程式庫 (WCF 資料服務)
開放式資料通訊協定 (OData) 的資料服務可以傳回服務元資料檔案，其中描述 OData 摘要所公開的資料模型。 如需詳細資訊，請參閱 [OData：總覽](https://www.odata.org/documentation/odata-version-2-0/overview/) 文章中的「服務元資料檔案」一節。 您可以使用 Visual Studio 中的 [ **加入服務參考** ] 對話方塊，將參考加入至以 OData 為基礎的服務。 當您使用此工具，將參考新增至用戶端專案中 OData 摘要所傳回的中繼資料時，它會執行下列動作：  
  
- 要求資料服務中的服務中繼資料文件，然後解譯傳回的中繼資料。  
  
    > [!NOTE]
    > 傳回的中繼資料會以 .edmx 檔案形式儲存在用戶端專案中。 這個 .edmx 檔案不能使用實體資料模型設計工具開啟，因為它的格式與 Entity Framework 使用的 .edmx 檔案格式不同。 您可以使用 XML 編輯器或任何文字編輯器檢視此中繼資料。 如需詳細資訊，請參閱[ \[ MC-EDMX \] ：適用于資料服務封裝格式的實體資料模型](/openspecs/windows_protocols/mc-edmx/5dff5e25-56a1-408b-9d44-bff6634c7d16)。
  
- 產生服務的表示，成為繼承自 <xref:System.Data.Services.Client.DataServiceContext> 的實體容器類別。 這樣產生的實體容器類別與實體資料模型工具產生的實體容器相似。 如需詳細資訊，請參閱[物件服務概觀 (Entity Framework)](/previous-versions/bb386871(v=vs.100))。  
  
- 針對在服務中繼資料中找到的資料模型型別產生資料類別。  
  
- 將參考加入至專案的 `System.Data.Services.Client` 組件。  
  
 如需詳細資訊，請參閱 [如何：加入資料服務參考](how-to-add-a-data-service-reference-wcf-data-services.md)。  
  
 您也可以在命令提示字元使用 [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) 工具來產生用戶端資料服務類別。 如需詳細資訊，請參閱 [如何：手動產生用戶端資料服務類別](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)。  
  
## <a name="client-data-type-mapping"></a>用戶端資料型別對應  
 當您使用 Visual Studio 或工具中的 [ **加入服務參考** ] 對話方塊 `DataSvcUtil.exe` 來產生以 OData 摘要為基礎的用戶端資料類別時，.NET Framework 資料類型會對應至資料模型中的基本型別，如下所示：  
  
|資料模型型別|.NET Framework 資料類型|  
|---------------------|------------------------------|  
|`Edm.Binary`|<xref:System.Byte> `[]`|  
|`Edm.Boolean`|<xref:System.Boolean>|  
|`Edm.Byte`|<xref:System.Byte>|  
|`Edm.DateTime`|<xref:System.DateTime>|  
|`Edm.Decimal`|<xref:System.Decimal>|  
|`Edm.Double`|<xref:System.Double>|  
|`Edm.Guid`|<xref:System.Guid>|  
|`Edm.Int16`|<xref:System.Int16>|  
|`Edm.Int32`|<xref:System.Int32>|  
|`Edm.Int64`|<xref:System.Int64>|  
|`Edm.SByte`|<xref:System.SByte>|  
|`Edm.Single`|<xref:System.Single>|  
|`Edm.String`|<xref:System.String>|  
  
 如需詳細資訊，請參閱 [OData：總覽](https://www.odata.org/documentation/odata-version-2-0/overview/) 文章中的基本資料類型一節。
  
## <a name="see-also"></a>另請參閱

- [WCF 資料服務用戶端程式庫](wcf-data-services-client-library.md)
- [快速入門](quickstart-wcf-data-services.md)
