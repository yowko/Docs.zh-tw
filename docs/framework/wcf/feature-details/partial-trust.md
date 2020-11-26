---
title: 部分信任
ms.date: 03/30/2017
ms.assetid: 489b1587-9909-4d0e-8c1a-5e83c8f8292b
ms.openlocfilehash: 844fa65bbb2858fc961091614ba581265bc08be5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247963"
---
# <a name="partial-trust"></a><span data-ttu-id="25e2a-102">部分信任</span><span class="sxs-lookup"><span data-stu-id="25e2a-102">Partial Trust</span></span>

<span data-ttu-id="25e2a-103">從 .NET Framework 3.5 開始，部分信任的呼叫端可以存取在、和中執行的公用類型和方法 <xref:System.ServiceModel> <xref:System.Runtime.Serialization> <xref:System.ServiceModel.Web> 。</span><span class="sxs-lookup"><span data-stu-id="25e2a-103">Starting with the .NET Framework 3.5, partially trusted callers can access public types and methods implemented in <xref:System.ServiceModel>, <xref:System.Runtime.Serialization>, and <xref:System.ServiceModel.Web>.</span></span> <span data-ttu-id="25e2a-104">本節說明在部分信任應用程式中使用 Windows Communication Foundation (WCF) 的支援案例，以及可供使用較少代碼啟用安全性 (CAS) 許可權的應用程式使用的有限 WCF 功能子集。</span><span class="sxs-lookup"><span data-stu-id="25e2a-104">This section describes supported scenarios for using Windows Communication Foundation (WCF) within a partially trusted application as well as the limited subset of WCF functionality available to applications running with reduced code access security (CAS) permissions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="25e2a-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="25e2a-105">In This Section</span></span>  

 [<span data-ttu-id="25e2a-106">支援的部署案例</span><span class="sxs-lookup"><span data-stu-id="25e2a-106">Supported Deployment Scenarios</span></span>](supported-deployment-scenarios.md)  
 <span data-ttu-id="25e2a-107">描述執行 WCF 的主要部分信任案例。</span><span class="sxs-lookup"><span data-stu-id="25e2a-107">Describes the main partial trust scenarios for running WCF.</span></span>  
  
 [<span data-ttu-id="25e2a-108">部分信任功能相容性</span><span class="sxs-lookup"><span data-stu-id="25e2a-108">Partial Trust Feature Compatibility</span></span>](partial-trust-feature-compatibility.md)  
 <span data-ttu-id="25e2a-109">描述無法搭配部分信任使用的 WCF 功能。</span><span class="sxs-lookup"><span data-stu-id="25e2a-109">Describes the WCF features that cannot be used with partial trust.</span></span>  
  
 [<span data-ttu-id="25e2a-110">部分信任最佳做法</span><span class="sxs-lookup"><span data-stu-id="25e2a-110">Partial Trust Best Practices</span></span>](partial-trust-best-practices.md)  
 <span data-ttu-id="25e2a-111">包含在部分信任應用程式中使用 WCF 的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="25e2a-111">Contains best practices for using WCF in partially trusted applications.</span></span>
