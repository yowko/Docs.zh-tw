---
title: "IHostMemoryManager::NeedsVirtualAddressSpace 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.NeedsVirtualAddressSpace
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62ceb9e5b4d5843b8e2adad344b3ffb662ab3aff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="182fc-102">IHostMemoryManager::NeedsVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="182fc-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="182fc-103">通知主機 common language runtime (CLR) 會嘗試使用指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="182fc-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="182fc-104">語法</span><span class="sxs-lookup"><span data-stu-id="182fc-104">Syntax</span></span>  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="182fc-105">參數</span><span class="sxs-lookup"><span data-stu-id="182fc-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="182fc-106">[in]起始位址的記憶體。</span><span class="sxs-lookup"><span data-stu-id="182fc-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="182fc-107">[in]以位元組為單位的記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="182fc-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="182fc-108">備註</span><span class="sxs-lookup"><span data-stu-id="182fc-108">Remarks</span></span>  
 <span data-ttu-id="182fc-109">`NeedsVirtualAddressSpace`方法是一種回呼方法，而且必須實作寫入器會在裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="182fc-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="182fc-110">CLR 會呼叫它。</span><span class="sxs-lookup"><span data-stu-id="182fc-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="182fc-111">如果主機不想要使用指定的記憶體 CLR，可能會傳回 E_OUTOFMEMORY HRESULT。</span><span class="sxs-lookup"><span data-stu-id="182fc-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="182fc-112">需求</span><span class="sxs-lookup"><span data-stu-id="182fc-112">Requirements</span></span>  
 <span data-ttu-id="182fc-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="182fc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="182fc-114">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="182fc-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="182fc-115">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="182fc-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="182fc-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="182fc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="182fc-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="182fc-117">See Also</span></span>  
 [<span data-ttu-id="182fc-118">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="182fc-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
