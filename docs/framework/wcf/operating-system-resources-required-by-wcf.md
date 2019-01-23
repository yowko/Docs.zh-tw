---
title: WCF 所需的作業系統資源
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 759ab099066e300484860cf3f91d6d084ba1d339
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527077"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="6d3e4-102">WCF 所需的作業系統資源</span><span class="sxs-lookup"><span data-stu-id="6d3e4-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="6d3e4-103">Windows Communication Foundation (WCF) 取決於所提供的函式作業系統的幾個資源。</span><span class="sxs-lookup"><span data-stu-id="6d3e4-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="6d3e4-104">下列表格列出這些資源。</span><span class="sxs-lookup"><span data-stu-id="6d3e4-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="6d3e4-105">資源</span><span class="sxs-lookup"><span data-stu-id="6d3e4-105">Resource</span></span>|<span data-ttu-id="6d3e4-106">描述</span><span class="sxs-lookup"><span data-stu-id="6d3e4-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="6d3e4-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="6d3e4-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="6d3e4-108">支援 OleTx 交易時需要。</span><span class="sxs-lookup"><span data-stu-id="6d3e4-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="6d3e4-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="6d3e4-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="6d3e4-110">如果您要使用 IIS 裝載應用程式時需要。</span><span class="sxs-lookup"><span data-stu-id="6d3e4-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="6d3e4-111">Windows Process Activation Service (WAS)</span><span class="sxs-lookup"><span data-stu-id="6d3e4-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="6d3e4-112">如果您要使用 WAS 裝載應用程式時需要。</span><span class="sxs-lookup"><span data-stu-id="6d3e4-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d3e4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d3e4-113">See also</span></span>
- [<span data-ttu-id="6d3e4-114">系統需求</span><span class="sxs-lookup"><span data-stu-id="6d3e4-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
