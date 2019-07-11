---
title: 使用資料定義語言
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 788388b93a00cf5393174d35b8a160b4991da3bc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743723"
---
# <a name="working-with-data-definition-language"></a><span data-ttu-id="e6509-102">使用資料定義語言</span><span class="sxs-lookup"><span data-stu-id="e6509-102">Working with Data Definition Language</span></span>
<span data-ttu-id="e6509-103">從.NET Framework 4 版中，開始[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]支援資料定義語言 (DDL)。</span><span class="sxs-lookup"><span data-stu-id="e6509-103">Starting with the .NET Framework version 4, the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] supports data definition language (DDL).</span></span> <span data-ttu-id="e6509-104">這可讓您根據連接字串和儲存體 (SSDL) 模型的中繼資料，建立或刪除資料庫執行個體。</span><span class="sxs-lookup"><span data-stu-id="e6509-104">This allows you to create or delete a database instance based on the connection string and the metadata of the storage (SSDL) model.</span></span>  
  
 <span data-ttu-id="e6509-105"><xref:System.Data.Objects.ObjectContext> 的下列方法會使用連接字串和 SSDL 內容來達成下列目的：建立或刪除資料庫、檢查資料庫是否存在，以及檢視產生的 DDL 指令碼：</span><span class="sxs-lookup"><span data-stu-id="e6509-105">The following methods on the <xref:System.Data.Objects.ObjectContext> use the connection string and the SSDL content to accomplish the following: create or delete the database, check whether the database exists, and view the generated DDL script:</span></span>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  <span data-ttu-id="e6509-106">執行 DDL 命令需要足夠的權限。</span><span class="sxs-lookup"><span data-stu-id="e6509-106">Executing the DDL commands assumes sufficient permissions.</span></span>  
  
 <span data-ttu-id="e6509-107">先前所列的方法會將大部分工作委派給基礎 ADO.NET 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="e6509-107">The methods previously listed delegate most of the work to the underlying ADO.NET data provider.</span></span> <span data-ttu-id="e6509-108">提供者要負責確保用來產生資料庫物件的命名慣例與用於查詢和更新的慣例一致。</span><span class="sxs-lookup"><span data-stu-id="e6509-108">It is the provider’s responsibility to ensure that the naming convention used to generate database objects is consistent with conventions used for querying and updates.</span></span>  
  
 <span data-ttu-id="e6509-109">下列範例將為您示範如何根據現有的模型產生資料庫。</span><span class="sxs-lookup"><span data-stu-id="e6509-109">The following example shows you how to generate the database based on the existing model.</span></span> <span data-ttu-id="e6509-110">此外，這個範例也會將新的實體物件加入至物件內容，然後將它儲存至資料庫。</span><span class="sxs-lookup"><span data-stu-id="e6509-110">It also adds a new entity object to the object context and then saves it to the database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="e6509-111">程序</span><span class="sxs-lookup"><span data-stu-id="e6509-111">Procedures</span></span>  
  
### <a name="to-define-a-database-based-on-the-existing-model"></a><span data-ttu-id="e6509-112">若要根據現有的模型定義資料庫</span><span class="sxs-lookup"><span data-stu-id="e6509-112">To define a database based on the existing model</span></span>  
  
1. <span data-ttu-id="e6509-113">建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6509-113">Create a console application.</span></span>  
  
2. <span data-ttu-id="e6509-114">將現有的模型加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6509-114">Add an existing model to your application.</span></span>  
  
    1. <span data-ttu-id="e6509-115">新增名為空的模型`SchoolModel`。</span><span class="sxs-lookup"><span data-stu-id="e6509-115">Add an empty model named `SchoolModel`.</span></span> <span data-ttu-id="e6509-116">若要建立空的模型，請參閱[How to:建立新.edmx 檔案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100))主題。</span><span class="sxs-lookup"><span data-stu-id="e6509-116">To create an empty model, see the [How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) topic.</span></span>  
  
     <span data-ttu-id="e6509-117">SchoolModel.edmx 檔案就會加入至您的專案。</span><span class="sxs-lookup"><span data-stu-id="e6509-117">The SchoolModel.edmx file is added to your project.</span></span>  
  
    1. <span data-ttu-id="e6509-118">複製概念、 儲存體，並將對應從 School 模型的內容[School 模型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))主題。</span><span class="sxs-lookup"><span data-stu-id="e6509-118">Copy the conceptual, storage, and mapping content for the School model from the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) topic.</span></span>  
  
    2. <span data-ttu-id="e6509-119">開啟 SchoolModel.edmx 檔案並在 `edmx:Runtime` 標記中貼上內容。</span><span class="sxs-lookup"><span data-stu-id="e6509-119">Open the SchoolModel.edmx file and paste the content within the `edmx:Runtime` tags.</span></span>  
  
3. <span data-ttu-id="e6509-120">將下列程式碼加入至 main 函式。</span><span class="sxs-lookup"><span data-stu-id="e6509-120">Add the following code to your main function.</span></span> <span data-ttu-id="e6509-121">此程式碼會將連接字串初始化為資料庫伺服器、檢視 DDL 指令碼、建立資料庫、將新的實體加入至內容，並且將變更儲存至資料庫。</span><span class="sxs-lookup"><span data-stu-id="e6509-121">The code initializes the connection string to your database server, views the DDL script, creates the database, adds a new entity to the context, and saves the changes to the database.</span></span>  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
