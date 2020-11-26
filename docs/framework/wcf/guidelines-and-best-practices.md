---
title: 方針及最佳作法
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, guidelines
- best practices [WCF], application design
- Windows Communication Foundation, best practices
- WCF, best practices
- Windows Communication Foundation, guidelines
ms.assetid: 5098ba46-6e8d-4e02-b0c5-d737f9fdad84
ms.openlocfilehash: eeca4ee47db2aef139567e37cba60cab863e6d53
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238128"
---
# <a name="guidelines-and-best-practices"></a><span data-ttu-id="2a3fd-102">方針及最佳作法</span><span class="sxs-lookup"><span data-stu-id="2a3fd-102">Guidelines and Best Practices</span></span>

<span data-ttu-id="2a3fd-103">本章節包含的主題會提供建立 Windows Communication Foundation (WCF) 應用程式的指導方針。</span><span class="sxs-lookup"><span data-stu-id="2a3fd-103">This section contains topics that provide guidelines for creating Windows Communication Foundation (WCF) applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2a3fd-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="2a3fd-104">In This Section</span></span>  

 [<span data-ttu-id="2a3fd-105">最佳做法：資料合約版本控制</span><span class="sxs-lookup"><span data-stu-id="2a3fd-105">Best Practices: Data Contract Versioning</span></span>](best-practices-data-contract-versioning.md)  
 <span data-ttu-id="2a3fd-106">說明如何及何時建立不會在未來版本建立時中斷的資料合約。</span><span class="sxs-lookup"><span data-stu-id="2a3fd-106">Explains how and when to create data contracts that do not break when future versions are created.</span></span>  
  
 [<span data-ttu-id="2a3fd-107">服務版本控制</span><span class="sxs-lookup"><span data-stu-id="2a3fd-107">Service Versioning</span></span>](service-versioning.md)  
 <span data-ttu-id="2a3fd-108">說明如何考慮 WCF 中的版本設定。</span><span class="sxs-lookup"><span data-stu-id="2a3fd-108">Explains how to consider versioning in WCF.</span></span> <span data-ttu-id="2a3fd-109">部署之後，服務 (及其公開的端點) 可能必須予以變更，例如，為了滿足商務需求或 IT 需求的變更，或者為了修復問題。</span><span class="sxs-lookup"><span data-stu-id="2a3fd-109">After deployment, services (and the endpoints they expose) might need to be changed, for example, to satisfy changing business requirements or IT requirements, or to fix issues.</span></span> <span data-ttu-id="2a3fd-110">每個變更都會產生新的服務版本。</span><span class="sxs-lookup"><span data-stu-id="2a3fd-110">Each change introduces a new version of the service.</span></span>  
  
 [<span data-ttu-id="2a3fd-111">負載平衡</span><span class="sxs-lookup"><span data-stu-id="2a3fd-111">Load Balancing</span></span>](load-balancing.md)  
 <span data-ttu-id="2a3fd-112">列出使用 Web 伺服陣列的負載平衡方針。</span><span class="sxs-lookup"><span data-stu-id="2a3fd-112">Lists guidelines for load balancing with a Web farm.</span></span>  
  
 [<span data-ttu-id="2a3fd-113">控制資源使用並改善效能</span><span class="sxs-lookup"><span data-stu-id="2a3fd-113">Controlling Resource Consumption and Improving Performance</span></span>](controlling-resource-consumption-and-improving-performance.md)  
 <span data-ttu-id="2a3fd-114">說明為了防止過度消耗資源及改善安全性，並指出有關其使用之完整資訊而設計的屬性。</span><span class="sxs-lookup"><span data-stu-id="2a3fd-114">Describes the properties that are designed to help prevent undue resource consumption and improve security and points to more complete information about their use.</span></span>  
  
 [<span data-ttu-id="2a3fd-115">使用 ClickOnce 來部署 WCF 應用程式</span><span class="sxs-lookup"><span data-stu-id="2a3fd-115">Deploying WCF Applications with ClickOnce</span></span>](deploying-wcf-applications-with-clickonce.md)  
 <span data-ttu-id="2a3fd-116">說明使用 ClickOnce 功能時所需考量的事項。</span><span class="sxs-lookup"><span data-stu-id="2a3fd-116">Describes the considerations to be made when using the ClickOnce feature.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2a3fd-117">參考</span><span class="sxs-lookup"><span data-stu-id="2a3fd-117">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="2a3fd-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="2a3fd-118">Related Sections</span></span>  

 [<span data-ttu-id="2a3fd-119">概觀說明</span><span class="sxs-lookup"><span data-stu-id="2a3fd-119">Conceptual Overview</span></span>](conceptual-overview.md)  
  
 [<span data-ttu-id="2a3fd-120">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="2a3fd-120">Basic WCF Programming</span></span>](basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="2a3fd-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a3fd-121">See also</span></span>

- [<span data-ttu-id="2a3fd-122">何謂 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="2a3fd-122">What Is Windows Communication Foundation</span></span>](whats-wcf.md)
- [<span data-ttu-id="2a3fd-123">Windows Communication Foundation (WCF) 範例</span><span class="sxs-lookup"><span data-stu-id="2a3fd-123">Windows Communication Foundation (WCF) samples</span></span>](./samples/index.md)
- [<span data-ttu-id="2a3fd-124">概觀說明</span><span class="sxs-lookup"><span data-stu-id="2a3fd-124">Conceptual Overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="2a3fd-125">建置用戶端</span><span class="sxs-lookup"><span data-stu-id="2a3fd-125">Building Clients</span></span>](building-clients.md)
