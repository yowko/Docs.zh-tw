---
title: ICorDebugMutableDataTarget：： WriteVirtual 方法
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 5947caa8dfb97574bb4b3c5634d962df153211c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132684"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="3acf2-102">ICorDebugMutableDataTarget：： WriteVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="3acf2-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="3acf2-103">將記憶體寫入目標處理序位址空間。</span><span class="sxs-lookup"><span data-stu-id="3acf2-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3acf2-104">語法</span><span class="sxs-lookup"><span data-stu-id="3acf2-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3acf2-105">參數</span><span class="sxs-lookup"><span data-stu-id="3acf2-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="3acf2-106">[in] 要寫入 `pBuffer` 內容的位址。</span><span class="sxs-lookup"><span data-stu-id="3acf2-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="3acf2-107">[in] 包含所要寫入之位元組的位元組陣列指標。</span><span class="sxs-lookup"><span data-stu-id="3acf2-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="3acf2-108">[in] `pBuffer` 中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="3acf2-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3acf2-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="3acf2-109">Return Value</span></span>  
 <span data-ttu-id="3acf2-110">成功時為 `S_OK`，失敗時為任何其他 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="3acf2-110">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3acf2-111">備註</span><span class="sxs-lookup"><span data-stu-id="3acf2-111">Remarks</span></span>  
 <span data-ttu-id="3acf2-112">如果無法寫入任何位元組，則方法呼叫失敗，但不變更目標位址空間中的任何位元組。</span><span class="sxs-lookup"><span data-stu-id="3acf2-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="3acf2-113">(否則，目標的狀態會不一致，使進一步的偵錯變得不可靠。)</span><span class="sxs-lookup"><span data-stu-id="3acf2-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3acf2-114">需求</span><span class="sxs-lookup"><span data-stu-id="3acf2-114">Requirements</span></span>  
 <span data-ttu-id="3acf2-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3acf2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3acf2-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3acf2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3acf2-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3acf2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3acf2-118">**.NET framework 版本：** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3acf2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3acf2-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="3acf2-119">See also</span></span>

- [<span data-ttu-id="3acf2-120">ICorDebugMutableDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="3acf2-120">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="3acf2-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3acf2-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
