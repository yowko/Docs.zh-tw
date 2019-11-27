---
title: 部分信任
ms.date: 03/30/2017
ms.assetid: 489b1587-9909-4d0e-8c1a-5e83c8f8292b
ms.openlocfilehash: fa496718d6c2a7f725c880d932c48d0f5d4bb7a4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283318"
---
# <a name="partial-trust"></a><span data-ttu-id="4dddc-102">部分信任</span><span class="sxs-lookup"><span data-stu-id="4dddc-102">Partial Trust</span></span>

<span data-ttu-id="4dddc-103">從 .NET Framework 3.5 開始，部分信任的呼叫端可以存取在 <xref:System.ServiceModel>、<xref:System.Runtime.Serialization>和 <xref:System.ServiceModel.Web>中執行的公用類型和方法。</span><span class="sxs-lookup"><span data-stu-id="4dddc-103">Starting with the .NET Framework 3.5, partially trusted callers can access public types and methods implemented in <xref:System.ServiceModel>, <xref:System.Runtime.Serialization>, and <xref:System.ServiceModel.Web>.</span></span> <span data-ttu-id="4dddc-104">本節說明在部分信任的應用程式中使用 Windows Communication Foundation （WCF）的支援案例，以及可用於以較低代碼啟用安全性（CAS）執行的應用程式所提供的有限 WCF 功能子集無權.</span><span class="sxs-lookup"><span data-stu-id="4dddc-104">This section describes supported scenarios for using Windows Communication Foundation (WCF) within a partially trusted application as well as the limited subset of WCF functionality available to applications running with reduced code access security (CAS) permissions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4dddc-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="4dddc-105">In This Section</span></span>  
 [<span data-ttu-id="4dddc-106">支援的部署案例</span><span class="sxs-lookup"><span data-stu-id="4dddc-106">Supported Deployment Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)  
 <span data-ttu-id="4dddc-107">描述執行 WCF 的主要部分信任案例。</span><span class="sxs-lookup"><span data-stu-id="4dddc-107">Describes the main partial trust scenarios for running WCF.</span></span>  
  
 [<span data-ttu-id="4dddc-108">部分信任功能相容性</span><span class="sxs-lookup"><span data-stu-id="4dddc-108">Partial Trust Feature Compatibility</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md)  
 <span data-ttu-id="4dddc-109">描述無法搭配部分信任使用的 WCF 功能。</span><span class="sxs-lookup"><span data-stu-id="4dddc-109">Describes the WCF features that cannot be used with partial trust.</span></span>  
  
 [<span data-ttu-id="4dddc-110">Partial Trust Best Practices</span><span class="sxs-lookup"><span data-stu-id="4dddc-110">Partial Trust Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)  
 <span data-ttu-id="4dddc-111">包含在部分信任的應用程式中使用 WCF 的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="4dddc-111">Contains best practices for using WCF in partially trusted applications.</span></span>
