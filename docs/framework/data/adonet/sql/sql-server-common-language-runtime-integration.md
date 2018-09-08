---
title: SQL Server Common Language Runtime 整合
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: 5f6c1dcccaddeadb65e6fc949960b0232d00ed81
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44190997"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="6927d-102">SQL Server Common Language Runtime 整合</span><span class="sxs-lookup"><span data-stu-id="6927d-102">SQL Server Common Language Runtime Integration</span></span>
<span data-ttu-id="6927d-103">SQL Server 2005 導入了 .NET Framework for Microsoft Windows 之 Common Language Runtime (CLR) 元件的整合。</span><span class="sxs-lookup"><span data-stu-id="6927d-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="6927d-104">這表示您可以使用任何 .NET Framework 語言 (包括 Microsoft Visual Basic .NET 及 Microsoft Visual C#)，撰寫預存程序 (Stored Procedure)、觸發程序 (Trigger)、使用者定義型別、使用者定義函式、使用者定義彙總及資料流資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="6927d-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="6927d-105"><xref:Microsoft.SqlServer.Server> 命名空間包含一組新的應用程式開發介面 (API)，以便 Managed 程式碼可與 Microsoft SQL Server 環境互動。</span><span class="sxs-lookup"><span data-stu-id="6927d-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="6927d-106">本節說明 SQL Server Common Language Runtime (CLR) 整合特定的功能及行為，以及 ADO.NET 的 SQL Server 同處理序特定擴充。</span><span class="sxs-lookup"><span data-stu-id="6927d-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="6927d-107">本節的目的是僅提供以 SQL Server CLR 整合進行程式設計快速入門所需的足夠資訊，並未包含廣泛資訊。</span><span class="sxs-lookup"><span data-stu-id="6927d-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="6927d-108">如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。</span><span class="sxs-lookup"><span data-stu-id="6927d-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="6927d-109">**SQL Server 線上叢書**</span><span class="sxs-lookup"><span data-stu-id="6927d-109">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="6927d-110">Common Language Runtime (CLR) 整合程式設計概念</span><span class="sxs-lookup"><span data-stu-id="6927d-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](https://go.microsoft.com/fwlink/?LinkId=115240)  
  
## <a name="in-this-section"></a><span data-ttu-id="6927d-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="6927d-111">In This Section</span></span>  
 [<span data-ttu-id="6927d-112">SQL Server CLR 整合簡介</span><span class="sxs-lookup"><span data-stu-id="6927d-112">Introduction to SQL Server CLR Integration</span></span>](../../../../../docs/framework/data/adonet/sql/introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="6927d-113">提供 SQL Server CLR 整合的簡介。</span><span class="sxs-lookup"><span data-stu-id="6927d-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="6927d-114">同時提供其他主題的連結。</span><span class="sxs-lookup"><span data-stu-id="6927d-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="6927d-115">CLR 使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="6927d-115">CLR User-Defined Functions</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-functions.md)  
 <span data-ttu-id="6927d-116">描述如何實作與使用各種類型的 CLR 函數：資料表值函式、純量函式，以及使用者定義彙總函式。</span><span class="sxs-lookup"><span data-stu-id="6927d-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="6927d-117">CLR 使用者定義類型</span><span class="sxs-lookup"><span data-stu-id="6927d-117">CLR User-Defined Types</span></span>](../../../../../docs/framework/data/adonet/sql/clr-user-defined-types.md)  
 <span data-ttu-id="6927d-118">說明如何實作及使用 CLR 使用者定義型別。</span><span class="sxs-lookup"><span data-stu-id="6927d-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="6927d-119">同時提供其他主題的連結。</span><span class="sxs-lookup"><span data-stu-id="6927d-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="6927d-120">CLR 預存程序</span><span class="sxs-lookup"><span data-stu-id="6927d-120">CLR Stored Procedures</span></span>](../../../../../docs/framework/data/adonet/sql/clr-stored-procedures.md)  
 <span data-ttu-id="6927d-121">說明如何實作及使用 CLR 預存程序。</span><span class="sxs-lookup"><span data-stu-id="6927d-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="6927d-122">同時提供其他主題的連結。</span><span class="sxs-lookup"><span data-stu-id="6927d-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="6927d-123">CLR 觸發程序</span><span class="sxs-lookup"><span data-stu-id="6927d-123">CLR Triggers</span></span>](../../../../../docs/framework/data/adonet/sql/clr-triggers.md)  
 <span data-ttu-id="6927d-124">說明如何實作及使用 CLR 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="6927d-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="6927d-125">同時提供其他主題的連結。</span><span class="sxs-lookup"><span data-stu-id="6927d-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="6927d-126">內容連線</span><span class="sxs-lookup"><span data-stu-id="6927d-126">The Context Connection</span></span>](../../../../../docs/framework/data/adonet/sql/the-context-connection.md)  
 <span data-ttu-id="6927d-127">說明內容連接。</span><span class="sxs-lookup"><span data-stu-id="6927d-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="6927d-128">ADO.NET 的 SQL Server 同處理序特定行為</span><span class="sxs-lookup"><span data-stu-id="6927d-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="6927d-129">說明 ADO.NET 的 SQL Server 同處理序特定擴充及內容連接。</span><span class="sxs-lookup"><span data-stu-id="6927d-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="6927d-130">同時提供其他主題的連結。</span><span class="sxs-lookup"><span data-stu-id="6927d-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6927d-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6927d-131">See Also</span></span>  
 [<span data-ttu-id="6927d-132">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6927d-132">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="6927d-133">在 Managed 程式碼中建立 SQL Server 2005 物件</span><span class="sxs-lookup"><span data-stu-id="6927d-133">Creating SQL Server 2005 Objects In Managed Code</span></span>](https://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [<span data-ttu-id="6927d-134">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="6927d-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
