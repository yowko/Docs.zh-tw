---
title: "Entity Framework 提供者 (WCF 資料服務)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 26c054e3cc9dbf920ab280df43d97acdb90ca055
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="entity-framework-provider-wcf-data-services"></a><span data-ttu-id="d5285-102">Entity Framework 提供者 (WCF 資料服務)</span><span class="sxs-lookup"><span data-stu-id="d5285-102">Entity Framework Provider (WCF Data Services)</span></span>
<span data-ttu-id="d5285-103">如同 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 一般，ADO.NET Entity Framework 是以實體資料模型為基礎 (實體資料模型是一種實體關聯模型)。</span><span class="sxs-lookup"><span data-stu-id="d5285-103">Like [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], the ADO.NET Entity Framework is based on the Entity Data Model, which is a type of entity-relationship model.</span></span> <span data-ttu-id="d5285-104">Entity Framework 將針對實體資料模型，也就所謂的其實作的作業轉譯*概念模型*，到針對資料來源的同等運算。</span><span class="sxs-lookup"><span data-stu-id="d5285-104">The Entity Framework translates operations against its implementation of the Entity Data Model, which is called the *conceptual model*, into equivalent operations against a data source.</span></span> <span data-ttu-id="d5285-105">因此，Entity Framework 非常適合做為以關聯式資料為基礎之資料服務的提供者，而且只要資料庫具有支援 Entity Framework 的資料提供者，皆可與 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="d5285-105">This makes the Entity Framework an ideal provider for data services that are based on relational data, and any database that has a data provider that supports the Entity Framework can be used with [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span> <span data-ttu-id="d5285-106">如需目前支援 Entity Framework 的資料來源的清單，請參閱[Entity framework 協力廠商提供者](http://go.microsoft.com/fwlink/?LinkId=143699)。</span><span class="sxs-lookup"><span data-stu-id="d5285-106">For a list of the data sources that currently support the Entity Framework, see [Third-Party Providers for the Entity Framework](http://go.microsoft.com/fwlink/?LinkId=143699).</span></span>  
  
 <span data-ttu-id="d5285-107">在概念模型中，實體容器是服務的根。</span><span class="sxs-lookup"><span data-stu-id="d5285-107">In a conceptual model, the entity container is the root of the service.</span></span> <span data-ttu-id="d5285-108">您必須先在 Entity Framework 中定義概念模型，資料服務才能公開資料。</span><span class="sxs-lookup"><span data-stu-id="d5285-108">You must define a conceptual model in the Entity Framework before the data can be exposed by a data service.</span></span> <span data-ttu-id="d5285-109">如需詳細資訊，請參閱[How to： 建立資料服務，使用 ADO.NET Entity Framework 資料來源](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="d5285-109">For more information, see [How to: Create a Data Service Using an ADO.NET Entity Framework Data Source](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).</span></span>  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="d5285-110">支援開放式並行存取模型，方式是讓您定義實體的並行語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d5285-110"> supports the optimistic concurrency model by enabling you to define a concurrency token for an entity.</span></span> <span data-ttu-id="d5285-111">這個並行語彙基元包含實體的一個或多個屬性，資料服務會使用它來判斷正在要求、更新或刪除的資料中是否已經發生變更。</span><span class="sxs-lookup"><span data-stu-id="d5285-111">This concurrency token, which includes one or more properties of the entity, is used by the data service to determine whether a change has occurred in the data that is being requested, updated, or deleted.</span></span> <span data-ttu-id="d5285-112">當取自要求中 eTag 的語彙基元值與目前實體的值不同時，資料服務就會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d5285-112">When token values obtained from the eTag in the request differ from the current values of the entity, an exception is raised by the data service.</span></span> <span data-ttu-id="d5285-113">為了指示屬性 (Property) 為並行語彙基元的一部分，您必須在 `ConcurrencyMode="Fixed"` 提供者所定義的資料模型中套用 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="d5285-113">To indicate that a property is part of the concurrency token, you must apply the attribute `ConcurrencyMode="Fixed"` in the data model defined by the [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] provider.</span></span> <span data-ttu-id="d5285-114">並行語彙基元不得包含索引鍵屬性或導覽屬性。</span><span class="sxs-lookup"><span data-stu-id="d5285-114">The concurrency token cannot include a key property or a navigation property.</span></span> <span data-ttu-id="d5285-115">如需詳細資訊，請參閱[更新資料服務](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d5285-115">For more information, see [Updating the Data Service](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="d5285-116">若要深入了解 Entity Framework，請參閱[Entity Framework 概觀](../../../../docs/framework/data/adonet/ef/overview.md)。</span><span class="sxs-lookup"><span data-stu-id="d5285-116">To learn more about the Entity Framework, see [Entity Framework Overview](../../../../docs/framework/data/adonet/ef/overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5285-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5285-117">See Also</span></span>  
 [<span data-ttu-id="d5285-118">資料服務提供者</span><span class="sxs-lookup"><span data-stu-id="d5285-118">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [<span data-ttu-id="d5285-119">反映提供者</span><span class="sxs-lookup"><span data-stu-id="d5285-119">Reflection Provider</span></span>](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)  
 [<span data-ttu-id="d5285-120">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="d5285-120">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
