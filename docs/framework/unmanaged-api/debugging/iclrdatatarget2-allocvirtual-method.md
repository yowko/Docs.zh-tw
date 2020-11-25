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
ms.openlocfilehash: 6d3985919ea7e766db7d07e4ed81484851156ca5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723658"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="87f7b-102">ICLRDataTarget2::AllocVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="87f7b-102">ICLRDataTarget2::AllocVirtual Method</span></span>

<span data-ttu-id="87f7b-103">由 common language runtime 呼叫 (CLR) 資料存取服務，在這個目標進程的位址空間中配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="87f7b-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87f7b-104">語法</span><span class="sxs-lookup"><span data-stu-id="87f7b-104">Syntax</span></span>  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87f7b-105">參數</span><span class="sxs-lookup"><span data-stu-id="87f7b-105">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="87f7b-106">在 `CLRDATA_ADDRESS` 值，指定要配置之記憶體的要求開始位址。</span><span class="sxs-lookup"><span data-stu-id="87f7b-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="87f7b-107">在要配置的記憶體大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="87f7b-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="87f7b-108">在控制記憶體配置的旗標。</span><span class="sxs-lookup"><span data-stu-id="87f7b-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="87f7b-109">請參閱 Win32 `VirtualAlloc` 函數。</span><span class="sxs-lookup"><span data-stu-id="87f7b-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="87f7b-110">在配置的記憶體的保護屬性。</span><span class="sxs-lookup"><span data-stu-id="87f7b-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="87f7b-111">請參閱 Win32 `VirtualAlloc` 函數。</span><span class="sxs-lookup"><span data-stu-id="87f7b-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="87f7b-112">擴展 `CLRDATA_ADDRESS` 值的指標，指定配置記憶體的實際起始位址。</span><span class="sxs-lookup"><span data-stu-id="87f7b-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87f7b-113">備註</span><span class="sxs-lookup"><span data-stu-id="87f7b-113">Remarks</span></span>  

 <span data-ttu-id="87f7b-114">`AllocVirtual`方法可作為 Win32 函數的邏輯包裝函式 `VirtualAlloc` 。</span><span class="sxs-lookup"><span data-stu-id="87f7b-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="87f7b-115">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="87f7b-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87f7b-116">需求</span><span class="sxs-lookup"><span data-stu-id="87f7b-116">Requirements</span></span>  

 <span data-ttu-id="87f7b-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87f7b-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87f7b-118">**標頭：** ClrData .idl、ClrData。h</span><span class="sxs-lookup"><span data-stu-id="87f7b-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="87f7b-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87f7b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87f7b-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87f7b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f7b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87f7b-121">See also</span></span>

- [<span data-ttu-id="87f7b-122">ICLRDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="87f7b-122">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="87f7b-123">FreeVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="87f7b-123">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)
