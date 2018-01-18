---
title: "如何：動態建立資料庫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f92d34276855a7b7473dd15dd3828c4ea91c64d1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-dynamically-create-a-database"></a><span data-ttu-id="9a4d0-102">如何：動態建立資料庫</span><span class="sxs-lookup"><span data-stu-id="9a4d0-102">How to: Dynamically Create a Database</span></span>
<span data-ttu-id="9a4d0-103">在 LINQ to SQL 中，物件模型 (Object Model) 會對應至關聯式資料庫。</span><span class="sxs-lookup"><span data-stu-id="9a4d0-103">In LINQ to SQL, an object model is mapped to a relational database.</span></span> <span data-ttu-id="9a4d0-104">對應的啟用方式是使用以屬性 (Attribute) 為基礎的對應或外部對應檔案來描述關聯式資料庫的結構。</span><span class="sxs-lookup"><span data-stu-id="9a4d0-104">Mapping is enabled by using attribute-based mapping or an external mapping file to describe the structure of the relational database.</span></span> <span data-ttu-id="9a4d0-105">在這兩種情況中，系統會提供足夠的關聯式資料庫相關資訊，可讓您使用 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 方法來建立新的資料庫執行個體 (Instance)。</span><span class="sxs-lookup"><span data-stu-id="9a4d0-105">In both scenarios, there is enough information about the relational database that you can create a new instance of the database using the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="9a4d0-106"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 方法只會針對物件模型中所編碼的資訊範圍，建立資料庫的複本。</span><span class="sxs-lookup"><span data-stu-id="9a4d0-106">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a replica of the database only to the extent of the information encoded in the object model.</span></span> <span data-ttu-id="9a4d0-107">物件模型中的對應檔案和屬性可能不會編碼現有資料庫結構的所有項目。</span><span class="sxs-lookup"><span data-stu-id="9a4d0-107">Mapping files and attributes from your object model might not encode everything about the structure of an existing database.</span></span> <span data-ttu-id="9a4d0-108">對應資訊並不代表使用者定義函式、預存程序 (Stored Procedure)、觸發程序 (Trigger) 或檢查條件約束 (Check Constraint) 的內容。</span><span class="sxs-lookup"><span data-stu-id="9a4d0-108">Mapping information does not represent the contents of user-defined functions, stored procedures, triggers, or check constraints.</span></span> <span data-ttu-id="9a4d0-109">這個行為對各種資料庫而言就已足夠。</span><span class="sxs-lookup"><span data-stu-id="9a4d0-109">This behavior is sufficient for a variety of databases.</span></span>  
  
 <span data-ttu-id="9a4d0-110">您可以將 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 方法用在許多情況下，特別是在已知的資料提供者 (Data Provider) (如 Microsoft SQL Server 2008) 可用時。</span><span class="sxs-lookup"><span data-stu-id="9a4d0-110">You can use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method in any number of scenarios, especially if a known data provider like Microsoft SQL Server 2008 is available.</span></span> <span data-ttu-id="9a4d0-111">典型情況包括：</span><span class="sxs-lookup"><span data-stu-id="9a4d0-111">Typical scenarios include the following:</span></span>  
  
-   <span data-ttu-id="9a4d0-112">建置應用程式，這個應用程式會自動將它自己安裝在客戶系統上。</span><span class="sxs-lookup"><span data-stu-id="9a4d0-112">You are building an application that automatically installs itself on a customer system.</span></span>  
  
-   <span data-ttu-id="9a4d0-113">建置用戶端應用程式，這個用戶端應用程式需要本機資料庫來儲存它的離線狀態。</span><span class="sxs-lookup"><span data-stu-id="9a4d0-113">You are building a client application that needs a local database to save its offline state.</span></span>  
  
 <span data-ttu-id="9a4d0-114">根據連接字串，您也可以使用 .mdf 檔案或目錄名稱來搭配使用 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 方法與 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="9a4d0-114">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method with SQL Server by using an .mdf file or a catalog name, depending on your connection string.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9a4d0-115"> 會使用連接字串來定義要建立的資料庫，以及要在其上建立資料庫的伺服器。</span><span class="sxs-lookup"><span data-stu-id="9a4d0-115"> uses the connection string to define the database to be created and on which server the database is to be created.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a4d0-116">請盡可能使用 Windows 整合式安全性來連接至資料庫，如此連接字串就不需要使用密碼。</span><span class="sxs-lookup"><span data-stu-id="9a4d0-116">Whenever possible, use Windows Integrated Security to connect to the database so that passwords are not required in the connection string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a4d0-117">範例</span><span class="sxs-lookup"><span data-stu-id="9a4d0-117">Example</span></span>  
 <span data-ttu-id="9a4d0-118">下列程式碼會提供如何建立名為 MyDVDs.mdf 之新資料庫的範例。</span><span class="sxs-lookup"><span data-stu-id="9a4d0-118">The following code provides an example of how to create a new database named MyDVDs.mdf.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="9a4d0-119">範例</span><span class="sxs-lookup"><span data-stu-id="9a4d0-119">Example</span></span>  
 <span data-ttu-id="9a4d0-120">您可以使用物件模型來建立資料庫，步驟如下所示：</span><span class="sxs-lookup"><span data-stu-id="9a4d0-120">You can use the object model to create a database by doing the following:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="9a4d0-121">範例</span><span class="sxs-lookup"><span data-stu-id="9a4d0-121">Example</span></span>  
 <span data-ttu-id="9a4d0-122">建置 (Build) 會自動在客戶系統上自行安裝的應用程式時，請查看資料庫是否已經存在，並在建立新的資料庫之前卸除現有的資料庫。</span><span class="sxs-lookup"><span data-stu-id="9a4d0-122">When building an application that automatically installs itself on a  customer system, see if the database already exists and drop it before creating a new one.</span></span> <span data-ttu-id="9a4d0-123"><xref:System.Data.Linq.DataContext> 類別 (Class) 會提供 <xref:System.Data.Linq.DataContext.DatabaseExists%2A> 和 <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> 方法來協助您進行此程序。</span><span class="sxs-lookup"><span data-stu-id="9a4d0-123">The <xref:System.Data.Linq.DataContext> class provides the <xref:System.Data.Linq.DataContext.DatabaseExists%2A> and <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> methods to help you with this process.</span></span>  
  
 <span data-ttu-id="9a4d0-124">下列範例顯示可以使用這些方法來實作此方法的方式：</span><span class="sxs-lookup"><span data-stu-id="9a4d0-124">The following example shows one way these methods can be used to implement this approach:</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="9a4d0-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="9a4d0-125">See Also</span></span>  
 [<span data-ttu-id="9a4d0-126">以屬性為基礎的對應</span><span class="sxs-lookup"><span data-stu-id="9a4d0-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [<span data-ttu-id="9a4d0-127">外部對應</span><span class="sxs-lookup"><span data-stu-id="9a4d0-127">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [<span data-ttu-id="9a4d0-128">SQL-CLR 類型對應</span><span class="sxs-lookup"><span data-stu-id="9a4d0-128">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [<span data-ttu-id="9a4d0-129">背景資訊</span><span class="sxs-lookup"><span data-stu-id="9a4d0-129">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="9a4d0-130">變更和提交資料</span><span class="sxs-lookup"><span data-stu-id="9a4d0-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
