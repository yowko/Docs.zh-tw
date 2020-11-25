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
ms.openlocfilehash: 74fbb2f162fbb68871f1bb4e1a1de32f5f913cd7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731315"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="3868f-102">IHostMemoryManager::NeedsVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="3868f-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>

<span data-ttu-id="3868f-103">通知主機 common language runtime (CLR) 即將嘗試使用指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="3868f-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3868f-104">語法</span><span class="sxs-lookup"><span data-stu-id="3868f-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3868f-105">參數</span><span class="sxs-lookup"><span data-stu-id="3868f-105">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="3868f-106">在記憶體的起始位址。</span><span class="sxs-lookup"><span data-stu-id="3868f-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="3868f-107">在記憶體的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="3868f-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3868f-108">備註</span><span class="sxs-lookup"><span data-stu-id="3868f-108">Remarks</span></span>  

 <span data-ttu-id="3868f-109">`NeedsVirtualAddressSpace`方法是回呼方法，必須由主控應用程式的寫入器來執行。</span><span class="sxs-lookup"><span data-stu-id="3868f-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="3868f-110">它是由 CLR 呼叫。</span><span class="sxs-lookup"><span data-stu-id="3868f-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="3868f-111">如果主機不希望 CLR 使用指定的記憶體，它可能會傳回 E_OUTOFMEMORY HRESULT。</span><span class="sxs-lookup"><span data-stu-id="3868f-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3868f-112">需求</span><span class="sxs-lookup"><span data-stu-id="3868f-112">Requirements</span></span>  

 <span data-ttu-id="3868f-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3868f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3868f-114">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3868f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3868f-115">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="3868f-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3868f-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3868f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3868f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3868f-117">See also</span></span>

- [<span data-ttu-id="3868f-118">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="3868f-118">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
