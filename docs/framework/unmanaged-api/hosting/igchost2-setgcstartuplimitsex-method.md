---
title: IGCHost2::SetGCStartupLimitsEx 方法
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
ms.openlocfilehash: 4dca62903a123765ceb8bb251b79455ad0e4730a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726804"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="da60e-102">IGCHost2::SetGCStartupLimitsEx 方法</span><span class="sxs-lookup"><span data-stu-id="da60e-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>

<span data-ttu-id="da60e-103">設定層代0的區段大小和大小上限。</span><span class="sxs-lookup"><span data-stu-id="da60e-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da60e-104">語法</span><span class="sxs-lookup"><span data-stu-id="da60e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da60e-105">參數</span><span class="sxs-lookup"><span data-stu-id="da60e-105">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="da60e-106">在垃圾收集系統所使用的區段大小。</span><span class="sxs-lookup"><span data-stu-id="da60e-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="da60e-107">在層代0的大小上限。</span><span class="sxs-lookup"><span data-stu-id="da60e-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da60e-108">備註</span><span class="sxs-lookup"><span data-stu-id="da60e-108">Remarks</span></span>  

 <span data-ttu-id="da60e-109">`SetGCStartupLimitsEx`只有在啟動主機之前，才可以指定所設定的值。</span><span class="sxs-lookup"><span data-stu-id="da60e-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="da60e-110">這些值稍後無法變更。</span><span class="sxs-lookup"><span data-stu-id="da60e-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da60e-111">需求</span><span class="sxs-lookup"><span data-stu-id="da60e-111">Requirements</span></span>  

 <span data-ttu-id="da60e-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="da60e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da60e-113">**標頭：** GCHost .idl、GCHost。h</span><span class="sxs-lookup"><span data-stu-id="da60e-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="da60e-114">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="da60e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da60e-115">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da60e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da60e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da60e-116">See also</span></span>

- [<span data-ttu-id="da60e-117">IGCHost2 介面</span><span class="sxs-lookup"><span data-stu-id="da60e-117">IGCHost2 Interface</span></span>](igchost2-interface.md)
