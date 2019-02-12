---
title: SQL Server CLR 整合簡介
ms.date: 03/30/2017
ms.assetid: 551d2290-ed80-49be-b377-44b32444da1c
ms.openlocfilehash: dcfc43a68fb8bcacd4a14d6b94a932d656635d55
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092575"
---
# <a name="introduction-to-sql-server-clr-integration"></a><span data-ttu-id="e5cea-102">SQL Server CLR 整合簡介</span><span class="sxs-lookup"><span data-stu-id="e5cea-102">Introduction to SQL Server CLR Integration</span></span>
<span data-ttu-id="e5cea-103">做為 Microsoft .NET Framework 核心的 Common Language Runtime (CLR)，提供了所有 .NET Framework 程式碼的執行環境。</span><span class="sxs-lookup"><span data-stu-id="e5cea-103">The common language runtime (CLR) is the heart of the Microsoft .NET Framework and provides the execution environment for all .NET Framework code.</span></span> <span data-ttu-id="e5cea-104">CLR 中執行的程式碼稱為 Managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e5cea-104">Code that runs within the CLR is referred to as managed code.</span></span> <span data-ttu-id="e5cea-105">CLR 提供程式執行所需的各種功能及服務，包括 just-in-time (JIT) 編譯、配置及管理記憶體、強制使用型別安全性、例外處理、執行緒管理及安全性。</span><span class="sxs-lookup"><span data-stu-id="e5cea-105">The CLR provides various functions and services required for program execution, including just-in-time (JIT) compilation, allocating and managing memory, enforcing type safety, exception handling, thread management, and security.</span></span>  
  
 <span data-ttu-id="e5cea-106">利用 Microsoft SQL Server 中裝載的 CLR (稱為 CLR 整合)，您能夠以 Managed 程式碼撰寫預存程序、觸發程序、使用者定義函式、使用者定義型別及使用者定義彙總。</span><span class="sxs-lookup"><span data-stu-id="e5cea-106">With the CLR hosted in Microsoft SQL Server (called CLR integration), you can author stored procedures, triggers, user-defined functions, user-defined types, and user-defined aggregates in managed code.</span></span> <span data-ttu-id="e5cea-107">因為 Managed 程式碼在執行前會編譯成原生程式碼，所以在部分案例中可大幅提升效能。</span><span class="sxs-lookup"><span data-stu-id="e5cea-107">Because managed code compiles to native code prior to execution, you can achieve significant performance increases in some scenarios.</span></span>  
  
 <span data-ttu-id="e5cea-108">Managed 程式碼使用程式碼存取安全性 (CAS)、程式碼連結及應用程式定義域，以防止組件執行某些作業。</span><span class="sxs-lookup"><span data-stu-id="e5cea-108">Managed code uses Code Access Security (CAS), code links, and application domains to prevent assemblies from performing certain operations.</span></span> <span data-ttu-id="e5cea-109">SQL Server 使用 CAS 協助保護 Managed 程式碼，並防止損害作業系統或資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="e5cea-109">SQL Server uses CAS to help secure the managed code and prevent compromise of the operating system or database server.</span></span>  
  
 <span data-ttu-id="e5cea-110">本節的目的是僅提供以 SQL Server CLR 整合進行程式設計快速入門所需的足夠資訊，並未包含廣泛資訊。</span><span class="sxs-lookup"><span data-stu-id="e5cea-110">This section is meant to provide only enough information to get started programming with SQL Server CLR integration, and is not meant to be comprehensive.</span></span> <span data-ttu-id="e5cea-111">如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。</span><span class="sxs-lookup"><span data-stu-id="e5cea-111">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="e5cea-112">**SQL Server 線上叢書**</span><span class="sxs-lookup"><span data-stu-id="e5cea-112">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="e5cea-113">Common Language Runtime (CLR) 整合概觀</span><span class="sxs-lookup"><span data-stu-id="e5cea-113">Common Language Runtime (CLR) Integration Overview</span></span>](https://go.microsoft.com/fwlink/?LinkId=115242)  
  
## <a name="enabling-clr-integration"></a><span data-ttu-id="e5cea-114">啟用 CLR 整合</span><span class="sxs-lookup"><span data-stu-id="e5cea-114">Enabling CLR Integration</span></span>  
 <span data-ttu-id="e5cea-115">預設會在 Microsoft SQL Server 中停用 Common Language Runtime (CLR) 整合功能，且為了使用 CLR 整合所實作的物件，必須啟用這個功能。</span><span class="sxs-lookup"><span data-stu-id="e5cea-115">The common language runtime (CLR) integration feature is off by default in Microsoft SQL Server, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="e5cea-116">若要啟用使用 Transact-SQL 進行 CLR 整合，請使用 `clr enabled` 預存程序的 `sp_configure` 選項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e5cea-116">To enable CLR integration using Transact-SQL, use the `clr enabled` option of the `sp_configure` stored procedure as shown:</span></span>  
  
```  
sp_configure 'clr enabled', 1  
GO  
RECONFIGURE  
GO  
```  
  
 <span data-ttu-id="e5cea-117">您可以將 `clr enabled` 選項設定為 0，藉以停用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="e5cea-117">You can disable CLR integration by setting the `clr enabled` option to 0.</span></span> <span data-ttu-id="e5cea-118">停用 CLR 整合時，SQL Server 會停止執行所有 CLR 常式，並卸載所有應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="e5cea-118">When you disable CLR integration, SQL Server stops executing all CLR routines and unloads all application domains.</span></span>  
  
 <span data-ttu-id="e5cea-119">如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。</span><span class="sxs-lookup"><span data-stu-id="e5cea-119">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="e5cea-120">**SQL Server 線上叢書**</span><span class="sxs-lookup"><span data-stu-id="e5cea-120">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="e5cea-121">啟用 CLR 整合</span><span class="sxs-lookup"><span data-stu-id="e5cea-121">Enabling CLR Integration</span></span>](https://go.microsoft.com/fwlink/?LinkId=115230)  
  
## <a name="deploying-a-clr-assembly"></a><span data-ttu-id="e5cea-122">部署 CLR 組件</span><span class="sxs-lookup"><span data-stu-id="e5cea-122">Deploying a CLR Assembly</span></span>  
 <span data-ttu-id="e5cea-123">一旦 CLR 方法已經在測試伺服器上測試並驗證，您就可以使用部署指令碼，將它們散發至實際執行伺服器 (Production Server)。</span><span class="sxs-lookup"><span data-stu-id="e5cea-123">Once the CLR methods have been tested and verified on the test server, they can be distributed to production servers using a deployment script.</span></span> <span data-ttu-id="e5cea-124">您可以手動產生部署指令碼，也可以使用 SQL Server Management Studio 來產生部署指令碼。</span><span class="sxs-lookup"><span data-stu-id="e5cea-124">The deployment script can be generated manually, or by using SQL Server Management Studio.</span></span> <span data-ttu-id="e5cea-125">如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。</span><span class="sxs-lookup"><span data-stu-id="e5cea-125">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="e5cea-126">**SQL Server 線上叢書**</span><span class="sxs-lookup"><span data-stu-id="e5cea-126">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="e5cea-127">部署 CLR 資料庫物件</span><span class="sxs-lookup"><span data-stu-id="e5cea-127">Deploying CLR Database Objects</span></span>](https://go.microsoft.com/fwlink/?LinkId=115232)  
  
## <a name="clr-integration-security"></a><span data-ttu-id="e5cea-128">CLR 整合安全性</span><span class="sxs-lookup"><span data-stu-id="e5cea-128">CLR Integration Security</span></span>  
 <span data-ttu-id="e5cea-129">Microsoft SQL Server 與 Microsoft .NET Framework Common Language Runtime (CLR) 的整合安全性模型，可管理及保護在 SQL Server 內執行之不同類型 CLR 及非 CLR 物件的存取權。</span><span class="sxs-lookup"><span data-stu-id="e5cea-129">The security model of the Microsoft SQL Server integration with the Microsoft .NET Framework common language runtime (CLR) manages and secures access between different types of CLR and non-CLR objects running within SQL Server.</span></span> <span data-ttu-id="e5cea-130">這些物件可由 Transact-SQL 陳述式或在伺服器中執行的其他 CLR 物件呼叫。</span><span class="sxs-lookup"><span data-stu-id="e5cea-130">These objects may be called by a Transact-SQL statement or another CLR object running in the server.</span></span>  
  
 <span data-ttu-id="e5cea-131">如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。</span><span class="sxs-lookup"><span data-stu-id="e5cea-131">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="e5cea-132">**SQL Server 線上叢書**</span><span class="sxs-lookup"><span data-stu-id="e5cea-132">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="e5cea-133">CLR 整合安全性</span><span class="sxs-lookup"><span data-stu-id="e5cea-133">CLR Integration Security</span></span>](https://go.microsoft.com/fwlink/?LinkId=115234)  
  
## <a name="debugging-a-clr-assembly"></a><span data-ttu-id="e5cea-134">偵錯 CLR 組件</span><span class="sxs-lookup"><span data-stu-id="e5cea-134">Debugging a CLR Assembly</span></span>  
 <span data-ttu-id="e5cea-135">Microsoft SQL Server 支援在資料庫中偵錯 Transact-SQL 及 Common Language Runtime (CLR) 物件。</span><span class="sxs-lookup"><span data-stu-id="e5cea-135">Microsoft SQL Server provides support for debugging Transact-SQL and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="e5cea-136">偵錯可跨語言運作：使用者可以從 Transact-SQL 無接縫地進入 CLR 物件，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="e5cea-136">Debugging works across languages: users can step seamlessly into CLR objects from Transact-SQL, and vice versa.</span></span>  
  
 <span data-ttu-id="e5cea-137">如需詳細資訊，請參閱您所使用之 SQL Server 版本的《SQL Server 線上叢書》版本。</span><span class="sxs-lookup"><span data-stu-id="e5cea-137">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="e5cea-138">**SQL Server 線上叢書**</span><span class="sxs-lookup"><span data-stu-id="e5cea-138">**SQL Server Books Online**</span></span>  
  
-   [<span data-ttu-id="e5cea-139">偵錯 CLR 資料庫物件</span><span class="sxs-lookup"><span data-stu-id="e5cea-139">Debugging CLR Database Objects</span></span>](https://go.microsoft.com/fwlink/?LinkId=115236)  
  
## <a name="see-also"></a><span data-ttu-id="e5cea-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5cea-140">See also</span></span>
- [<span data-ttu-id="e5cea-141">程式碼存取安全性和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e5cea-141">Code Access Security and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/code-access-security.md)
- [<span data-ttu-id="e5cea-142">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="e5cea-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
