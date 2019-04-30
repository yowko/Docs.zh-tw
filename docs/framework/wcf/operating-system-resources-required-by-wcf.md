---
title: WCF 所需的作業系統資源
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 828d656370efd7638fa4cf367b84ee7b316b89bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955216"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="954dd-102">WCF 所需的作業系統資源</span><span class="sxs-lookup"><span data-stu-id="954dd-102">Operating System Resources Required by WCF</span></span>
<span data-ttu-id="954dd-103">Windows Communication Foundation (WCF) 取決於所提供的函式作業系統的幾個資源。</span><span class="sxs-lookup"><span data-stu-id="954dd-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="954dd-104">下列表格列出這些資源。</span><span class="sxs-lookup"><span data-stu-id="954dd-104">The following table lists those resources.</span></span>  
  
|<span data-ttu-id="954dd-105">資源</span><span class="sxs-lookup"><span data-stu-id="954dd-105">Resource</span></span>|<span data-ttu-id="954dd-106">描述</span><span class="sxs-lookup"><span data-stu-id="954dd-106">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="954dd-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="954dd-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="954dd-108">支援 OleTx 異動時需要。</span><span class="sxs-lookup"><span data-stu-id="954dd-108">Required to support OleTx transactions.</span></span>|  
|<span data-ttu-id="954dd-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="954dd-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="954dd-110">如果您要使用 IIS 裝載應用程式時需要。</span><span class="sxs-lookup"><span data-stu-id="954dd-110">Required if you want to use IIS to host your application.</span></span>|  
|<span data-ttu-id="954dd-111">Windows Process Activation Service (WAS)</span><span class="sxs-lookup"><span data-stu-id="954dd-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="954dd-112">如果您要使用 WAS 裝載應用程式時需要。</span><span class="sxs-lookup"><span data-stu-id="954dd-112">Required if you want to use WAS to host your application.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="954dd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="954dd-113">See also</span></span>

- [<span data-ttu-id="954dd-114">系統需求</span><span class="sxs-lookup"><span data-stu-id="954dd-114">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)
