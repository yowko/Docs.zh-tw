---
title: IHostMemoryManager::AcquiredVirtualAddressSpace 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.AcquiredVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 423fbfc2bda9d3544a5c32b6cd650643209f0e86
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767238"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="163c7-102">IHostMemoryManager::AcquiredVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="163c7-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>
<span data-ttu-id="163c7-103">Common language runtime (CLR) 已取得指定的記憶體，作業系統會告知主應用程式。</span><span class="sxs-lookup"><span data-stu-id="163c7-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="163c7-104">語法</span><span class="sxs-lookup"><span data-stu-id="163c7-104">Syntax</span></span>  
  
```cpp  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="163c7-105">參數</span><span class="sxs-lookup"><span data-stu-id="163c7-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="163c7-106">[in]記憶體的起始位址。</span><span class="sxs-lookup"><span data-stu-id="163c7-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="163c7-107">[in]以位元組為單位的記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="163c7-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="163c7-108">備註</span><span class="sxs-lookup"><span data-stu-id="163c7-108">Remarks</span></span>  
 <span data-ttu-id="163c7-109">`AcquiredVirtualAddressSpace`方法的回呼方法，必須在裝載應用程式寫入器實作。</span><span class="sxs-lookup"><span data-stu-id="163c7-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="163c7-110">CLR 會呼叫它。</span><span class="sxs-lookup"><span data-stu-id="163c7-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="163c7-111">需求</span><span class="sxs-lookup"><span data-stu-id="163c7-111">Requirements</span></span>  
 <span data-ttu-id="163c7-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="163c7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="163c7-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="163c7-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="163c7-114">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="163c7-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="163c7-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="163c7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="163c7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="163c7-116">See also</span></span>

- [<span data-ttu-id="163c7-117">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="163c7-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
