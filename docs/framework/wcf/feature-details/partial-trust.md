---
title: "部分信任"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489b1587-9909-4d0e-8c1a-5e83c8f8292b
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f3febf1f3703377806493c8067b50c149bce0108
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="partial-trust"></a><span data-ttu-id="d7944-102">部分信任</span><span class="sxs-lookup"><span data-stu-id="d7944-102">Partial Trust</span></span>
<span data-ttu-id="d7944-103">從 [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]開始，部分信任的呼叫端可以存取在 <xref:System.ServiceModel>、<xref:System.Runtime.Serialization> 和 <xref:System.ServiceModel.Web> 中實作的公用型別與方法。</span><span class="sxs-lookup"><span data-stu-id="d7944-103">Starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)], partially trusted callers can access public types and methods implemented in <xref:System.ServiceModel>, <xref:System.Runtime.Serialization>, and <xref:System.ServiceModel.Web>.</span></span> <span data-ttu-id="d7944-104">本節說明在部分信任的應用程式中使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]，以及使用有限的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 功能子集 (提供以較低程式碼存取安全性 (CAS) 使用權限來執行的應用程式使用) 時的一些支援案例。</span><span class="sxs-lookup"><span data-stu-id="d7944-104">This section describes supported scenarios for using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] within a partially trusted application as well as the limited subset of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] functionality available to applications running with reduced code access security (CAS) permissions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7944-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="d7944-105">In This Section</span></span>  
 [<span data-ttu-id="d7944-106">支援的部署案例</span><span class="sxs-lookup"><span data-stu-id="d7944-106">Supported Deployment Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)  
 <span data-ttu-id="d7944-107">說明執行 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 時的主要部分信任案例。</span><span class="sxs-lookup"><span data-stu-id="d7944-107">Describes the main partial trust scenarios for running [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="d7944-108">部分信任功能相容性</span><span class="sxs-lookup"><span data-stu-id="d7944-108">Partial Trust Feature Compatibility</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust-feature-compatibility.md)  
 <span data-ttu-id="d7944-109">說明無法搭配使用部分信任的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="d7944-109">Describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] features that cannot be used with partial trust.</span></span>  
  
 [<span data-ttu-id="d7944-110">部分信任最佳做法</span><span class="sxs-lookup"><span data-stu-id="d7944-110">Partial Trust Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)  
 <span data-ttu-id="d7944-111">包含在部分信任應用程式中使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="d7944-111">Contains best practices for using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in partially trusted applications.</span></span>
