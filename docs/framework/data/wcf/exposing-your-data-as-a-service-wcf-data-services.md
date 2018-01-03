---
title: "將資料當做服務公開 (WCF 資料服務)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 55e0bc058b92540c9b11965854d38e8d124e205c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-your-data-as-a-service-wcf-data-services"></a><span data-ttu-id="4d244-102">將資料當做服務公開 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="4d244-102">Exposing Your Data as a Service (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="4d244-103">使用 Visual Studio 可讓您更輕鬆地定義服務，您將資料公開為整合[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]摘要。</span><span class="sxs-lookup"><span data-stu-id="4d244-103"> integrates with Visual Studio to enable you to more easily define services to expose your data as [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feeds.</span></span> <span data-ttu-id="4d244-104">建立資料服務會公開[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要包含下列基本步驟：</span><span class="sxs-lookup"><span data-stu-id="4d244-104">Creating a data service that exposes an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="4d244-105">**定義****資料模型**。</span><span class="sxs-lookup"><span data-stu-id="4d244-105">**Define** **the data model**.</span></span> [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="4d244-106">原生方式支援資料模型為基礎的[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4d244-106"> natively supports data models that are based on the [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).</span></span> <span data-ttu-id="4d244-107">如需詳細資訊，請參閱[How to： 建立資料服務，使用 ADO.NET Entity Framework 資料來源](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="4d244-107">For more information, see [How to: Create a Data Service Using an ADO.NET Entity Framework Data Source](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).</span></span>  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="4d244-108"> 也支援以 Common Language Runtime (CLR) 物件為基礎的資料模型，這些物件會傳回 <xref:System.Linq.IQueryable%601> 介面的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4d244-108"> also supports data models that are based on common language runtime (CLR) objects that return an instance of the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="4d244-109">這樣可以讓您部署 .NET Framework 中以清單、陣列和集合為基礎的資料服務。</span><span class="sxs-lookup"><span data-stu-id="4d244-109">This enables you to deploy data services that are based on lists, arrays, and collections in the .NET Framework.</span></span> <span data-ttu-id="4d244-110">若要透過這些資料結構啟用建立、更新及刪除作業，您必須同時實作 <xref:System.Data.Services.IUpdatable> 介面。</span><span class="sxs-lookup"><span data-stu-id="4d244-110">To enable create, update, and delete operations over these data structures, you must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="4d244-111">如需詳細資訊，請參閱[How to： 建立資料服務，使用反映提供者](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4d244-111">For more information, see [How to: Create a Data Service Using the Reflection Provider](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).</span></span>  
  
     <span data-ttu-id="4d244-112">更進階的情況下，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]包含一組可讓您定義資料模型，根據晚期繫結資料型別提供者。</span><span class="sxs-lookup"><span data-stu-id="4d244-112">For more advanced scenarios, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] includes a set of providers that enable you to define a data model based on late-bound data types.</span></span> <span data-ttu-id="4d244-113">如需詳細資訊，請參閱[自訂資料服務提供者](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4d244-113">For more information, see [Custom Data Service Providers](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).</span></span>  
  
2.  <span data-ttu-id="4d244-114">**建立資料服務。**</span><span class="sxs-lookup"><span data-stu-id="4d244-114">**Create the data service.**</span></span> <span data-ttu-id="4d244-115">最基本的資料服務會公開繼承自 <xref:System.Data.Services.DataService%601> 類別的類別，其具有實體容器之命名空間限定名稱 `T` 型別。</span><span class="sxs-lookup"><span data-stu-id="4d244-115">The most basic data service exposes a class that inherits from the <xref:System.Data.Services.DataService%601> class, with a type `T` that is the namespace-qualified name of the entity container.</span></span> <span data-ttu-id="4d244-116">如需詳細資訊，請參閱 [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)的資訊。</span><span class="sxs-lookup"><span data-stu-id="4d244-116">For more information, see [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).</span></span>  
  
3.  <span data-ttu-id="4d244-117">**設定資料服務。**</span><span class="sxs-lookup"><span data-stu-id="4d244-117">**Configure the data service.**</span></span> <span data-ttu-id="4d244-118">根據預設， [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 會停用實體容器所公開的資源存取。</span><span class="sxs-lookup"><span data-stu-id="4d244-118">By default, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] disables access to resources that are exposed by an entity container.</span></span> <span data-ttu-id="4d244-119"><xref:System.Data.Services.DataServiceConfiguration> 介面可讓您設定對資源和服務作業的存取、指定可支援的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 版本，以及定義其他整個服務的行為 (例如，批次行為或在單一回應中可傳回的最大實體數目)。</span><span class="sxs-lookup"><span data-stu-id="4d244-119">The <xref:System.Data.Services.DataServiceConfiguration> interface enables you to configure access to resources and service operations, specify the supported version of [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)], and to define other service-wide behaviors, such as batching behaviors or the maximum number of entities that can be returned in a single response.</span></span> <span data-ttu-id="4d244-120">如需詳細資訊，請參閱[設定資料服務](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4d244-120">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="4d244-121">如需如何建立 Northwind 範例資料庫為基礎的簡易資料服務的範例，請參閱[快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4d244-121">For an example of how to create a simple data service that is based on the Northwind sample database, see [Quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d244-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="4d244-122">See Also</span></span>  
 [<span data-ttu-id="4d244-123">快速入門</span><span class="sxs-lookup"><span data-stu-id="4d244-123">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [<span data-ttu-id="4d244-124">概觀</span><span class="sxs-lookup"><span data-stu-id="4d244-124">Overview</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)
