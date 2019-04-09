---
title: IGCHost2 介面
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75bef91eb70c8109653741452362cd2e85f625ce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138134"
---
# <a name="igchost2-interface"></a><span data-ttu-id="6c5f2-102">IGCHost2 介面</span><span class="sxs-lookup"><span data-stu-id="6c5f2-102">IGCHost2 Interface</span></span>
<span data-ttu-id="6c5f2-103">提供方法來取得記憶體回收系統的相關資訊，以及控制記憶體回收的某些層面。</span><span class="sxs-lookup"><span data-stu-id="6c5f2-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c5f2-104">新的程式開發，我們建議您使用[ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)改為介面。</span><span class="sxs-lookup"><span data-stu-id="6c5f2-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c5f2-105">方法</span><span class="sxs-lookup"><span data-stu-id="6c5f2-105">Methods</span></span>  
  
|<span data-ttu-id="6c5f2-106">方法</span><span class="sxs-lookup"><span data-stu-id="6c5f2-106">Method</span></span>|<span data-ttu-id="6c5f2-107">描述</span><span class="sxs-lookup"><span data-stu-id="6c5f2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c5f2-108">SetGCStartupLimitsEx 方法</span><span class="sxs-lookup"><span data-stu-id="6c5f2-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="6c5f2-109">層代 0 設定區段的大小和大小上限。</span><span class="sxs-lookup"><span data-stu-id="6c5f2-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="6c5f2-110">可讓第 0 代和區段大小大於`DWORD`。</span><span class="sxs-lookup"><span data-stu-id="6c5f2-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6c5f2-111">需求</span><span class="sxs-lookup"><span data-stu-id="6c5f2-111">Requirements</span></span>  
 <span data-ttu-id="6c5f2-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c5f2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c5f2-113">**標頭：** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="6c5f2-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="6c5f2-114">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6c5f2-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6c5f2-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="6c5f2-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6c5f2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c5f2-116">See also</span></span>

- [<span data-ttu-id="6c5f2-117">裝載介面</span><span class="sxs-lookup"><span data-stu-id="6c5f2-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="6c5f2-118">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="6c5f2-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="6c5f2-119">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="6c5f2-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
