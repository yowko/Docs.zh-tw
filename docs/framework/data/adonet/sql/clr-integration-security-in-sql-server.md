---
title: SQL Server 中的 CLR 整合安全性
ms.date: 03/30/2017
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
ms.openlocfilehash: 946401211d515df9ba5b9e38d7cfd10730973b64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165811"
---
# <a name="clr-integration-security-in-sql-server"></a><span data-ttu-id="1e4f5-102">SQL Server 中的 CLR 整合安全性</span><span class="sxs-lookup"><span data-stu-id="1e4f5-102">CLR Integration Security in SQL Server</span></span>
<span data-ttu-id="1e4f5-103">Microsoft SQL Server 提供 .NET Framework 之 Common Language Runtime (CLR) 元件的整合。</span><span class="sxs-lookup"><span data-stu-id="1e4f5-103">Microsoft SQL Server provides the integration of the common language runtime (CLR) component of the .NET Framework.</span></span> <span data-ttu-id="1e4f5-104">CLR 整合可讓您使用任意 .NET Framework 語言 (包括 Microsoft Visual Basic .NET 或 Microsoft Visual C#)，撰寫預存程序 (Stored Procedure)、觸發程序 (Trigger)、使用者定義型別、使用者定義函式、使用者定義彙總及資料流資料表值函式等。</span><span class="sxs-lookup"><span data-stu-id="1e4f5-104">CLR integration allows you to write stored procedures, triggers, user-defined types, user-defined functions, user-defined aggregates, and streaming table-valued functions, using any .NET Framework language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span>  
  
 <span data-ttu-id="1e4f5-105">CLR 支援稱為 Managed 程式碼之程式碼存取安全性 (CAS) 的安全性模型。</span><span class="sxs-lookup"><span data-stu-id="1e4f5-105">The CLR supports a security model called code access security (CAS) for managed code.</span></span> <span data-ttu-id="1e4f5-106">此模型會根據中繼資料中的程式碼所提供的辨識項，為組件授與權限。</span><span class="sxs-lookup"><span data-stu-id="1e4f5-106">In this model, permissions are granted to assemblies based on evidence supplied by the code in metadata.</span></span> <span data-ttu-id="1e4f5-107">SQL Server 將 SQL Server 的使用者架構安全性模型與 CLR 的程式碼存取架構安全性模型相整合。</span><span class="sxs-lookup"><span data-stu-id="1e4f5-107">SQL Server integrates the user-based security model of SQL Server with the code access-based security model of the CLR.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="1e4f5-108">外部資源</span><span class="sxs-lookup"><span data-stu-id="1e4f5-108">External Resources</span></span>  
 <span data-ttu-id="1e4f5-109">如需有關 SQL Server 的 CLR 整合的詳細資訊，請參閱下列資源。</span><span class="sxs-lookup"><span data-stu-id="1e4f5-109">For more information on CLR integration with SQL Server, see the following resources.</span></span>  
  
|<span data-ttu-id="1e4f5-110">資源</span><span class="sxs-lookup"><span data-stu-id="1e4f5-110">Resource</span></span>|<span data-ttu-id="1e4f5-111">描述</span><span class="sxs-lookup"><span data-stu-id="1e4f5-111">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="1e4f5-112">程式碼存取安全性</span><span class="sxs-lookup"><span data-stu-id="1e4f5-112">Code Access Security</span></span>](../../../../../docs/framework/misc/code-access-security.md)|<span data-ttu-id="1e4f5-113">包含說明 .NET Framework 中的 CAS 的主題。</span><span class="sxs-lookup"><span data-stu-id="1e4f5-113">Contains topics describing CAS in the .NET Framework.</span></span>|  
|[<span data-ttu-id="1e4f5-114">CLR 整合安全性</span><span class="sxs-lookup"><span data-stu-id="1e4f5-114">CLR Integration Security</span></span>](/sql/relational-databases/clr-integration/security/clr-integration-security)|<span data-ttu-id="1e4f5-115">討論在 SQL Server 內部執行之 Managed 程式碼的安全性模型。</span><span class="sxs-lookup"><span data-stu-id="1e4f5-115">Discusses the security model for managed code executing inside of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e4f5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e4f5-116">See also</span></span>

- [<span data-ttu-id="1e4f5-117">設定 ADO.NET 應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="1e4f5-117">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [<span data-ttu-id="1e4f5-118">SQL Server 中的應用程式安全性案例</span><span class="sxs-lookup"><span data-stu-id="1e4f5-118">Application Security Scenarios in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="1e4f5-119">SQL Server Common Language Runtime 整合</span><span class="sxs-lookup"><span data-stu-id="1e4f5-119">SQL Server Common Language Runtime Integration</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)
- [<span data-ttu-id="1e4f5-120">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="1e4f5-120">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)
