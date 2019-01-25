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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b7bf2a3e359ca05a147553d89a1d2bb3d235209
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571045"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="0d1cf-102">IHostMemoryManager::ReleasedVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="0d1cf-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="0d1cf-103">通知主機 common language runtime (CLR) 已完成使用指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="0d1cf-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d1cf-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d1cf-104">Syntax</span></span>  
  
```  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d1cf-105">參數</span><span class="sxs-lookup"><span data-stu-id="0d1cf-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="0d1cf-106">[in]要釋放的記憶體的起始位址指標。</span><span class="sxs-lookup"><span data-stu-id="0d1cf-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d1cf-107">備註</span><span class="sxs-lookup"><span data-stu-id="0d1cf-107">Remarks</span></span>  
 <span data-ttu-id="0d1cf-108">`ReleasedVirtualAddressSpace`方法的回呼方法，必須在裝載應用程式寫入器實作。</span><span class="sxs-lookup"><span data-stu-id="0d1cf-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="0d1cf-109">CLR 會呼叫它。</span><span class="sxs-lookup"><span data-stu-id="0d1cf-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d1cf-110">需求</span><span class="sxs-lookup"><span data-stu-id="0d1cf-110">Requirements</span></span>  
 <span data-ttu-id="0d1cf-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d1cf-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d1cf-112">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0d1cf-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d1cf-113">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0d1cf-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d1cf-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d1cf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d1cf-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d1cf-115">See also</span></span>
- [<span data-ttu-id="0d1cf-116">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="0d1cf-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
