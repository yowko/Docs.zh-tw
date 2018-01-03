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
ms.workload: dotnet
ms.openlocfilehash: 9251cbadaf182cda8d52f3f5792452310561c376
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="d90c9-102">IHostMemoryManager::NeedsVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="d90c9-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="d90c9-103">通知主機 common language runtime (CLR) 會嘗試使用指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="d90c9-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d90c9-104">語法</span><span class="sxs-lookup"><span data-stu-id="d90c9-104">Syntax</span></span>  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d90c9-105">參數</span><span class="sxs-lookup"><span data-stu-id="d90c9-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="d90c9-106">[in]起始位址的記憶體。</span><span class="sxs-lookup"><span data-stu-id="d90c9-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="d90c9-107">[in]以位元組為單位的記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="d90c9-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d90c9-108">備註</span><span class="sxs-lookup"><span data-stu-id="d90c9-108">Remarks</span></span>  
 <span data-ttu-id="d90c9-109">`NeedsVirtualAddressSpace`方法是一種回呼方法，而且必須實作寫入器會在裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="d90c9-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="d90c9-110">CLR 會呼叫它。</span><span class="sxs-lookup"><span data-stu-id="d90c9-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="d90c9-111">如果主機不想要使用指定的記憶體 CLR，可能會傳回 E_OUTOFMEMORY HRESULT。</span><span class="sxs-lookup"><span data-stu-id="d90c9-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d90c9-112">需求</span><span class="sxs-lookup"><span data-stu-id="d90c9-112">Requirements</span></span>  
 <span data-ttu-id="d90c9-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d90c9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d90c9-114">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d90c9-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d90c9-115">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d90c9-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d90c9-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d90c9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d90c9-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="d90c9-117">See Also</span></span>  
 [<span data-ttu-id="d90c9-118">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="d90c9-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
