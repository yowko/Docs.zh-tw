---
title: 定義 WCF 資料服務
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
ms.openlocfilehash: ac75f5fd91f68d9403dc7b42325bf8970f0c6794
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765644"
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="87104-102">定義 WCF 資料服務</span><span class="sxs-lookup"><span data-stu-id="87104-102">Defining WCF Data Services</span></span>

<span data-ttu-id="87104-103">本節說明如何建立和設定將資料公開為 WCF Data Services[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]摘要。</span><span class="sxs-lookup"><span data-stu-id="87104-103">This section describes how to create and configure WCF Data Services to expose data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="87104-104">如需有關建立資料服務所需的基本步驟的詳細資訊，請參閱 <<c0> [ 公開資料做為服務](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="87104-104">For more information about the basic steps required to create a data service, see [Exposing Your Data as a Service](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="87104-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="87104-105">In This Section</span></span>

 [<span data-ttu-id="87104-106">設定資料服務</span><span class="sxs-lookup"><span data-stu-id="87104-106">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)

 <span data-ttu-id="87104-107">描述 WCF Data Services 提供的資料服務組態選項。</span><span class="sxs-lookup"><span data-stu-id="87104-107">Describes the data service configuration options provided by WCF Data Services.</span></span>

 [<span data-ttu-id="87104-108">資料服務提供者</span><span class="sxs-lookup"><span data-stu-id="87104-108">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)

 <span data-ttu-id="87104-109">描述將資料公開為資料服務的提供者模型。</span><span class="sxs-lookup"><span data-stu-id="87104-109">Describes the provider models for exposing data as a data service.</span></span>

 [<span data-ttu-id="87104-110">服務作業</span><span class="sxs-lookup"><span data-stu-id="87104-110">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)

 <span data-ttu-id="87104-111">描述如何定義在伺服器上公開方法的服務作業。</span><span class="sxs-lookup"><span data-stu-id="87104-111">Describes how to define service operations that expose methods on the server.</span></span>

 [<span data-ttu-id="87104-112">摘要自訂</span><span class="sxs-lookup"><span data-stu-id="87104-112">Feed Customization</span></span>](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)

 <span data-ttu-id="87104-113">描述如何建立資料模型內實體之間的對應，此模型是由資料服務提供者和資料摘要中的元素所定義。</span><span class="sxs-lookup"><span data-stu-id="87104-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>

 [<span data-ttu-id="87104-114">攔截器</span><span class="sxs-lookup"><span data-stu-id="87104-114">Interceptors</span></span>](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)

 <span data-ttu-id="87104-115">描述如何定義攔截器方法，針對資料服務的要求執行自訂商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="87104-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>

 [<span data-ttu-id="87104-116">開發和部署 WCF 資料服務</span><span class="sxs-lookup"><span data-stu-id="87104-116">Developing and Deploying WCF Data Services</span></span>](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)

 <span data-ttu-id="87104-117">描述如何使用 Visual Studio 來開發和部署資料服務。</span><span class="sxs-lookup"><span data-stu-id="87104-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>

 [<span data-ttu-id="87104-118">保護 WCF 資料服務的安全</span><span class="sxs-lookup"><span data-stu-id="87104-118">Securing WCF Data Services</span></span>](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)

 <span data-ttu-id="87104-119">描述資料服務的驗證和授權和其他安全性考量。</span><span class="sxs-lookup"><span data-stu-id="87104-119">Describes authentication and authorization for the data service and other security considerations.</span></span>

 [<span data-ttu-id="87104-120">裝載資料服務</span><span class="sxs-lookup"><span data-stu-id="87104-120">Hosting the Data Service</span></span>](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)

 <span data-ttu-id="87104-121">描述如何為您的資料服務選取主機。</span><span class="sxs-lookup"><span data-stu-id="87104-121">Describes how to select a host for your data service.</span></span>

 [<span data-ttu-id="87104-122">資料服務版本控制</span><span class="sxs-lookup"><span data-stu-id="87104-122">Data Service Versioning</span></span>](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)

 <span data-ttu-id="87104-123">描述如何使用不同版本的 OData。</span><span class="sxs-lookup"><span data-stu-id="87104-123">Describes how to work with different versions of the OData.</span></span>

 [<span data-ttu-id="87104-124">WCF 資料服務通訊協定實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="87104-124">WCF Data Services Protocol Implementation Details</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-protocol-implementation-details.md)

 <span data-ttu-id="87104-125">描述 OData 通訊協定目前尚未實作的 WCF Data Services 的選擇性功能。</span><span class="sxs-lookup"><span data-stu-id="87104-125">Describes optional functionalities of the OData protocol that are not currently implemented by WCF Data Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="87104-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87104-126">See also</span></span>

- [<span data-ttu-id="87104-127">WCF Data Services 用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="87104-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [<span data-ttu-id="87104-128">存取資料服務資源</span><span class="sxs-lookup"><span data-stu-id="87104-128">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
- [<span data-ttu-id="87104-129">快速入門</span><span class="sxs-lookup"><span data-stu-id="87104-129">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
