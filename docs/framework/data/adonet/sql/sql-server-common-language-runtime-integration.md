---
title: SQL Server Common Language Runtime 整合
ms.date: 03/30/2017
ms.assetid: c7a324c4-160d-44c2-b593-641af06eca61
ms.openlocfilehash: d9fe0f03c88584607c6bc38fcbcff3f9424fd40c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183022"
---
# <a name="sql-server-common-language-runtime-integration"></a><span data-ttu-id="5687c-102">SQL Server Common Language Runtime 整合</span><span class="sxs-lookup"><span data-stu-id="5687c-102">SQL Server Common Language Runtime Integration</span></span>

<span data-ttu-id="5687c-103">SQL Server 2005 導入了 .NET Framework for Microsoft Windows 之 Common Language Runtime (CLR) 元件的整合。</span><span class="sxs-lookup"><span data-stu-id="5687c-103">SQL Server 2005 introduced the integration of the common language runtime (CLR) component of the .NET Framework for Microsoft Windows.</span></span> <span data-ttu-id="5687c-104">這表示您可以使用任何 .NET Framework 語言 (包括 Microsoft Visual Basic .NET 及 Microsoft Visual C#)，撰寫預存程序 (Stored Procedure)、觸發程序 (Trigger)、使用者定義型別、使用者定義函式、使用者定義彙總及資料流資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="5687c-104">This means that you can write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, including Microsoft Visual Basic .NET and Microsoft Visual C#.</span></span> <span data-ttu-id="5687c-105"><xref:Microsoft.SqlServer.Server> 命名空間包含一組新的應用程式開發介面 (API)，以便 Managed 程式碼可與 Microsoft SQL Server 環境互動。</span><span class="sxs-lookup"><span data-stu-id="5687c-105">The <xref:Microsoft.SqlServer.Server> namespace contains a set of new application programming interfaces (APIs) so that managed code can interact with the Microsoft SQL Server environment.</span></span>  
  
 <span data-ttu-id="5687c-106">本節說明 SQL Server Common Language Runtime (CLR) 整合特定的功能及行為，以及 ADO.NET 的 SQL Server 同處理序特定擴充。</span><span class="sxs-lookup"><span data-stu-id="5687c-106">This section describes features and behaviors that are specific to SQL Server common language runtime (CLR) integration and the SQL Server in-process specific extensions to ADO.NET.</span></span>  
  
 <span data-ttu-id="5687c-107">本節的目的是僅提供以 SQL Server CLR 整合進行程式設計快速入門所需的足夠資訊，並未包含廣泛資訊。</span><span class="sxs-lookup"><span data-stu-id="5687c-107">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="5687c-108">如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。</span><span class="sxs-lookup"><span data-stu-id="5687c-108">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="5687c-109">**SQL Server 文件**</span><span class="sxs-lookup"><span data-stu-id="5687c-109">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="5687c-110">Common Language Runtime (CLR) 整合程式設計概念</span><span class="sxs-lookup"><span data-stu-id="5687c-110">Common Language Runtime (CLR) Integration Programming Concepts</span></span>](/sql/relational-databases/clr-integration/common-language-runtime-clr-integration-programming-concepts)  
  
## <a name="in-this-section"></a><span data-ttu-id="5687c-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="5687c-111">In This Section</span></span>  

 [<span data-ttu-id="5687c-112">SQL Server CLR 整合簡介</span><span class="sxs-lookup"><span data-stu-id="5687c-112">Introduction to SQL Server CLR Integration</span></span>](introduction-to-sql-server-clr-integration.md)  
 <span data-ttu-id="5687c-113">提供 SQL Server CLR 整合的簡介。</span><span class="sxs-lookup"><span data-stu-id="5687c-113">Provides an introduction to SQL Server CLR integration.</span></span> <span data-ttu-id="5687c-114">同時提供其他主題的連結。</span><span class="sxs-lookup"><span data-stu-id="5687c-114">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="5687c-115">CLR 使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="5687c-115">CLR User-Defined Functions</span></span>](clr-user-defined-functions.md)  
 <span data-ttu-id="5687c-116">描述如何實作與使用各種類型的 CLR 函數：資料表值函式、純量函數，以及使用者定義彙總函式。</span><span class="sxs-lookup"><span data-stu-id="5687c-116">Describes how to implement and use the various types of CLR functions: table-valued, scalar, and user-defined aggregate functions.</span></span>  
  
 [<span data-ttu-id="5687c-117">CLR 使用者定義類型</span><span class="sxs-lookup"><span data-stu-id="5687c-117">CLR User-Defined Types</span></span>](clr-user-defined-types.md)  
 <span data-ttu-id="5687c-118">描述如何實作及使用 CLR 使用者定義型別。</span><span class="sxs-lookup"><span data-stu-id="5687c-118">Describes how to implement and use CLR user-defined types.</span></span> <span data-ttu-id="5687c-119">同時提供其他主題的連結。</span><span class="sxs-lookup"><span data-stu-id="5687c-119">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="5687c-120">CLR 預存程序</span><span class="sxs-lookup"><span data-stu-id="5687c-120">CLR Stored Procedures</span></span>](clr-stored-procedures.md)  
 <span data-ttu-id="5687c-121">描述如何實作及使用 CLR 預存程序。</span><span class="sxs-lookup"><span data-stu-id="5687c-121">Describes how to implement and use CLR stored procedures.</span></span> <span data-ttu-id="5687c-122">同時提供其他主題的連結。</span><span class="sxs-lookup"><span data-stu-id="5687c-122">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="5687c-123">CLR 觸發程序</span><span class="sxs-lookup"><span data-stu-id="5687c-123">CLR Triggers</span></span>](clr-triggers.md)  
 <span data-ttu-id="5687c-124">描述如何實作及使用 CLR 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="5687c-124">Describes how to implement and use CLR triggers.</span></span> <span data-ttu-id="5687c-125">同時提供其他主題的連結。</span><span class="sxs-lookup"><span data-stu-id="5687c-125">Provides links to additional topics.</span></span>  
  
 [<span data-ttu-id="5687c-126">內容連接</span><span class="sxs-lookup"><span data-stu-id="5687c-126">The Context Connection</span></span>](the-context-connection.md)  
 <span data-ttu-id="5687c-127">描述內容連線。</span><span class="sxs-lookup"><span data-stu-id="5687c-127">Describes the context connection.</span></span>  
  
 [<span data-ttu-id="5687c-128">ADO.NET 的 SQL Server 同處理序特定行為</span><span class="sxs-lookup"><span data-stu-id="5687c-128">SQL Server In-Process-Specific Behavior of ADO.NET</span></span>](sql-server-in-process-specific-behavior-of-adonet.md)  
 <span data-ttu-id="5687c-129">說明 ADO.NET 的 SQL Server 同處理序特定擴充及內容連接。</span><span class="sxs-lookup"><span data-stu-id="5687c-129">Describes the SQL Server in-process specific extensions to ADO.NET, and the context connection.</span></span> <span data-ttu-id="5687c-130">同時提供其他主題的連結。</span><span class="sxs-lookup"><span data-stu-id="5687c-130">Provides links to additional topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5687c-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5687c-131">See also</span></span>

- <span data-ttu-id="5687c-132">[SQL Server and ADO.NET](index.md) (SQL Server 和 ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="5687c-132">[SQL Server and ADO.NET](index.md)</span></span>
- <span data-ttu-id="5687c-133">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="5687c-133">[ADO.NET Overview](../ado-net-overview.md)</span></span>
