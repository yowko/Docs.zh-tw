---
title: "方針及最佳作法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, guidelines
- best practices [WCF], application design
- Windows Communication Foundation, best practices
- WCF, best practices
- Windows Communication Foundation, guidelines
ms.assetid: 5098ba46-6e8d-4e02-b0c5-d737f9fdad84
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6dc6ad423010cf881c62e2c22570c080cad6a1e0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="guidelines-and-best-practices"></a><span data-ttu-id="cfc3e-102">方針及最佳作法</span><span class="sxs-lookup"><span data-stu-id="cfc3e-102">Guidelines and Best Practices</span></span>
<span data-ttu-id="cfc3e-103">本章節所包含的主題，提供建立 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 應用程式的方針。</span><span class="sxs-lookup"><span data-stu-id="cfc3e-103">This section contains topics that provide guidelines for creating [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cfc3e-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="cfc3e-104">In This Section</span></span>  
 [<span data-ttu-id="cfc3e-105">最佳做法：資料合約版本設定</span><span class="sxs-lookup"><span data-stu-id="cfc3e-105">Best Practices: Data Contract Versioning</span></span>](../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 <span data-ttu-id="cfc3e-106">說明如何及何時建立不會在未來版本建立時中斷的資料合約。</span><span class="sxs-lookup"><span data-stu-id="cfc3e-106">Explains how and when to create data contracts that do not break when future versions are created.</span></span>  
  
 [<span data-ttu-id="cfc3e-107">服務版本設定</span><span class="sxs-lookup"><span data-stu-id="cfc3e-107">Service Versioning</span></span>](../../../docs/framework/wcf/service-versioning.md)  
 <span data-ttu-id="cfc3e-108">說明如何考量 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 內的版本控制。</span><span class="sxs-lookup"><span data-stu-id="cfc3e-108">Explains how to consider versioning in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="cfc3e-109">部署之後，服務 (及其公開的端點) 可能必須予以變更，例如，為了滿足商務需求或 IT 需求的變更，或者為了修復問題。</span><span class="sxs-lookup"><span data-stu-id="cfc3e-109">After deployment, services (and the endpoints they expose) might need to be changed, for example, to satisfy changing business requirements or IT requirements, or to fix issues.</span></span> <span data-ttu-id="cfc3e-110">每個變更都會產生新的服務版本。</span><span class="sxs-lookup"><span data-stu-id="cfc3e-110">Each change introduces a new version of the service.</span></span>  
  
 [<span data-ttu-id="cfc3e-111">負載平衡</span><span class="sxs-lookup"><span data-stu-id="cfc3e-111">Load Balancing</span></span>](../../../docs/framework/wcf/load-balancing.md)  
 <span data-ttu-id="cfc3e-112">列出使用 Web 伺服陣列的負載平衡方針。</span><span class="sxs-lookup"><span data-stu-id="cfc3e-112">Lists guidelines for load balancing with a Web farm.</span></span>  
  
 [<span data-ttu-id="cfc3e-113">控制資源使用並改善效能</span><span class="sxs-lookup"><span data-stu-id="cfc3e-113">Controlling Resource Consumption and Improving Performance</span></span>](../../../docs/framework/wcf/controlling-resource-consumption-and-improving-performance.md)  
 <span data-ttu-id="cfc3e-114">說明為了防止過度消耗資源及改善安全性，並指出有關其使用之完整資訊而設計的屬性。</span><span class="sxs-lookup"><span data-stu-id="cfc3e-114">Describes the properties that are designed to help prevent undue resource consumption and improve security and points to more complete information about their use.</span></span>  
  
 [<span data-ttu-id="cfc3e-115">利用 ClickOnce 部署 WCF 應用程式</span><span class="sxs-lookup"><span data-stu-id="cfc3e-115">Deploying WCF Applications with ClickOnce</span></span>](../../../docs/framework/wcf/deploying-wcf-applications-with-clickonce.md)  
 <span data-ttu-id="cfc3e-116">說明使用 ClickOnce 功能時所需考量的事項。</span><span class="sxs-lookup"><span data-stu-id="cfc3e-116">Describes the considerations to be made when using the ClickOnce feature.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="cfc3e-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="cfc3e-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="cfc3e-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="cfc3e-118">Related Sections</span></span>  
 [<span data-ttu-id="cfc3e-119">概念性概觀</span><span class="sxs-lookup"><span data-stu-id="cfc3e-119">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
  
 [<span data-ttu-id="cfc3e-120">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="cfc3e-120">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="cfc3e-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="cfc3e-121">See Also</span></span>  
 [<span data-ttu-id="cfc3e-122">什麼是 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="cfc3e-122">What Is Windows Communication Foundation</span></span>](../../../docs/framework/wcf/whats-wcf.md)  
 [<span data-ttu-id="cfc3e-123">Windows Communication Foundation 範例</span><span class="sxs-lookup"><span data-stu-id="cfc3e-123">Windows Communication Foundation Samples</span></span>](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
 [<span data-ttu-id="cfc3e-124">概念性概觀</span><span class="sxs-lookup"><span data-stu-id="cfc3e-124">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
 [<span data-ttu-id="cfc3e-125">建置用戶端</span><span class="sxs-lookup"><span data-stu-id="cfc3e-125">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)
