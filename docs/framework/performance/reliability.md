---
title: 可靠性
description: 瞭解 .NET 中的可靠性。 防止在 .NET 中執行之主機中的非同步例外狀況，例如 SQL Server。
ms.date: 03/30/2017
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
ms.openlocfilehash: ce9ffbb7f58c2f5dc016c56c0e2ce13b45c30f26
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474250"
---
# <a name="reliability"></a><span data-ttu-id="1807b-104">可靠性</span><span class="sxs-lookup"><span data-stu-id="1807b-104">Reliability</span></span>
<span data-ttu-id="1807b-105">重要的是，在 SQL Server 這類伺服器環境中執行的程式碼可防止發生非同步例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1807b-105">It is important that code executing in server environments such as SQL Server protect against asynchronous exceptions.</span></span> <span data-ttu-id="1807b-106">如這裡所討論，可靠性不是 SQL Server 特有的，而是針對任何在 .NET Framework 2.0 版環境中執行的主機撰寫可靠程式碼。</span><span class="sxs-lookup"><span data-stu-id="1807b-106">Reliability, as discussed here, is not specific to SQL Server but to writing reliable code for any host executing in a .NET Framework version 2.0 environment.</span></span> <span data-ttu-id="1807b-107">不過，SQL Server 是大規模使用 2.0 版新可靠性功能的第一個服務，因此當成範例使用。</span><span class="sxs-lookup"><span data-stu-id="1807b-107">However, SQL Server is the first service making extensive use of the new reliability features of version 2.0, so it is used as an example.</span></span>  
  
 <span data-ttu-id="1807b-108">在 SQL Server 中執行的程式碼必須處理比其他伺服器環境更嚴格的可靠性方針。</span><span class="sxs-lookup"><span data-stu-id="1807b-108">Code running in SQL Server must deal with more stringent reliability guidelines than other server environments.</span></span> <span data-ttu-id="1807b-109">這是因為 SQL Server 的穩定作業處於資源耗用邊緣。</span><span class="sxs-lookup"><span data-stu-id="1807b-109">This is due to SQL Server’s steady operation at the edge of resource consumption.</span></span>  <span data-ttu-id="1807b-110">在 SQL Server 環境中，<xref:System.OutOfMemoryException> 和 <xref:System.Threading.ThreadAbortException> 例外狀況並不常見。</span><span class="sxs-lookup"><span data-stu-id="1807b-110"><xref:System.OutOfMemoryException> and <xref:System.Threading.ThreadAbortException> exceptions are not uncommon in the SQL Server environment.</span></span> <span data-ttu-id="1807b-111">這些方針一般較不著重可靠性，但較著重允許完全受信任的 Managed 程式碼在面對 <xref:System.AppDomain> 層級回收時依正常程序失敗，而這是伺服器維護一致性和可用性的主要方式。</span><span class="sxs-lookup"><span data-stu-id="1807b-111">These guidelines in general are focused less on reliability and more on allowing fully trusted managed code to fail gracefully in the face of <xref:System.AppDomain>-level recycling, which is the primary way the server maintains consistency and availability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1807b-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="1807b-112">In This Section</span></span>  
 [<span data-ttu-id="1807b-113">SQL Server 程式設計和主機保護屬性</span><span class="sxs-lookup"><span data-stu-id="1807b-113">SQL Server Programming and Host Protection Attributes</span></span>](sql-server-programming-and-host-protection-attributes.md)  
 <span data-ttu-id="1807b-114">描述 SQL Server 如何使用 <xref:System.Security.Permissions.HostProtectionAttribute> 屬性來限制 Managed 程式碼的執行。</span><span class="sxs-lookup"><span data-stu-id="1807b-114">Describes how the <xref:System.Security.Permissions.HostProtectionAttribute> attribute is used by SQL Server to restrict the execution of managed code.</span></span>  
  
 [<span data-ttu-id="1807b-115">可靠性最佳作法</span><span class="sxs-lookup"><span data-stu-id="1807b-115">Reliability Best Practices</span></span>](reliability-best-practices.md)  
 <span data-ttu-id="1807b-116">提供撰寫符合可靠性需求之程式碼的方針。</span><span class="sxs-lookup"><span data-stu-id="1807b-116">Provides guidelines for writing code that meets reliability requirements.</span></span>  
  
 [<span data-ttu-id="1807b-117">限制的執行區域</span><span class="sxs-lookup"><span data-stu-id="1807b-117">Constrained Execution Regions</span></span>](constrained-execution-regions.md)  
 <span data-ttu-id="1807b-118">描述限制的執行區域 (CER) 的功能和行為。</span><span class="sxs-lookup"><span data-stu-id="1807b-118">Describes the function and behavior of constrained execution regions (CERs).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1807b-119">參考</span><span class="sxs-lookup"><span data-stu-id="1807b-119">Reference</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
