---
title: IHostMemoryManager::ReleasedVirtualAddressSpace 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.ReleasedVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type:
- apiref
ms.openlocfilehash: 46082ddcee0163d5e61b3e468eb32c71e9f242ce
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128621"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="b9676-102">IHostMemoryManager::ReleasedVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="b9676-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="b9676-103">通知主機 common language runtime （CLR）已使用指定的記憶體完成。</span><span class="sxs-lookup"><span data-stu-id="b9676-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9676-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9676-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9676-105">參數</span><span class="sxs-lookup"><span data-stu-id="b9676-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="b9676-106">在要釋放之記憶體的起始位址指標。</span><span class="sxs-lookup"><span data-stu-id="b9676-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9676-107">備註</span><span class="sxs-lookup"><span data-stu-id="b9676-107">Remarks</span></span>  
 <span data-ttu-id="b9676-108">`ReleasedVirtualAddressSpace` 方法是回呼方法，必須由主控應用程式的寫入器來執行。</span><span class="sxs-lookup"><span data-stu-id="b9676-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="b9676-109">CLR 會呼叫它。</span><span class="sxs-lookup"><span data-stu-id="b9676-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9676-110">需求</span><span class="sxs-lookup"><span data-stu-id="b9676-110">Requirements</span></span>  
 <span data-ttu-id="b9676-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9676-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9676-112">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b9676-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b9676-113">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b9676-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9676-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9676-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9676-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9676-115">See also</span></span>

- [<span data-ttu-id="b9676-116">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="b9676-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
