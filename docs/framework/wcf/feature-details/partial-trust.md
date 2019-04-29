---
title: 部分信任
ms.date: 03/30/2017
ms.assetid: 489b1587-9909-4d0e-8c1a-5e83c8f8292b
ms.openlocfilehash: a6bdcd4424670b18a81d8fa274f213ef4be4c2c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769547"
---
# <a name="partial-trust"></a><span data-ttu-id="b0f4b-102">部分信任</span><span class="sxs-lookup"><span data-stu-id="b0f4b-102">Partial Trust</span></span>
<span data-ttu-id="b0f4b-103">從 [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]開始，部分信任的呼叫端可以存取在 <xref:System.ServiceModel>、<xref:System.Runtime.Serialization> 和 <xref:System.ServiceModel.Web> 中實作的公用型別與方法。</span><span class="sxs-lookup"><span data-stu-id="b0f4b-103">Starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)], partially trusted callers can access public types and methods implemented in <xref:System.ServiceModel>, <xref:System.Runtime.Serialization>, and <xref:System.ServiceModel.Web>.</span></span> <span data-ttu-id="b0f4b-104">本節說明在部分信任的應用程式，以及提供精簡的程式碼存取安全性 (CAS) 執行的應用程式的 WCF 功能的有限的子集內使用 Windows Communication Foundation (WCF) 的支援的案例權限。</span><span class="sxs-lookup"><span data-stu-id="b0f4b-104">This section describes supported scenarios for using Windows Communication Foundation (WCF) within a partially trusted application as well as the limited subset of WCF functionality available to applications running with reduced code access security (CAS) permissions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b0f4b-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="b0f4b-105">In This Section</span></span>  
 [<span data-ttu-id="b0f4b-106">支援的部署案例</span><span class="sxs-lookup"><span data-stu-id="b0f4b-106">Supported Deployment Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)  
 <span data-ttu-id="b0f4b-107">說明執行 WCF 的主要部分信任案例。</span><span class="sxs-lookup"><span data-stu-id="b0f4b-107">Describes the main partial trust scenarios for running WCF.</span></span>  
  
 [<span data-ttu-id="b0f4b-108">部分信任功能相容性</span><span class="sxs-lookup"><span data-stu-id="b0f4b-108">Partial Trust Feature Compatibility</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md)  
 <span data-ttu-id="b0f4b-109">描述不能搭配部分信任的 WCF 功能。</span><span class="sxs-lookup"><span data-stu-id="b0f4b-109">Describes the WCF features that cannot be used with partial trust.</span></span>  
  
 [<span data-ttu-id="b0f4b-110">部分信任最佳做法</span><span class="sxs-lookup"><span data-stu-id="b0f4b-110">Partial Trust Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)  
 <span data-ttu-id="b0f4b-111">包含在部分信任的應用程式中使用 WCF 的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="b0f4b-111">Contains best practices for using WCF in partially trusted applications.</span></span>
