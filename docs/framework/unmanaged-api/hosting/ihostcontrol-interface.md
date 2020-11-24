---
title: IHostControl 介面
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: 1bffef31702aa051d9ca865b18a67ac90c00cd00
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680650"
---
# <a name="ihostcontrol-interface"></a><span data-ttu-id="309e3-102">IHostControl 介面</span><span class="sxs-lookup"><span data-stu-id="309e3-102">IHostControl Interface</span></span>

<span data-ttu-id="309e3-103">提供方法來設定元件的載入，以及判斷主機所支援的裝載介面。</span><span class="sxs-lookup"><span data-stu-id="309e3-103">Provides methods for configuring the loading of assemblies, and for determining which hosting interfaces the host supports.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="309e3-104">方法</span><span class="sxs-lookup"><span data-stu-id="309e3-104">Methods</span></span>  
  
|<span data-ttu-id="309e3-105">方法</span><span class="sxs-lookup"><span data-stu-id="309e3-105">Method</span></span>|<span data-ttu-id="309e3-106">描述</span><span class="sxs-lookup"><span data-stu-id="309e3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="309e3-107">GetHostManager 方法</span><span class="sxs-lookup"><span data-stu-id="309e3-107">GetHostManager Method</span></span>](ihostcontrol-gethostmanager-method.md)|<span data-ttu-id="309e3-108">取得具有指定之介面的主機實介面指標 `IID` 。</span><span class="sxs-lookup"><span data-stu-id="309e3-108">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>|  
|[<span data-ttu-id="309e3-109">SetAppDomainManager 方法</span><span class="sxs-lookup"><span data-stu-id="309e3-109">SetAppDomainManager Method</span></span>](ihostcontrol-setappdomainmanager-method.md)|<span data-ttu-id="309e3-110">通知主機已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="309e3-110">Notifies the host that an application domain has been created.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="309e3-111">需求</span><span class="sxs-lookup"><span data-stu-id="309e3-111">Requirements</span></span>  

 <span data-ttu-id="309e3-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="309e3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="309e3-113">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="309e3-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="309e3-114">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="309e3-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="309e3-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="309e3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="309e3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="309e3-116">See also</span></span>

- <xref:System.AppDomainManager>
- [<span data-ttu-id="309e3-117">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="309e3-117">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="309e3-118">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="309e3-118">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="309e3-119">裝載介面</span><span class="sxs-lookup"><span data-stu-id="309e3-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
