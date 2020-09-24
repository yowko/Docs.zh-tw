---
title: HOW TO：啟用資料服務的存取 (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 62622a5788a735497a6869c114c572e947067449
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155415"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="3166e-102">HOW TO：啟用資料服務的存取 (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="3166e-102">How to: Enable Access to the Data Service (WCF Data Services)</span></span>

<span data-ttu-id="3166e-103">在 WCF Data Services 中，您必須明確地授與資料服務所公開之資源的存取權。</span><span class="sxs-lookup"><span data-stu-id="3166e-103">In WCF Data Services, you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="3166e-104">這表示當您建立新的資料服務之後，您仍然必須明確提供個別資源的存取權當做實體集。</span><span class="sxs-lookup"><span data-stu-id="3166e-104">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="3166e-105">本主題說明如何在完成 [快速入門](quickstart-wcf-data-services.md)時所建立的 Northwind 資料服務中，啟用五個實體集的讀取和寫入存取權。</span><span class="sxs-lookup"><span data-stu-id="3166e-105">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="3166e-106">因為 <xref:System.Data.Services.EntitySetRights> 列舉的定義方式是透過使用 <xref:System.FlagsAttribute>，所以您可以使用邏輯 OR 運算子為單一實體集指定多個權限。</span><span class="sxs-lookup"><span data-stu-id="3166e-106">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3166e-107">任何可以存取 ASP.NET 應用程式的用戶端也可以存取資料服務公開的資源。</span><span class="sxs-lookup"><span data-stu-id="3166e-107">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="3166e-108">在實際執行的資料服務中，若要避免未經授權存取資源，您也應該要保護應用程式本身的安全。</span><span class="sxs-lookup"><span data-stu-id="3166e-108">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="3166e-109">如需詳細資訊，請參閱 [保護 ASP.NET 的網站](/previous-versions/aspnet/91f66yxt(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="3166e-109">For more information, see [Securing ASP.NET Web Sites](/previous-versions/aspnet/91f66yxt(v=vs.100)).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="3166e-110">啟用存取資料服務</span><span class="sxs-lookup"><span data-stu-id="3166e-110">To enable access to the data service</span></span>  
  
- <span data-ttu-id="3166e-111">在資料服務的程式碼中，以下列程式碼取代 `InitializeService` 函數中的預留位置程式碼：</span><span class="sxs-lookup"><span data-stu-id="3166e-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="3166e-112">如此可讓用戶端具有 `Orders` 和 `Order_Details` 實體集的讀取和寫入存取權，並擁有 `Customers` 實體集的唯讀存取權。</span><span class="sxs-lookup"><span data-stu-id="3166e-112">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3166e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3166e-113">See also</span></span>

- [<span data-ttu-id="3166e-114">作法：開發在 IIS 上執行的 WCF 資料服務</span><span class="sxs-lookup"><span data-stu-id="3166e-114">How to: Develop a WCF Data Service Running on IIS</span></span>](how-to-develop-a-wcf-data-service-running-on-iis.md)
- [<span data-ttu-id="3166e-115">設定資料服務</span><span class="sxs-lookup"><span data-stu-id="3166e-115">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
