---
title: WCF 所需的作業系統資源
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 4522f1c59c8f74281a0e197338c6206ab29c229b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498640"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="e9575-102">WCF 所需的作業系統資源</span><span class="sxs-lookup"><span data-stu-id="e9575-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="e9575-103">Windows Communication Foundation (WCF) 取決於數個作業系統運作所提供的資源。</span><span class="sxs-lookup"><span data-stu-id="e9575-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="e9575-104">下列表格列出這些資源。</span><span class="sxs-lookup"><span data-stu-id="e9575-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="e9575-105">資源</span><span class="sxs-lookup"><span data-stu-id="e9575-105">Resource</span></span>|<span data-ttu-id="e9575-106">描述</span><span class="sxs-lookup"><span data-stu-id="e9575-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="e9575-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="e9575-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="e9575-108">支援 OleTx 交易時需要。</span><span class="sxs-lookup"><span data-stu-id="e9575-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="e9575-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="e9575-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="e9575-110">如果您要使用 IIS 裝載應用程式時需要。</span><span class="sxs-lookup"><span data-stu-id="e9575-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="e9575-111">Windows Process Activation Service (WAS)</span><span class="sxs-lookup"><span data-stu-id="e9575-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="e9575-112">如果您要使用 WAS 裝載應用程式時需要。</span><span class="sxs-lookup"><span data-stu-id="e9575-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9575-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9575-113">See Also</span></span>  
 [<span data-ttu-id="e9575-114">系統需求</span><span class="sxs-lookup"><span data-stu-id="e9575-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
