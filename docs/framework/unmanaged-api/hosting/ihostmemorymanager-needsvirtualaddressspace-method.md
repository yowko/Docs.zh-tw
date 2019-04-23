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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0f029c8fbab97afe3089956391e8446d4cc5e15
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215491"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="4e1d3-102">IHostMemoryManager::NeedsVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="4e1d3-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="4e1d3-103">通知主機 common language runtime (CLR) 會嘗試使用指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="4e1d3-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e1d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e1d3-104">Syntax</span></span>  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e1d3-105">參數</span><span class="sxs-lookup"><span data-stu-id="4e1d3-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="4e1d3-106">[in]記憶體的起始位址。</span><span class="sxs-lookup"><span data-stu-id="4e1d3-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="4e1d3-107">[in]以位元組為單位的記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="4e1d3-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e1d3-108">備註</span><span class="sxs-lookup"><span data-stu-id="4e1d3-108">Remarks</span></span>  
 <span data-ttu-id="4e1d3-109">`NeedsVirtualAddressSpace`方法的回呼方法，必須在裝載應用程式寫入器實作。</span><span class="sxs-lookup"><span data-stu-id="4e1d3-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="4e1d3-110">CLR 會呼叫它。</span><span class="sxs-lookup"><span data-stu-id="4e1d3-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="4e1d3-111">如果主機不想要使用指定的記憶體 CLR，它可能會傳回 E_OUTOFMEMORY HRESULT。</span><span class="sxs-lookup"><span data-stu-id="4e1d3-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e1d3-112">需求</span><span class="sxs-lookup"><span data-stu-id="4e1d3-112">Requirements</span></span>  
 <span data-ttu-id="4e1d3-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e1d3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e1d3-114">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4e1d3-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4e1d3-115">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4e1d3-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e1d3-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e1d3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e1d3-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e1d3-117">See also</span></span>

- [<span data-ttu-id="4e1d3-118">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="4e1d3-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
