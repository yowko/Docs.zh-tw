---
title: IGCHost::Collect 方法
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
ms.openlocfilehash: e20ea6addc1ae3f99b4b3d65f532e0128ac160b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134964"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="3cd98-102">IGCHost::Collect 方法</span><span class="sxs-lookup"><span data-stu-id="3cd98-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="3cd98-103">無論目前垃圾收集的狀態為何，都會強制針對給定的層代進行集合。</span><span class="sxs-lookup"><span data-stu-id="3cd98-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cd98-104">語法</span><span class="sxs-lookup"><span data-stu-id="3cd98-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cd98-105">參數</span><span class="sxs-lookup"><span data-stu-id="3cd98-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="3cd98-106">在要在其上執行垃圾收集的產生。</span><span class="sxs-lookup"><span data-stu-id="3cd98-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="3cd98-107">-1 值表示所有層代都會進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="3cd98-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cd98-108">需求</span><span class="sxs-lookup"><span data-stu-id="3cd98-108">Requirements</span></span>  
 <span data-ttu-id="3cd98-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3cd98-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cd98-110">**標頭：** GCHost .idl，GCHost。h</span><span class="sxs-lookup"><span data-stu-id="3cd98-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="3cd98-111">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3cd98-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3cd98-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cd98-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cd98-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="3cd98-113">See also</span></span>

- [<span data-ttu-id="3cd98-114">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="3cd98-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
