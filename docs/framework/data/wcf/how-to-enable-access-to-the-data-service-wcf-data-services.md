---
title: 作法：啟用資料服務的存取 (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 82b2ec9313c6e0d4b9fa05862209a3ea838f31fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918614"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>作法：啟用資料服務的存取 (WCF Data Services)
在 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 中，您必須明確授與資料服務所公開之資源的存取權。 這表示當您建立新的資料服務之後，您仍然必須明確提供個別資源的存取權當做實體集。 本主題說明如何在您完成[快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)時所建立的 Northwind 資料服務中, 啟用五個實體集的讀取和寫入存取權。 因為 <xref:System.Data.Services.EntitySetRights> 列舉的定義方式是透過使用 <xref:System.FlagsAttribute>，所以您可以使用邏輯 OR 運算子為單一實體集指定多個權限。  
  
> [!NOTE]
> 任何可以存取 ASP.NET 應用程式的用戶端也可以存取資料服務公開的資源。 在實際執行的資料服務中，若要避免未經授權存取資源，您也應該要保護應用程式本身的安全。 如需詳細資訊, 請參閱[保護 ASP.NET 網站](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100))。  
  
### <a name="to-enable-access-to-the-data-service"></a>啟用存取資料服務  
  
- 在資料服務的程式碼中，以下列程式碼取代 `InitializeService` 函數中的預留位置程式碼：  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     如此可讓用戶端具有 `Orders` 和 `Order_Details` 實體集的讀取和寫入存取權，並擁有 `Customers` 實體集的唯讀存取權。  
  
## <a name="see-also"></a>另請參閱

- [如何：開發在 IIS 上執行的 WCF 資料服務](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)
- [設定資料服務](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
