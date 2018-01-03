---
title: "產生資料服務用戶端程式庫 (WCF 資料服務)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6adbaafe170cf3f5398677d5df3b3d2ff0a95abe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a>產生資料服務用戶端程式庫 (WCF 資料服務)
資料服務可實作[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]可以傳回描述資料模型所公開服務中繼資料文件[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要。 如需詳細資訊，請參閱[OData： 服務中繼資料文件](http://go.microsoft.com/fwlink/?LinkId=186070)。 您可以使用**加入服務參考**將參考加入至 Visual Studio 中的對話方塊[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]為基礎的服務。 當您使用此工具將參考加入至所傳回的中繼資料[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要的用戶端專案中，執行下列動作：  
  
-   要求資料服務中的服務中繼資料文件，然後解譯傳回的中繼資料。  
  
    > [!NOTE]
    >  傳回的中繼資料會以 .edmx 檔案形式儲存在用戶端專案中。 這個 .edmx 檔案不能使用實體資料模型設計工具開啟，因為它的格式與 Entity Framework 使用的 .edmx 檔案格式不同。 您可以使用 XML 編輯器或任何文字編輯器檢視此中繼資料。 如需詳細資訊，請參閱[ \[MC-EDMX\]： 資料服務封裝格式的實體資料模型](http://go.microsoft.com/fwlink/?LinkID=178833)規格  
  
-   產生服務的表示，成為繼承自 <xref:System.Data.Services.Client.DataServiceContext> 的實體容器類別。 這樣產生的實體容器類別與實體資料模型工具產生的實體容器相似。 如需詳細資訊，請參閱[物件服務概觀 (Entity Framework)](http://msdn.microsoft.com/en-us/43014cf9-c9cb-4538-bfbb-197820b60038)。  
  
-   針對在服務中繼資料中找到的資料模型型別產生資料類別。  
  
-   將參考加入至專案的 `System.Data.Services.Client` 組件。  
  
 如需詳細資訊，請參閱[如何： 加入資料服務參考](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)。  
  
 也可以使用產生的用戶端資料服務類別[DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)在命令提示字元工具。 如需詳細資訊，請參閱[How to： 手動產生用戶端資料服務類別](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)。  
  
## <a name="client-data-type-mapping"></a>用戶端資料型別對應  
 當您使用**加入服務參考**Visual Studio 中的對話方塊或`DataSvcUtil.exe`工具來產生用戶端資料類別為基礎的[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要時，.NET Framework 資料型別會對應至從基本的類型資料模型，如下所示：  
  
|資料模型型別|.NET Framework 資料型別|  
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
  
 如需詳細資訊，請參閱[OData： 基本資料型別](http://go.microsoft.com/fwlink/?LinkId=186072)。  
  
## <a name="see-also"></a>請參閱  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
