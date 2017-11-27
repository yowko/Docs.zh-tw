---
title: "WCF 所需的作業系統資源"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6cfe114e5e044a6aaa1e356194a46b4a46011aa0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="bb9ad-102">WCF 所需的作業系統資源</span><span class="sxs-lookup"><span data-stu-id="bb9ad-102">Operating System Resources Required by WCF</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="bb9ad-103"> 視作業系統提供給函式的數個資源而定。</span><span class="sxs-lookup"><span data-stu-id="bb9ad-103"> depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="bb9ad-104">下列表格列出這些資源。</span><span class="sxs-lookup"><span data-stu-id="bb9ad-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="bb9ad-105">資源</span><span class="sxs-lookup"><span data-stu-id="bb9ad-105">Resource</span></span>|<span data-ttu-id="bb9ad-106">描述</span><span class="sxs-lookup"><span data-stu-id="bb9ad-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="bb9ad-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="bb9ad-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="bb9ad-108">支援 OleTx 交易時需要。</span><span class="sxs-lookup"><span data-stu-id="bb9ad-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="bb9ad-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="bb9ad-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="bb9ad-110">如果您要使用 IIS 裝載應用程式時需要。</span><span class="sxs-lookup"><span data-stu-id="bb9ad-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="bb9ad-111">Windows Process Activation Service (WAS)</span><span class="sxs-lookup"><span data-stu-id="bb9ad-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="bb9ad-112">如果您要使用 WAS 裝載應用程式時需要。</span><span class="sxs-lookup"><span data-stu-id="bb9ad-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb9ad-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb9ad-113">See Also</span></span>  
 [<span data-ttu-id="bb9ad-114">系統需求</span><span class="sxs-lookup"><span data-stu-id="bb9ad-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
