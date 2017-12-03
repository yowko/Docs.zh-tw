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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31006331f5e8a71bf3f4fb9a68c31cb32d0b6f2b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="970a9-102">WCF 所需的作業系統資源</span><span class="sxs-lookup"><span data-stu-id="970a9-102">Operating System Resources Required by WCF</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="970a9-103"> 視作業系統提供給函式的數個資源而定。</span><span class="sxs-lookup"><span data-stu-id="970a9-103"> depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="970a9-104">下列表格列出這些資源。</span><span class="sxs-lookup"><span data-stu-id="970a9-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="970a9-105">資源</span><span class="sxs-lookup"><span data-stu-id="970a9-105">Resource</span></span>|<span data-ttu-id="970a9-106">描述</span><span class="sxs-lookup"><span data-stu-id="970a9-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="970a9-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="970a9-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="970a9-108">支援 OleTx 交易時需要。</span><span class="sxs-lookup"><span data-stu-id="970a9-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="970a9-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="970a9-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="970a9-110">如果您要使用 IIS 裝載應用程式時需要。</span><span class="sxs-lookup"><span data-stu-id="970a9-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="970a9-111">Windows Process Activation Service (WAS)</span><span class="sxs-lookup"><span data-stu-id="970a9-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="970a9-112">如果您要使用 WAS 裝載應用程式時需要。</span><span class="sxs-lookup"><span data-stu-id="970a9-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="970a9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="970a9-113">See Also</span></span>  
 [<span data-ttu-id="970a9-114">系統需求</span><span class="sxs-lookup"><span data-stu-id="970a9-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
