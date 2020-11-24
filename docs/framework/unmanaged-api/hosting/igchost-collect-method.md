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
ms.openlocfilehash: f32b91f0d47449f80c38542162035999d616813b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670133"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="f49b1-102">IGCHost::Collect 方法</span><span class="sxs-lookup"><span data-stu-id="f49b1-102">IGCHost::Collect Method</span></span>

<span data-ttu-id="f49b1-103">無論目前垃圾收集的狀態為何，都會強制執行給定層代的集合。</span><span class="sxs-lookup"><span data-stu-id="f49b1-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f49b1-104">語法</span><span class="sxs-lookup"><span data-stu-id="f49b1-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f49b1-105">參數</span><span class="sxs-lookup"><span data-stu-id="f49b1-105">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="f49b1-106">在要執行垃圾收集的層代。</span><span class="sxs-lookup"><span data-stu-id="f49b1-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="f49b1-107">-1 的值表示所有層代都會進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="f49b1-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f49b1-108">需求</span><span class="sxs-lookup"><span data-stu-id="f49b1-108">Requirements</span></span>  

 <span data-ttu-id="f49b1-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f49b1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f49b1-110">**標頭：** GCHost .idl、GCHost。h</span><span class="sxs-lookup"><span data-stu-id="f49b1-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="f49b1-111">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f49b1-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f49b1-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f49b1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f49b1-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f49b1-113">See also</span></span>

- [<span data-ttu-id="f49b1-114">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="f49b1-114">IGCHost Interface</span></span>](igchost-interface.md)
