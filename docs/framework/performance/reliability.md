---
title: 可靠性
ms.date: 03/30/2017
helpviewer_keywords:
- SQL Server [.NET Framework]
- managed code, reliability
- reliability [.NET Framework]
- writing reliable code
- code, reliability
ms.assetid: 294aa306-0afe-4cbe-b397-86ba9f1860f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: acb84c6617cdffabfe276895f81e7df2b04bb8bb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046241"
---
# <a name="reliability"></a><span data-ttu-id="8318f-102">可靠性</span><span class="sxs-lookup"><span data-stu-id="8318f-102">Reliability</span></span>
<span data-ttu-id="8318f-103">重要的是，在 SQL Server 這類伺服器環境中執行的程式碼可防止發生非同步例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8318f-103">It is important that code executing in server environments such as SQL Server protect against asynchronous exceptions.</span></span> <span data-ttu-id="8318f-104">如這裡所討論，可靠性不是 SQL Server 特有的，而是針對任何在 .NET Framework 2.0 版環境中執行的主機撰寫可靠程式碼。</span><span class="sxs-lookup"><span data-stu-id="8318f-104">Reliability, as discussed here, is not specific to SQL Server but to writing reliable code for any host executing in a .NET Framework version 2.0 environment.</span></span> <span data-ttu-id="8318f-105">不過，SQL Server 是大規模使用 2.0 版新可靠性功能的第一個服務，因此當成範例使用。</span><span class="sxs-lookup"><span data-stu-id="8318f-105">However, SQL Server is the first service making extensive use of the new reliability features of version 2.0, so it is used as an example.</span></span>  
  
 <span data-ttu-id="8318f-106">在 SQL Server 中執行的程式碼必須處理比其他伺服器環境更嚴格的可靠性方針。</span><span class="sxs-lookup"><span data-stu-id="8318f-106">Code running in SQL Server must deal with more stringent reliability guidelines than other server environments.</span></span> <span data-ttu-id="8318f-107">這是因為 SQL Server 的穩定作業處於資源耗用邊緣。</span><span class="sxs-lookup"><span data-stu-id="8318f-107">This is due to SQL Server’s steady operation at the edge of resource consumption.</span></span>  <span data-ttu-id="8318f-108">在 SQL Server 環境中，<xref:System.OutOfMemoryException> 和 <xref:System.Threading.ThreadAbortException> 例外狀況並不常見。</span><span class="sxs-lookup"><span data-stu-id="8318f-108"><xref:System.OutOfMemoryException> and <xref:System.Threading.ThreadAbortException> exceptions are not uncommon in the SQL Server environment.</span></span> <span data-ttu-id="8318f-109">這些方針一般較不著重可靠性，但較著重允許完全受信任的 Managed 程式碼在面對 <xref:System.AppDomain> 層級回收時依正常程序失敗，而這是伺服器維護一致性和可用性的主要方式。</span><span class="sxs-lookup"><span data-stu-id="8318f-109">These guidelines in general are focused less on reliability and more on allowing fully trusted managed code to fail gracefully in the face of <xref:System.AppDomain>-level recycling, which is the primary way the server maintains consistency and availability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8318f-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="8318f-110">In This Section</span></span>  
 [<span data-ttu-id="8318f-111">SQL Server 程式設計和主機保護屬性</span><span class="sxs-lookup"><span data-stu-id="8318f-111">SQL Server Programming and Host Protection Attributes</span></span>](sql-server-programming-and-host-protection-attributes.md)  
 <span data-ttu-id="8318f-112">描述 SQL Server 如何使用 <xref:System.Security.Permissions.HostProtectionAttribute> 屬性來限制 Managed 程式碼的執行。</span><span class="sxs-lookup"><span data-stu-id="8318f-112">Describes how the <xref:System.Security.Permissions.HostProtectionAttribute> attribute is used by SQL Server to restrict the execution of managed code.</span></span>  
  
 [<span data-ttu-id="8318f-113">可靠性最佳做法</span><span class="sxs-lookup"><span data-stu-id="8318f-113">Reliability Best Practices</span></span>](reliability-best-practices.md)  
 <span data-ttu-id="8318f-114">提供撰寫符合可靠性需求之程式碼的方針。</span><span class="sxs-lookup"><span data-stu-id="8318f-114">Provides guidelines for writing code that meets reliability requirements.</span></span>  
  
 [<span data-ttu-id="8318f-115">限制的執行區域</span><span class="sxs-lookup"><span data-stu-id="8318f-115">Constrained Execution Regions</span></span>](constrained-execution-regions.md)  
 <span data-ttu-id="8318f-116">描述限制的執行區域 (CER) 的功能和行為。</span><span class="sxs-lookup"><span data-stu-id="8318f-116">Describes the function and behavior of constrained execution regions (CERs).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8318f-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="8318f-117">Reference</span></span>  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
  
 <xref:System.Security.Permissions.HostProtectionResource>
