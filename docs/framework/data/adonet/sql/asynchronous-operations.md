---
title: "非同步作業"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 293f1ff1fad193c019a42372a30ae6466c074515
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="asynchronous-operations"></a><span data-ttu-id="72fae-102">非同步作業</span><span class="sxs-lookup"><span data-stu-id="72fae-102">Asynchronous Operations</span></span>
<span data-ttu-id="72fae-103">某些資料庫作業 (如命令執行) 要花費相當長的時間才能完成。</span><span class="sxs-lookup"><span data-stu-id="72fae-103">Some database operations, such as command executions, can take significant time to complete.</span></span> <span data-ttu-id="72fae-104">在此情況下，單一執行緒應用程式必須封鎖其他作業並等待命令完成後，才能繼續它們自己的作業。</span><span class="sxs-lookup"><span data-stu-id="72fae-104">In such a case, single-threaded applications must block other operations and wait for the command to finish before they can continue their own operations.</span></span> <span data-ttu-id="72fae-105">相反的，將長期執行作業指派給背景執行緒，可讓前景執行緒在作業過程中保持作用中狀態。</span><span class="sxs-lookup"><span data-stu-id="72fae-105">In contrast, being able to assign the long-running operation to a background thread allows the foreground thread to remain active throughout the operation.</span></span> <span data-ttu-id="72fae-106">例如，若在 Windows 應用程式中將長期執行作業委派給背景執行緒，可讓使用者介面執行緒在作業執行時保持回應狀態。</span><span class="sxs-lookup"><span data-stu-id="72fae-106">In a Windows application, for example, delegating the long-running operation to a background thread allows the user interface thread to remain responsive while the operation is executing.</span></span>  
  
 <span data-ttu-id="72fae-107">.NET Framework 提供數個標準非同步設計模式，可供開發人員用於利用背景執行緒，讓使用者介面或高優先權執行緒可以完成其他作業。</span><span class="sxs-lookup"><span data-stu-id="72fae-107">The .NET Framework provides several standard asynchronous design patterns that developers can use to take advantage of background threads and free the user interface or high-priority threads to complete other operations.</span></span> <span data-ttu-id="72fae-108">ADO.NET 在其 <xref:System.Data.SqlClient.SqlCommand> 類別中，支援這些相同的設計模式。</span><span class="sxs-lookup"><span data-stu-id="72fae-108">ADO.NET supports these same design patterns in its <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="72fae-109">尤其是，<xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>、<xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> 及 <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> 方法，搭配 <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>、<xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A> 及 <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> 方法，都可以提供非同步支援。</span><span class="sxs-lookup"><span data-stu-id="72fae-109">Specifically, the <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>, and <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> methods, paired with the <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A>, and <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> methods, provide the asynchronous support.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72fae-110">非同步程式設計是 .NET Framework 的核心功能，而 ADO.NET 可充分利用這些標準設計模式。</span><span class="sxs-lookup"><span data-stu-id="72fae-110">Asynchronous programming is a core feature of the .NET Framework, and ADO.NET takes full advantage of the standard design patterns.</span></span> <span data-ttu-id="72fae-111">如需不同的非同步方法可供開發人員的詳細資訊，請參閱[呼叫同步方法以非同步方式](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)。</span><span class="sxs-lookup"><span data-stu-id="72fae-111">For more information about the different asynchronous techniques available to developers, see [Calling Synchronous Methods Asynchronously](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
 <span data-ttu-id="72fae-112">儘管與 ADO.NET 功能搭配使用非同步技術並不會有任何額外的特殊考量，但大多數的開發人員都只會在 ADO.NET 中使用非同步功能，而不會在 .NET Framework 中的其他領域使用。</span><span class="sxs-lookup"><span data-stu-id="72fae-112">Although using asynchronous techniques with ADO.NET features does not add any special considerations, it is likely that more developers will use asynchronous features in ADO.NET than in other areas of the .NET Framework.</span></span> <span data-ttu-id="72fae-113">瞭解建立多執行緒應用程式的優缺點是很重要的。</span><span class="sxs-lookup"><span data-stu-id="72fae-113">It is important to be aware of the benefits and pitfalls of creating multithreaded applications.</span></span> <span data-ttu-id="72fae-114">本節中接下來的範例會指出在建置包括多執行緒功能的應用程式時，開發人員需要考量的數個重要問題。</span><span class="sxs-lookup"><span data-stu-id="72fae-114">The examples that follow in this section point out several important issues that developers will need to take into account when building applications that incorporate multithreaded functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="72fae-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="72fae-115">In This Section</span></span>  
 [<span data-ttu-id="72fae-116">使用回呼的 Windows 應用程式</span><span class="sxs-lookup"><span data-stu-id="72fae-116">Windows Applications Using Callbacks</span></span>](../../../../../docs/framework/data/adonet/sql/windows-applications-using-callbacks.md)  
 <span data-ttu-id="72fae-117">提供範例，示範如何安全地執行非同步命令，以及正確地處理單獨執行緒與表單及其內容之容的互動。</span><span class="sxs-lookup"><span data-stu-id="72fae-117">Provides an example demonstrating how to execute an asynchronous command safely, correctly handling interaction with a form and its contents from a separate thread.</span></span>  
  
 [<span data-ttu-id="72fae-118">使用 Wait 控制代碼的 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="72fae-118">ASP.NET Applications Using Wait Handles</span></span>](../../../../../docs/framework/data/adonet/sql/aspnet-apps-using-wait-handles.md)  
 <span data-ttu-id="72fae-119">提供範例，示範如何從 ASP.NET 網頁執行多個並行命令，並在所有命令完成後使用等候控制代碼管理作業。</span><span class="sxs-lookup"><span data-stu-id="72fae-119">Provides an example demonstrating how to execute multiple concurrent commands from an ASP.NET page, using Wait handles to manage the operation at completion of all the commands.</span></span>  
  
 [<span data-ttu-id="72fae-120">在主控台應用程式中輪詢</span><span class="sxs-lookup"><span data-stu-id="72fae-120">Polling in Console Applications</span></span>](../../../../../docs/framework/data/adonet/sql/polling-in-console-applications.md)  
 <span data-ttu-id="72fae-121">提供範例，示範如何使用輪詢等待從主控台應用程式執行的非同步命令完成。</span><span class="sxs-lookup"><span data-stu-id="72fae-121">Provides an example demonstrating the use of polling to wait for the completion of an asynchronous command execution from a console application.</span></span> <span data-ttu-id="72fae-122">此技術在類別庫或不具使用者介面的其他應用程式中也有效。</span><span class="sxs-lookup"><span data-stu-id="72fae-122">This technique is also valid in a class library or other application without a user interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72fae-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="72fae-123">See Also</span></span>  
 [<span data-ttu-id="72fae-124">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="72fae-124">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="72fae-125">非同步呼叫同步方法</span><span class="sxs-lookup"><span data-stu-id="72fae-125">Calling Synchronous Methods Asynchronously</span></span>](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 [<span data-ttu-id="72fae-126">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="72fae-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
