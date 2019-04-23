---
title: 處理站模型概觀
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: 3b1d438ce5a7dbb22772d6c5dc97f196b3263d38
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221830"
---
# <a name="factory-model-overview"></a><span data-ttu-id="e167f-102">處理站模型概觀</span><span class="sxs-lookup"><span data-stu-id="e167f-102">Factory Model Overview</span></span>
<span data-ttu-id="e167f-103">ADO.NET 2.0 在 <xref:System.Data.Common> 命名空間 (Namespace) 中導入了新的基底類別 (Base Class)。</span><span class="sxs-lookup"><span data-stu-id="e167f-103">ADO.NET 2.0 introduced new base classes in the <xref:System.Data.Common> namespace.</span></span> <span data-ttu-id="e167f-104">這些基底類別是抽象類別，表示它們無法直接具現化 (Instantiated)。</span><span class="sxs-lookup"><span data-stu-id="e167f-104">The base classes are abstract, which means that they can't be directly instantiated.</span></span> <span data-ttu-id="e167f-105">它們包括 <xref:System.Data.Common.DbConnection>、<xref:System.Data.Common.DbCommand> 和 <xref:System.Data.Common.DbDataAdapter>，而且可由 .NET Framework 資料提供者 (例如 <xref:System.Data.SqlClient> 和 <xref:System.Data.OleDb>) 共用。</span><span class="sxs-lookup"><span data-stu-id="e167f-105">They include <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, and <xref:System.Data.Common.DbDataAdapter> and are shared by the .NET Framework data providers, such as <xref:System.Data.SqlClient> and <xref:System.Data.OleDb>.</span></span> <span data-ttu-id="e167f-106">加入基底類別可簡化針對 .NET Framework 資料提供者加入功能的程序，而且不需要建立新的介面。</span><span class="sxs-lookup"><span data-stu-id="e167f-106">The addition of base classes simplifies adding functionality to the .NET Framework data providers without having to create new interfaces.</span></span>  
  
 <span data-ttu-id="e167f-107">ADO.NET 2.0 也導入了抽象基底類別，可讓開發人員撰寫不需仰賴特定資料提供者的泛型資料存取程式碼。</span><span class="sxs-lookup"><span data-stu-id="e167f-107">ADO.NET 2.0 also introduced abstract base classes, which enable a developer to write generic data access code that does not depend on a specific data provider.</span></span>  
  
## <a name="the-factory-design-pattern"></a><span data-ttu-id="e167f-108">Factory 設計模式</span><span class="sxs-lookup"><span data-stu-id="e167f-108">The Factory Design Pattern</span></span>  
 <span data-ttu-id="e167f-109">撰寫獨立於提供者以外之程式碼的程式設計模型是以 "Factory" 設計模式為基礎，而這種設計模式會使用單一 API 來存取多個提供者之間的資料庫。</span><span class="sxs-lookup"><span data-stu-id="e167f-109">The programming model for writing provider-independent code is based on the use of the "factory" design pattern, which uses a single API to access databases across multiple providers.</span></span> <span data-ttu-id="e167f-110">要適當命名此模式，因為它會要求僅用特定的物件來建立其他物件，與實際的 Factory 非常相似。</span><span class="sxs-lookup"><span data-stu-id="e167f-110">This pattern is aptly named, as it calls for the use of a specialized object solely to create other objects, much like a real-world factory.</span></span> <span data-ttu-id="e167f-111">如需 factory 設計模式的更詳細說明，請參閱[撰寫泛型資料存取程式碼在 ASP.NET 2.0 和 ADO.NET 2.0 中](https://go.microsoft.com/fwlink/?LinkId=55915)。</span><span class="sxs-lookup"><span data-stu-id="e167f-111">For a more detailed description of the factory design pattern, see [Writing Generic Data Access Code in ASP.NET 2.0 and ADO.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=55915).</span></span>
  
 <span data-ttu-id="e167f-112">從 ADO.NET 2.0 開始，<xref:System.Data.Common.DbProviderFactories> 類別會提供 `static` (或 Visual Basic 中的 `Shared`) 方法來建立 <xref:System.Data.Common.DbProviderFactory> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e167f-112">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbProviderFactories> class provides `static` (or `Shared` in Visual Basic) methods for creating a <xref:System.Data.Common.DbProviderFactory> instance.</span></span> <span data-ttu-id="e167f-113">然後，此執行個體會根據提供者資訊以及在執行階段提供的連接字串，傳回正確的強型別物件。</span><span class="sxs-lookup"><span data-stu-id="e167f-113">The instance then returns a correct strongly typed object based on provider information and the connection string supplied at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e167f-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e167f-114">See also</span></span>

- [<span data-ttu-id="e167f-115">取得 DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="e167f-115">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)
- [<span data-ttu-id="e167f-116">DbConnection、DbCommand 和 DbException</span><span class="sxs-lookup"><span data-stu-id="e167f-116">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="e167f-117">使用 DbDataAdapter 修改資料</span><span class="sxs-lookup"><span data-stu-id="e167f-117">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="e167f-118">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="e167f-118">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
