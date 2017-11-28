---
title: "IHostMemoryManager::AcquiredVirtualAddressSpace 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.AcquiredVirtualAddressSpace
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 480dba9257c34af2cd1bc11aba4a07a4fbbe1162
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="62fcf-102">IHostMemoryManager::AcquiredVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="62fcf-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>
<span data-ttu-id="62fcf-103">通知主機 common language runtime (CLR) 已取得作業系統中指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="62fcf-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62fcf-104">語法</span><span class="sxs-lookup"><span data-stu-id="62fcf-104">Syntax</span></span>  
  
```  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62fcf-105">參數</span><span class="sxs-lookup"><span data-stu-id="62fcf-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="62fcf-106">[in]起始位址的記憶體。</span><span class="sxs-lookup"><span data-stu-id="62fcf-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="62fcf-107">[in]以位元組為單位的記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="62fcf-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62fcf-108">備註</span><span class="sxs-lookup"><span data-stu-id="62fcf-108">Remarks</span></span>  
 <span data-ttu-id="62fcf-109">`AcquiredVirtualAddressSpace`方法是一種回呼方法，而且必須實作寫入器會在裝載應用程式。</span><span class="sxs-lookup"><span data-stu-id="62fcf-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="62fcf-110">CLR 會呼叫它。</span><span class="sxs-lookup"><span data-stu-id="62fcf-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62fcf-111">需求</span><span class="sxs-lookup"><span data-stu-id="62fcf-111">Requirements</span></span>  
 <span data-ttu-id="62fcf-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62fcf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62fcf-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="62fcf-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62fcf-114">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="62fcf-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62fcf-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62fcf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62fcf-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62fcf-116">See Also</span></span>  
 [<span data-ttu-id="62fcf-117">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="62fcf-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
