---
title: IGCHost::SetVirtualMemLimit 方法
ms.date: 03/30/2017
api_name:
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
ms.openlocfilehash: 9898b760edbb149afcd6bf957a30d0a47287485b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687804"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="c665b-102">IGCHost::SetVirtualMemLimit 方法</span><span class="sxs-lookup"><span data-stu-id="c665b-102">IGCHost::SetVirtualMemLimit Method</span></span>

<span data-ttu-id="c665b-103">設定執行時間的虛擬記憶體大小上限。</span><span class="sxs-lookup"><span data-stu-id="c665b-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c665b-104">語法</span><span class="sxs-lookup"><span data-stu-id="c665b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c665b-105">參數</span><span class="sxs-lookup"><span data-stu-id="c665b-105">Parameters</span></span>  

 `sztMaxVirtualMemMB`  
 <span data-ttu-id="c665b-106">在執行時間之虛擬記憶體的大小上限（以 mb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="c665b-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c665b-107">備註</span><span class="sxs-lookup"><span data-stu-id="c665b-107">Remarks</span></span>  

 <span data-ttu-id="c665b-108">執行時間的虛擬記憶體大小上限可動態變更。</span><span class="sxs-lookup"><span data-stu-id="c665b-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c665b-109">需求</span><span class="sxs-lookup"><span data-stu-id="c665b-109">Requirements</span></span>  

 <span data-ttu-id="c665b-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c665b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c665b-111">**標頭：** GCHost .idl、GCHost。h</span><span class="sxs-lookup"><span data-stu-id="c665b-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="c665b-112">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="c665b-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c665b-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c665b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c665b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c665b-114">See also</span></span>

- [<span data-ttu-id="c665b-115">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="c665b-115">IGCHost Interface</span></span>](igchost-interface.md)
