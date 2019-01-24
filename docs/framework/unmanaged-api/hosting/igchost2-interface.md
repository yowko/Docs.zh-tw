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
ms.openlocfilehash: 742f738ca1a147c75b976d24fa4ac8e7fa4947c4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622230"
---
# <a name="igchost2-interface"></a><span data-ttu-id="d6670-102">IGCHost2 介面</span><span class="sxs-lookup"><span data-stu-id="d6670-102">IGCHost2 Interface</span></span>
<span data-ttu-id="d6670-103">提供方法來取得記憶體回收系統的相關資訊，以及控制記憶體回收的某些層面。</span><span class="sxs-lookup"><span data-stu-id="d6670-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6670-104">新的程式開發，我們建議您使用[ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)改為介面。</span><span class="sxs-lookup"><span data-stu-id="d6670-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d6670-105">方法</span><span class="sxs-lookup"><span data-stu-id="d6670-105">Methods</span></span>  
  
|<span data-ttu-id="d6670-106">方法</span><span class="sxs-lookup"><span data-stu-id="d6670-106">Method</span></span>|<span data-ttu-id="d6670-107">描述</span><span class="sxs-lookup"><span data-stu-id="d6670-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d6670-108">SetGCStartupLimitsEx 方法</span><span class="sxs-lookup"><span data-stu-id="d6670-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="d6670-109">層代 0 設定區段的大小和大小上限。</span><span class="sxs-lookup"><span data-stu-id="d6670-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="d6670-110">可讓第 0 代和區段大小大於`DWORD`。</span><span class="sxs-lookup"><span data-stu-id="d6670-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6670-111">需求</span><span class="sxs-lookup"><span data-stu-id="d6670-111">Requirements</span></span>  
 <span data-ttu-id="d6670-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6670-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6670-113">**標頭：** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="d6670-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="d6670-114">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d6670-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6670-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6670-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6670-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6670-116">See also</span></span>
- [<span data-ttu-id="d6670-117">裝載介面</span><span class="sxs-lookup"><span data-stu-id="d6670-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="d6670-118">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="d6670-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="d6670-119">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="d6670-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
