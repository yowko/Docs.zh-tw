---
title: 使用資料定義語言
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 25d7f49644996d87ddb5d191dc313916c0ca6fbb
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45748627"
---
# <a name="working-with-data-definition-language"></a><span data-ttu-id="7934b-102">使用資料定義語言</span><span class="sxs-lookup"><span data-stu-id="7934b-102">Working with Data Definition Language</span></span>
<span data-ttu-id="7934b-103">開頭[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]第 4 版，[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]支援資料定義語言 (DDL)。</span><span class="sxs-lookup"><span data-stu-id="7934b-103">Starting with the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] version 4, the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] supports data definition language (DDL).</span></span> <span data-ttu-id="7934b-104">這可讓您根據連接字串和儲存體 (SSDL) 模型的中繼資料，建立或刪除資料庫執行個體。</span><span class="sxs-lookup"><span data-stu-id="7934b-104">This allows you to create or delete a database instance based on the connection string and the metadata of the storage (SSDL) model.</span></span>  
  
 <span data-ttu-id="7934b-105"><xref:System.Data.Objects.ObjectContext> 的下列方法會使用連接字串和 SSDL 內容來達成下列目的：建立或刪除資料庫、檢查資料庫是否存在，以及檢視產生的 DDL 指令碼：</span><span class="sxs-lookup"><span data-stu-id="7934b-105">The following methods on the <xref:System.Data.Objects.ObjectContext> use the connection string and the SSDL content to accomplish the following: create or delete the database, check whether the database exists, and view the generated DDL script:</span></span>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  <span data-ttu-id="7934b-106">執行 DDL 命令需要足夠的權限。</span><span class="sxs-lookup"><span data-stu-id="7934b-106">Executing the DDL commands assumes sufficient permissions.</span></span>  
  
 <span data-ttu-id="7934b-107">先前所列的方法會將大部分工作委派給基礎 ADO.NET 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="7934b-107">The methods previously listed delegate most of the work to the underlying ADO.NET data provider.</span></span> <span data-ttu-id="7934b-108">提供者要負責確保用來產生資料庫物件的命名慣例與用於查詢和更新的慣例一致。</span><span class="sxs-lookup"><span data-stu-id="7934b-108">It is the provider’s responsibility to ensure that the naming convention used to generate database objects is consistent with conventions used for querying and updates.</span></span>  
  
 <span data-ttu-id="7934b-109">下列範例將為您示範如何根據現有的模型產生資料庫。</span><span class="sxs-lookup"><span data-stu-id="7934b-109">The following example shows you how to generate the database based on the existing model.</span></span> <span data-ttu-id="7934b-110">此外，這個範例也會將新的實體物件加入至物件內容，然後將它儲存至資料庫。</span><span class="sxs-lookup"><span data-stu-id="7934b-110">It also adds a new entity object to the object context and then saves it to the database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="7934b-111">程序</span><span class="sxs-lookup"><span data-stu-id="7934b-111">Procedures</span></span>  
  
#### <a name="to-define-a-database-based-on-the-existing-model"></a><span data-ttu-id="7934b-112">若要根據現有的模型定義資料庫</span><span class="sxs-lookup"><span data-stu-id="7934b-112">To define a database based on the existing model</span></span>  
  
1.  <span data-ttu-id="7934b-113">建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="7934b-113">Create a console application.</span></span>  
  
2.  <span data-ttu-id="7934b-114">將現有的模型加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="7934b-114">Add an existing model to your application.</span></span>  
  
    1.  <span data-ttu-id="7934b-115">新增名為空的模型`SchoolModel`。</span><span class="sxs-lookup"><span data-stu-id="7934b-115">Add an empty model named `SchoolModel`.</span></span> <span data-ttu-id="7934b-116">若要建立空的模型，請參閱[如何： 建立新.edmx 檔案](https://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2)主題。</span><span class="sxs-lookup"><span data-stu-id="7934b-116">To create an empty model, see the [How to: Create a New .edmx File](https://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2) topic.</span></span>  
  
     <span data-ttu-id="7934b-117">SchoolModel.edmx 檔案就會加入至您的專案。</span><span class="sxs-lookup"><span data-stu-id="7934b-117">The SchoolModel.edmx file is added to your project.</span></span>  
  
    1.  <span data-ttu-id="7934b-118">複製概念、 儲存體，並將對應從 School 模型的內容[School 模型](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac)主題。</span><span class="sxs-lookup"><span data-stu-id="7934b-118">Copy the conceptual, storage, and mapping content for the School model from the [School Model](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) topic.</span></span>  
  
    2.  <span data-ttu-id="7934b-119">開啟 SchoolModel.edmx 檔案並在 `edmx:Runtime` 標記中貼上內容。</span><span class="sxs-lookup"><span data-stu-id="7934b-119">Open the SchoolModel.edmx file and paste the content within the `edmx:Runtime` tags.</span></span>  
  
3.  <span data-ttu-id="7934b-120">將下列程式碼加入至 main 函式。</span><span class="sxs-lookup"><span data-stu-id="7934b-120">Add the following code to your main function.</span></span> <span data-ttu-id="7934b-121">此程式碼會將連接字串初始化為資料庫伺服器、檢視 DDL 指令碼、建立資料庫、將新的實體加入至內容，並且將變更儲存至資料庫。</span><span class="sxs-lookup"><span data-stu-id="7934b-121">The code initializes the connection string to your database server, views the DDL script, creates the database, adds a new entity to the context, and saves the changes to the database.</span></span>  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
