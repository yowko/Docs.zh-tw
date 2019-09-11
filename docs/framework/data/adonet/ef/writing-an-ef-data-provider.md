---
title: 撰寫 Entity Framework 資料提供者
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 29aa8cb1c6b31d9ada6b01860d76bcf03d37416c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854157"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="ca660-102">撰寫 Entity Framework 資料提供者</span><span class="sxs-lookup"><span data-stu-id="ca660-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="ca660-103">本節將討論如何撰寫 Entity Framework 提供者，以支援 SQL Server 以外的資料來源。</span><span class="sxs-lookup"><span data-stu-id="ca660-103">This section discusses how to write an Entity Framework provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="ca660-104">Entity Framework 包含支援 SQL Server 的提供者。</span><span class="sxs-lookup"><span data-stu-id="ca660-104">The Entity Framework includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="ca660-105">Entity Framework 提供者模型簡介</span><span class="sxs-lookup"><span data-stu-id="ca660-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="ca660-106">Entity Framework 與資料庫無關，而且您可以使用 ADO.NET 提供者模型來撰寫提供者，以連接到不同的資料來源集合。</span><span class="sxs-lookup"><span data-stu-id="ca660-106">The Entity Framework is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="ca660-107">Entity Framework 資料提供者 (使用 ADO.NET 資料提供者模型所建置) 會執行下列功能：</span><span class="sxs-lookup"><span data-stu-id="ca660-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
- <span data-ttu-id="ca660-108">將實體資料模型 (EDM) 基本型別對應到提供者類型。</span><span class="sxs-lookup"><span data-stu-id="ca660-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
- <span data-ttu-id="ca660-109">公開提供者特有的函式。</span><span class="sxs-lookup"><span data-stu-id="ca660-109">Exposes provider-specific functions.</span></span>  
  
- <span data-ttu-id="ca660-110">為指定的 DbQueryCommandTree 產生提供者特有的命令，以支援 Entity Framework 查詢。</span><span class="sxs-lookup"><span data-stu-id="ca660-110">Generates provider-specific commands for a given DbQueryCommandTree to support Entity Framework queries.</span></span>  
  
- <span data-ttu-id="ca660-111">為指定的 DbModificationCommandTree 產生提供者特定的更新命令，以透過 Entity Framework 支援更新。</span><span class="sxs-lookup"><span data-stu-id="ca660-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the Entity Framework.</span></span>  
  
- <span data-ttu-id="ca660-112">公開存放結構定義的對應檔案，以便支援根據資料庫產生模型。</span><span class="sxs-lookup"><span data-stu-id="ca660-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
- <span data-ttu-id="ca660-113">透過概念模型公開中繼資料 (如資料表和檢視表)。</span><span class="sxs-lookup"><span data-stu-id="ca660-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="ca660-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="ca660-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="ca660-115">範例</span><span class="sxs-lookup"><span data-stu-id="ca660-115">Sample</span></span>  
 <span data-ttu-id="ca660-116">如需支援 SQL Server 以外之資料來源的 Entity Framework 提供者範例，請參閱[Entity Framework 範例提供者](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)。</span><span class="sxs-lookup"><span data-stu-id="ca660-116">See the [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) for a sample of an Entity Framework provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ca660-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="ca660-117">In This Section</span></span>  
 [<span data-ttu-id="ca660-118">SQL 產生</span><span class="sxs-lookup"><span data-stu-id="ca660-118">SQL Generation</span></span>](sql-generation.md)  
  
 [<span data-ttu-id="ca660-119">修改 SQL 產生</span><span class="sxs-lookup"><span data-stu-id="ca660-119">Modification SQL Generation</span></span>](modification-sql-generation.md)  
  
 [<span data-ttu-id="ca660-120">提供者資訊清單規格</span><span class="sxs-lookup"><span data-stu-id="ca660-120">Provider Manifest Specification</span></span>](provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="ca660-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca660-121">See also</span></span>

- [<span data-ttu-id="ca660-122">處理資料提供者</span><span class="sxs-lookup"><span data-stu-id="ca660-122">Working with Data Providers</span></span>](working-with-data-providers.md)
