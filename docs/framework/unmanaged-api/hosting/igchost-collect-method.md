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
ms.openlocfilehash: ac73c462aa210927f0665cae161fd7f3e17a0cdb
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805302"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="20c6f-102">IGCHost::Collect 方法</span><span class="sxs-lookup"><span data-stu-id="20c6f-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="20c6f-103">無論目前垃圾收集的狀態為何，都會強制針對給定的層代進行集合。</span><span class="sxs-lookup"><span data-stu-id="20c6f-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20c6f-104">語法</span><span class="sxs-lookup"><span data-stu-id="20c6f-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20c6f-105">參數</span><span class="sxs-lookup"><span data-stu-id="20c6f-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="20c6f-106">在要在其上執行垃圾收集的產生。</span><span class="sxs-lookup"><span data-stu-id="20c6f-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="20c6f-107">-1 值表示所有層代都會進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="20c6f-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20c6f-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="20c6f-108">Requirements</span></span>  
 <span data-ttu-id="20c6f-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="20c6f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20c6f-110">**標頭：** GCHost .idl，GCHost。h</span><span class="sxs-lookup"><span data-stu-id="20c6f-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="20c6f-111">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="20c6f-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20c6f-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20c6f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20c6f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20c6f-113">See also</span></span>

- [<span data-ttu-id="20c6f-114">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="20c6f-114">IGCHost Interface</span></span>](igchost-interface.md)
