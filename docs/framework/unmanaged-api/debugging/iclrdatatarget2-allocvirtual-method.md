---
title: ICLRDataTarget2::AllocVirtual 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
ms.openlocfilehash: 7640f7fafd0bf52a302ac0da1e5df39b5da22d68
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091151"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="8a4fb-102">ICLRDataTarget2::AllocVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="8a4fb-102">ICLRDataTarget2::AllocVirtual Method</span></span>
<span data-ttu-id="8a4fb-103">由 common language runtime （CLR）資料存取服務呼叫，以在此目標進程的位址空間中配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="8a4fb-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a4fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="8a4fb-104">Syntax</span></span>  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a4fb-105">參數</span><span class="sxs-lookup"><span data-stu-id="8a4fb-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="8a4fb-106">在`CLRDATA_ADDRESS` 值，指定要配置之記憶體的要求起始位址。</span><span class="sxs-lookup"><span data-stu-id="8a4fb-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="8a4fb-107">在要配置的記憶體大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="8a4fb-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="8a4fb-108">在控制記憶體配置的旗標。</span><span class="sxs-lookup"><span data-stu-id="8a4fb-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="8a4fb-109">請參閱 Win32 `VirtualAlloc` 函數。</span><span class="sxs-lookup"><span data-stu-id="8a4fb-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="8a4fb-110">在已配置記憶體的保護屬性。</span><span class="sxs-lookup"><span data-stu-id="8a4fb-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="8a4fb-111">請參閱 Win32 `VirtualAlloc` 函數。</span><span class="sxs-lookup"><span data-stu-id="8a4fb-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="8a4fb-112">脫銷`CLRDATA_ADDRESS` 值的指標，指定配置之記憶體的實際起始位址。</span><span class="sxs-lookup"><span data-stu-id="8a4fb-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a4fb-113">備註</span><span class="sxs-lookup"><span data-stu-id="8a4fb-113">Remarks</span></span>  
 <span data-ttu-id="8a4fb-114">`AllocVirtual` 方法可做為 Win32 `VirtualAlloc` 函數的邏輯包裝函式。</span><span class="sxs-lookup"><span data-stu-id="8a4fb-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="8a4fb-115">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="8a4fb-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a4fb-116">需求</span><span class="sxs-lookup"><span data-stu-id="8a4fb-116">Requirements</span></span>  
 <span data-ttu-id="8a4fb-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a4fb-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a4fb-118">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="8a4fb-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8a4fb-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a4fb-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a4fb-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a4fb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a4fb-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="8a4fb-121">See also</span></span>

- [<span data-ttu-id="8a4fb-122">ICLRDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="8a4fb-122">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="8a4fb-123">FreeVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="8a4fb-123">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
