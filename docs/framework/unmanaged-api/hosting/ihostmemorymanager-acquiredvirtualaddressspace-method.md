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
ms.openlocfilehash: f5469a6f35826bcb06fe821e3748861dbf3682f3
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804536"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="11c3f-102">IHostMemoryManager::AcquiredVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="11c3f-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>
<span data-ttu-id="11c3f-103">通知主機 common language runtime （CLR）已從作業系統取得指定的記憶體。</span><span class="sxs-lookup"><span data-stu-id="11c3f-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11c3f-104">語法</span><span class="sxs-lookup"><span data-stu-id="11c3f-104">Syntax</span></span>  
  
```cpp  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11c3f-105">參數</span><span class="sxs-lookup"><span data-stu-id="11c3f-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="11c3f-106">在記憶體的起始位址。</span><span class="sxs-lookup"><span data-stu-id="11c3f-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="11c3f-107">在記憶體的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="11c3f-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11c3f-108">備註</span><span class="sxs-lookup"><span data-stu-id="11c3f-108">Remarks</span></span>  
 <span data-ttu-id="11c3f-109">`AcquiredVirtualAddressSpace`方法是回呼方法，必須由主控應用程式的寫入器來執行。</span><span class="sxs-lookup"><span data-stu-id="11c3f-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="11c3f-110">CLR 會呼叫它。</span><span class="sxs-lookup"><span data-stu-id="11c3f-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11c3f-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="11c3f-111">Requirements</span></span>  
 <span data-ttu-id="11c3f-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11c3f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11c3f-113">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="11c3f-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="11c3f-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="11c3f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11c3f-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11c3f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c3f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11c3f-116">See also</span></span>

- [<span data-ttu-id="11c3f-117">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="11c3f-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
