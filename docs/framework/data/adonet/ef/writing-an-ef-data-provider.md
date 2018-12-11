---
title: 撰寫 Entity Framework 資料提供者
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 513af001392ae0b7abe8e6c62dc74f09469b3655
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148440"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="dff39-102">撰寫 Entity Framework 資料提供者</span><span class="sxs-lookup"><span data-stu-id="dff39-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="dff39-103">本節討論如何撰寫[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]支援 SQL Server 以外的資料來源的提供者。</span><span class="sxs-lookup"><span data-stu-id="dff39-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="dff39-104">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]包含支援 SQL Server 的提供者。</span><span class="sxs-lookup"><span data-stu-id="dff39-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="dff39-105">Entity Framework 提供者模型簡介</span><span class="sxs-lookup"><span data-stu-id="dff39-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="dff39-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 與資料庫無關，而且您可以使用 ADO.NET 提供者模型來撰寫提供者，以便連接到各種不同的資料來源。</span><span class="sxs-lookup"><span data-stu-id="dff39-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="dff39-107">Entity Framework 資料提供者 (使用 ADO.NET 資料提供者模型所建置) 會執行下列功能：</span><span class="sxs-lookup"><span data-stu-id="dff39-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
-   <span data-ttu-id="dff39-108">將實體資料模型 (EDM) 基本型別對應到提供者類型。</span><span class="sxs-lookup"><span data-stu-id="dff39-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
-   <span data-ttu-id="dff39-109">公開提供者特有的函式。</span><span class="sxs-lookup"><span data-stu-id="dff39-109">Exposes provider-specific functions.</span></span>  
  
-   <span data-ttu-id="dff39-110">為給定的 DbQueryCommandTree 產生提供者特有的命令來支援 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="dff39-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
-   <span data-ttu-id="dff39-111">為給定的 DbModificationCommandTree 產生提供者特有的更新命令，以支援透過 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 的更新。</span><span class="sxs-lookup"><span data-stu-id="dff39-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="dff39-112">公開存放結構定義的對應檔案，以便支援根據資料庫產生模型。</span><span class="sxs-lookup"><span data-stu-id="dff39-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
-   <span data-ttu-id="dff39-113">透過概念模型公開中繼資料 (如資料表和檢視表)。</span><span class="sxs-lookup"><span data-stu-id="dff39-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="dff39-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="dff39-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="dff39-115">範例</span><span class="sxs-lookup"><span data-stu-id="dff39-115">Sample</span></span>  
 <span data-ttu-id="dff39-116">請參閱[Entity Framework 範例提供者](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)如需範例的[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]支援 SQL Server 以外的資料來源的提供者。</span><span class="sxs-lookup"><span data-stu-id="dff39-116">See the [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dff39-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="dff39-117">In This Section</span></span>  
 [<span data-ttu-id="dff39-118">SQL 產生</span><span class="sxs-lookup"><span data-stu-id="dff39-118">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [<span data-ttu-id="dff39-119">修改 SQL 產生</span><span class="sxs-lookup"><span data-stu-id="dff39-119">Modification SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [<span data-ttu-id="dff39-120">提供者資訊清單規格</span><span class="sxs-lookup"><span data-stu-id="dff39-120">Provider Manifest Specification</span></span>](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="dff39-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dff39-121">See Also</span></span>  
 [<span data-ttu-id="dff39-122">處理資料提供者</span><span class="sxs-lookup"><span data-stu-id="dff39-122">Working with Data Providers</span></span>](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
