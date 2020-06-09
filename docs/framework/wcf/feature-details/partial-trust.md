---
title: 部分信任
ms.date: 03/30/2017
ms.assetid: 489b1587-9909-4d0e-8c1a-5e83c8f8292b
ms.openlocfilehash: f4eace87593f2b4c45101bafa0843998a093cbd5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579146"
---
# <a name="partial-trust"></a><span data-ttu-id="6e800-102">部分信任</span><span class="sxs-lookup"><span data-stu-id="6e800-102">Partial Trust</span></span>

<span data-ttu-id="6e800-103">從 .NET Framework 3.5 開始，部分信任的呼叫端可以存取在、和中實作為的公用類型和方法 <xref:System.ServiceModel> <xref:System.Runtime.Serialization> <xref:System.ServiceModel.Web> 。</span><span class="sxs-lookup"><span data-stu-id="6e800-103">Starting with the .NET Framework 3.5, partially trusted callers can access public types and methods implemented in <xref:System.ServiceModel>, <xref:System.Runtime.Serialization>, and <xref:System.ServiceModel.Web>.</span></span> <span data-ttu-id="6e800-104">本節說明在部分信任的應用程式中使用 Windows Communication Foundation （WCF）的支援案例，以及可用於以較低代碼啟用安全性（CAS）許可權來執行之應用程式的有限 WCF 功能子集。</span><span class="sxs-lookup"><span data-stu-id="6e800-104">This section describes supported scenarios for using Windows Communication Foundation (WCF) within a partially trusted application as well as the limited subset of WCF functionality available to applications running with reduced code access security (CAS) permissions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6e800-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="6e800-105">In This Section</span></span>  
 [<span data-ttu-id="6e800-106">Supported Deployment Scenarios</span><span class="sxs-lookup"><span data-stu-id="6e800-106">Supported Deployment Scenarios</span></span>](supported-deployment-scenarios.md)  
 <span data-ttu-id="6e800-107">描述執行 WCF 的主要部分信任案例。</span><span class="sxs-lookup"><span data-stu-id="6e800-107">Describes the main partial trust scenarios for running WCF.</span></span>  
  
 [<span data-ttu-id="6e800-108">部分信任功能相容性</span><span class="sxs-lookup"><span data-stu-id="6e800-108">Partial Trust Feature Compatibility</span></span>](partial-trust-feature-compatibility.md)  
 <span data-ttu-id="6e800-109">描述無法搭配部分信任使用的 WCF 功能。</span><span class="sxs-lookup"><span data-stu-id="6e800-109">Describes the WCF features that cannot be used with partial trust.</span></span>  
  
 [<span data-ttu-id="6e800-110">Partial Trust Best Practices</span><span class="sxs-lookup"><span data-stu-id="6e800-110">Partial Trust Best Practices</span></span>](partial-trust-best-practices.md)  
 <span data-ttu-id="6e800-111">包含在部分信任的應用程式中使用 WCF 的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="6e800-111">Contains best practices for using WCF in partially trusted applications.</span></span>
