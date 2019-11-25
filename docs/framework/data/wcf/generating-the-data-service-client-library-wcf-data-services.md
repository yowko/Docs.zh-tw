---
title: 產生資料服務用戶端程式庫 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: f73ea93fe76f31c81935dbfb29183c247e41d8cd
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975277"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="20095-102">產生資料服務用戶端程式庫 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="20095-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="20095-103">執行開放式資料通訊協定（OData）的資料服務可以傳回服務元資料檔案，其中描述 OData 摘要所公開的資料模型。</span><span class="sxs-lookup"><span data-stu-id="20095-103">A data service that implements the Open Data Protocol (OData) can return a service metadata document that describes the data model exposed by the OData feed.</span></span> <span data-ttu-id="20095-104">如需詳細資訊，請參閱[OData：服務元資料檔案](https://go.microsoft.com/fwlink/?LinkId=186070)。</span><span class="sxs-lookup"><span data-stu-id="20095-104">For more information, see [OData: Service Metadata Document](https://go.microsoft.com/fwlink/?LinkId=186070).</span></span> <span data-ttu-id="20095-105">您可以使用 Visual Studio 中的 [**加入服務參考**] 對話方塊，將參考新增至以 OData 為基礎的服務。</span><span class="sxs-lookup"><span data-stu-id="20095-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an OData-based service.</span></span> <span data-ttu-id="20095-106">當您使用此工具將參考加入至用戶端專案中 OData 摘要所傳回的中繼資料時，它會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="20095-106">When you use this tool to add a reference to the metadata returned by an OData feed in a client project, it performs the following actions:</span></span>  
  
- <span data-ttu-id="20095-107">要求資料服務中的服務中繼資料文件，然後解譯傳回的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="20095-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="20095-108">傳回的中繼資料會以 .edmx 檔案形式儲存在用戶端專案中。</span><span class="sxs-lookup"><span data-stu-id="20095-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="20095-109">這個 .edmx 檔案不能使用實體資料模型設計工具開啟，因為它的格式與 Entity Framework 使用的 .edmx 檔案格式不同。</span><span class="sxs-lookup"><span data-stu-id="20095-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="20095-110">您可以使用 XML 編輯器或任何文字編輯器檢視此中繼資料。</span><span class="sxs-lookup"><span data-stu-id="20095-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="20095-111">如需詳細資訊，請參閱[\[MC-EDMX\]：資料服務封裝格式](https://go.microsoft.com/fwlink/?LinkID=178833)規格的實體資料模型</span><span class="sxs-lookup"><span data-stu-id="20095-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](https://go.microsoft.com/fwlink/?LinkID=178833) specification</span></span>  
  
- <span data-ttu-id="20095-112">產生服務的表示，成為繼承自 <xref:System.Data.Services.Client.DataServiceContext> 的實體容器類別。</span><span class="sxs-lookup"><span data-stu-id="20095-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="20095-113">這樣產生的實體容器類別與實體資料模型工具產生的實體容器相似。</span><span class="sxs-lookup"><span data-stu-id="20095-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="20095-114">如需詳細資訊，請參閱[物件服務概觀 (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="20095-114">For more information, see [Object Services Overview (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).</span></span>  
  
- <span data-ttu-id="20095-115">針對在服務中繼資料中找到的資料模型型別產生資料類別。</span><span class="sxs-lookup"><span data-stu-id="20095-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
- <span data-ttu-id="20095-116">將參考加入至專案的 `System.Data.Services.Client` 組件。</span><span class="sxs-lookup"><span data-stu-id="20095-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="20095-117">如需詳細資訊，請參閱[如何：加入資料服務參考](how-to-add-a-data-service-reference-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="20095-117">For more information, see [How to: Add a Data Service Reference](how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="20095-118">您也可以在命令提示字元中使用[DataSvcUtil](wcf-data-service-client-utility-datasvcutil-exe.md)來產生用戶端資料服務類別。</span><span class="sxs-lookup"><span data-stu-id="20095-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="20095-119">如需詳細資訊，請參閱[如何：手動產生用戶端資料服務類別](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="20095-119">For more information, see [How to: Manually Generate Client Data Service Classes](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="20095-120">用戶端資料型別對應</span><span class="sxs-lookup"><span data-stu-id="20095-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="20095-121">當您使用 Visual Studio 或 `DataSvcUtil.exe` 工具中的 [**加入服務參考**] 對話方塊來產生以 OData 摘要為基礎的用戶端資料類別時，.NET Framework 資料類型會對應至資料模型中的基本類型，如下所示：</span><span class="sxs-lookup"><span data-stu-id="20095-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an OData feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="20095-122">資料模型型別</span><span class="sxs-lookup"><span data-stu-id="20095-122">Data model type</span></span>|<span data-ttu-id="20095-123">.NET Framework 資料型別</span><span class="sxs-lookup"><span data-stu-id="20095-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="20095-124"><xref:System.Byte> `[]`</span><span class="sxs-lookup"><span data-stu-id="20095-124"><xref:System.Byte> `[]`</span></span>|  
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
  
 <span data-ttu-id="20095-125">如需詳細資訊，請參閱[OData：基本資料類型](https://go.microsoft.com/fwlink/?LinkId=186072)。</span><span class="sxs-lookup"><span data-stu-id="20095-125">For more information, see [OData: Primitive Data Types](https://go.microsoft.com/fwlink/?LinkId=186072).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20095-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="20095-126">See also</span></span>

- [<span data-ttu-id="20095-127">WCF Data Services 用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="20095-127">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
- [<span data-ttu-id="20095-128">快速入門</span><span class="sxs-lookup"><span data-stu-id="20095-128">Quickstart</span></span>](quickstart-wcf-data-services.md)
