---
title: ICLRDataTarget2::FreeVirtual 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8d2f6a716c65596c781015bad0dea52705611a0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487150"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="5342e-102">ICLRDataTarget2::FreeVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="5342e-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="5342e-103">由通用語言執行平台 (CLR) 資料存取服務先前配置的目標處理序的位址空間中的可用記憶體來呼叫。</span><span class="sxs-lookup"><span data-stu-id="5342e-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5342e-104">語法</span><span class="sxs-lookup"><span data-stu-id="5342e-104">Syntax</span></span>  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5342e-105">參數</span><span class="sxs-lookup"><span data-stu-id="5342e-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="5342e-106">[in]A`CLRDATA_ADDRESS`值，指定要釋放記憶體的起始位址。</span><span class="sxs-lookup"><span data-stu-id="5342e-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="5342e-107">[in]以位元組為單位，以釋放記憶體的大小。</span><span class="sxs-lookup"><span data-stu-id="5342e-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="5342e-108">[in]控制釋放記憶體的旗標。</span><span class="sxs-lookup"><span data-stu-id="5342e-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="5342e-109">請參閱 Win32`VirtualFree`函式。</span><span class="sxs-lookup"><span data-stu-id="5342e-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5342e-110">備註</span><span class="sxs-lookup"><span data-stu-id="5342e-110">Remarks</span></span>  
 <span data-ttu-id="5342e-111">`FreeVirtual`方法做為 Win32 的邏輯包裝函數`VirtualFree`函式。</span><span class="sxs-lookup"><span data-stu-id="5342e-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="5342e-112">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="5342e-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5342e-113">需求</span><span class="sxs-lookup"><span data-stu-id="5342e-113">Requirements</span></span>  
 <span data-ttu-id="5342e-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5342e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5342e-115">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="5342e-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5342e-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5342e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5342e-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5342e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5342e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5342e-118">See also</span></span>
- [<span data-ttu-id="5342e-119">ICLRDataTarget2 介面</span><span class="sxs-lookup"><span data-stu-id="5342e-119">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="5342e-120">AllocVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="5342e-120">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
