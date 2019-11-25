---
title: 定義 WCF 資料服務
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
ms.openlocfilehash: 26cfee95f7cd3b956ff263d90b713e9d70b98202
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975337"
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="77ef1-102">定義 WCF 資料服務</span><span class="sxs-lookup"><span data-stu-id="77ef1-102">Defining WCF Data Services</span></span>

<span data-ttu-id="77ef1-103">本節說明如何建立和設定 WCF Data Services，以將資料公開為開放式資料通訊協定（OData）摘要。</span><span class="sxs-lookup"><span data-stu-id="77ef1-103">This section describes how to create and configure WCF Data Services to expose data as an Open Data Protocol (OData) feed.</span></span> <span data-ttu-id="77ef1-104">如需建立資料服務所需之基本步驟的詳細資訊，請參閱[將資料公開為服務](exposing-your-data-as-a-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="77ef1-104">For more information about the basic steps required to create a data service, see [Exposing Your Data as a Service](exposing-your-data-as-a-service-wcf-data-services.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="77ef1-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="77ef1-105">In This Section</span></span>

 [<span data-ttu-id="77ef1-106">設定資料服務</span><span class="sxs-lookup"><span data-stu-id="77ef1-106">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)

 <span data-ttu-id="77ef1-107">描述 WCF Data Services 所提供的資料服務設定選項。</span><span class="sxs-lookup"><span data-stu-id="77ef1-107">Describes the data service configuration options provided by WCF Data Services.</span></span>

 [<span data-ttu-id="77ef1-108">資料服務提供者</span><span class="sxs-lookup"><span data-stu-id="77ef1-108">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)

 <span data-ttu-id="77ef1-109">描述將資料公開為資料服務的提供者模型。</span><span class="sxs-lookup"><span data-stu-id="77ef1-109">Describes the provider models for exposing data as a data service.</span></span>

 [<span data-ttu-id="77ef1-110">服務作業</span><span class="sxs-lookup"><span data-stu-id="77ef1-110">Service Operations</span></span>](service-operations-wcf-data-services.md)

 <span data-ttu-id="77ef1-111">描述如何定義在伺服器上公開方法的服務作業。</span><span class="sxs-lookup"><span data-stu-id="77ef1-111">Describes how to define service operations that expose methods on the server.</span></span>

 [<span data-ttu-id="77ef1-112">摘要自訂</span><span class="sxs-lookup"><span data-stu-id="77ef1-112">Feed Customization</span></span>](feed-customization-wcf-data-services.md)

 <span data-ttu-id="77ef1-113">描述如何建立資料模型內實體之間的對應，此模型是由資料服務提供者和資料摘要中的元素所定義。</span><span class="sxs-lookup"><span data-stu-id="77ef1-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>

 [<span data-ttu-id="77ef1-114">攔截器</span><span class="sxs-lookup"><span data-stu-id="77ef1-114">Interceptors</span></span>](interceptors-wcf-data-services.md)

 <span data-ttu-id="77ef1-115">描述如何定義攔截器方法，針對資料服務的要求執行自訂商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="77ef1-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>

 [<span data-ttu-id="77ef1-116">開發和部署 WCF 資料服務</span><span class="sxs-lookup"><span data-stu-id="77ef1-116">Developing and Deploying WCF Data Services</span></span>](developing-and-deploying-wcf-data-services.md)

 <span data-ttu-id="77ef1-117">描述如何使用 Visual Studio 來開發和部署資料服務。</span><span class="sxs-lookup"><span data-stu-id="77ef1-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>

 [<span data-ttu-id="77ef1-118">保護 WCF 資料服務的安全</span><span class="sxs-lookup"><span data-stu-id="77ef1-118">Securing WCF Data Services</span></span>](securing-wcf-data-services.md)

 <span data-ttu-id="77ef1-119">描述資料服務的驗證和授權和其他安全性考量。</span><span class="sxs-lookup"><span data-stu-id="77ef1-119">Describes authentication and authorization for the data service and other security considerations.</span></span>

 [<span data-ttu-id="77ef1-120">裝載資料服務</span><span class="sxs-lookup"><span data-stu-id="77ef1-120">Hosting the Data Service</span></span>](hosting-the-data-service-wcf-data-services.md)

 <span data-ttu-id="77ef1-121">描述如何為您的資料服務選取主機。</span><span class="sxs-lookup"><span data-stu-id="77ef1-121">Describes how to select a host for your data service.</span></span>

 [<span data-ttu-id="77ef1-122">資料服務版本控制</span><span class="sxs-lookup"><span data-stu-id="77ef1-122">Data Service Versioning</span></span>](data-service-versioning-wcf-data-services.md)

 <span data-ttu-id="77ef1-123">描述如何使用不同版本的 OData。</span><span class="sxs-lookup"><span data-stu-id="77ef1-123">Describes how to work with different versions of the OData.</span></span>

 [<span data-ttu-id="77ef1-124">WCF 資料服務通訊協定實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="77ef1-124">WCF Data Services Protocol Implementation Details</span></span>](wcf-data-services-protocol-implementation-details.md)

 <span data-ttu-id="77ef1-125">描述 WCF Data Services 目前未執行的 OData 通訊協定的選擇性功能。</span><span class="sxs-lookup"><span data-stu-id="77ef1-125">Describes optional functionalities of the OData protocol that are not currently implemented by WCF Data Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="77ef1-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="77ef1-126">See also</span></span>

- [<span data-ttu-id="77ef1-127">WCF Data Services 用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="77ef1-127">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
- [<span data-ttu-id="77ef1-128">存取資料服務資源</span><span class="sxs-lookup"><span data-stu-id="77ef1-128">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
- [<span data-ttu-id="77ef1-129">使用者入門</span><span class="sxs-lookup"><span data-stu-id="77ef1-129">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
