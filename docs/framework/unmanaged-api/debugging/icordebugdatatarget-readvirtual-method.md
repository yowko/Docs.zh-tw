---
title: ICorDebugDataTarget::ReadVirtual 方法
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.ReadVirtual Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::ReadVirtual
helpviewer_keywords:
- ICorDebugDataTarget::ReadVirtual method [.NET Framework debugging]
- ReadVirtual method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: 55e57640-b3d2-413d-b4f4-fbc27fb8e37c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9d42c85502c12d4d77694626a533c69af97da67
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750257"
---
# <a name="icordebugdatatargetreadvirtual-method"></a><span data-ttu-id="ebe05-102">ICorDebugDataTarget::ReadVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="ebe05-102">ICorDebugDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="ebe05-103">取得從指定的位址、 開始的連續記憶體區塊，並傳回它在提供的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ebe05-103">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebe05-104">語法</span><span class="sxs-lookup"><span data-stu-id="ebe05-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual(  
    [in] CORDB_ADDRESS   address,  
    [out, size_is(bytesRequested), length_is(*pBytesRead)]  
          BYTE *     pBuffer,  
    [in]  ULONG32    bytesRequested,  
    [out] ULONG32 *  pBytesRead);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebe05-105">參數</span><span class="sxs-lookup"><span data-stu-id="ebe05-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="ebe05-106">[in]起始要求的記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="ebe05-106">[in] The start address of requested memory.</span></span>  
  
 `pbuffer`  
 <span data-ttu-id="ebe05-107">[out]將儲存記憶體緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ebe05-107">[out] The buffer where the memory will be stored.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="ebe05-108">[in]若要從目標位址取得的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="ebe05-108">[in] The number of bytes to get from the target address.</span></span>  
  
 `pBytesRead`  
 <span data-ttu-id="ebe05-109">[out]從目標位址實際讀取的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="ebe05-109">[out] The number of bytes actually read from the target address.</span></span> <span data-ttu-id="ebe05-110">這可以是少於`bytesRequested`。</span><span class="sxs-lookup"><span data-stu-id="ebe05-110">This can be fewer than `bytesRequested`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebe05-111">備註</span><span class="sxs-lookup"><span data-stu-id="ebe05-111">Remarks</span></span>  
 <span data-ttu-id="ebe05-112">如果可以讀取的第一個位元組 （在指定的開始位址），呼叫應該會傳回成功 （以支援有效讀取具有自我描述的長度，例如 null 結尾字串的資料結構）。</span><span class="sxs-lookup"><span data-stu-id="ebe05-112">If the first byte (at the specified start address) can be read, the call should return success (to support efficient reading of data structures with self-describing length, like null-terminated strings).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebe05-113">需求</span><span class="sxs-lookup"><span data-stu-id="ebe05-113">Requirements</span></span>  
 <span data-ttu-id="ebe05-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ebe05-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebe05-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ebe05-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebe05-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebe05-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebe05-117">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebe05-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebe05-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebe05-118">See also</span></span>

- [<span data-ttu-id="ebe05-119">ICorDebugDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="ebe05-119">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="ebe05-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ebe05-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ebe05-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="ebe05-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
