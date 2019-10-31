---
title: IHostMemoryManager::NeedsVirtualAddressSpace 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
ms.openlocfilehash: a3ae474a73f4c8e4b98c4b2bc5d04e55bcae6874
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128659"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="5b3c2-102">IHostMemoryManager::NeedsVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="5b3c2-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="5b3c2-103">通知主機 common language runtime （CLR）即將嘗試使用指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="5b3c2-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b3c2-104">語法</span><span class="sxs-lookup"><span data-stu-id="5b3c2-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b3c2-105">參數</span><span class="sxs-lookup"><span data-stu-id="5b3c2-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="5b3c2-106">在記憶體的起始位址。</span><span class="sxs-lookup"><span data-stu-id="5b3c2-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="5b3c2-107">在記憶體的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="5b3c2-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b3c2-108">備註</span><span class="sxs-lookup"><span data-stu-id="5b3c2-108">Remarks</span></span>  
 <span data-ttu-id="5b3c2-109">`NeedsVirtualAddressSpace` 方法是回呼方法，必須由主控應用程式的寫入器來執行。</span><span class="sxs-lookup"><span data-stu-id="5b3c2-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="5b3c2-110">CLR 會呼叫它。</span><span class="sxs-lookup"><span data-stu-id="5b3c2-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="5b3c2-111">如果主機不想讓 CLR 使用指定的記憶體，它可能會傳回 E_OUTOFMEMORY HRESULT。</span><span class="sxs-lookup"><span data-stu-id="5b3c2-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b3c2-112">需求</span><span class="sxs-lookup"><span data-stu-id="5b3c2-112">Requirements</span></span>  
 <span data-ttu-id="5b3c2-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5b3c2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b3c2-114">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="5b3c2-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b3c2-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5b3c2-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b3c2-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b3c2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b3c2-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="5b3c2-117">See also</span></span>

- [<span data-ttu-id="5b3c2-118">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="5b3c2-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
