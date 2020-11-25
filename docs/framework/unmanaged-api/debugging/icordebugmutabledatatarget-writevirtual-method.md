---
title: ICorDebugMutableDataTarget::WriteVirtual 方法
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 453ab23e292c5eab4a8300c32bf76743b787750d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709332"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="bd5d3-102">ICorDebugMutableDataTarget::WriteVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="bd5d3-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>

<span data-ttu-id="bd5d3-103">將記憶體寫入目標處理序位址空間。</span><span class="sxs-lookup"><span data-stu-id="bd5d3-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd5d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd5d3-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd5d3-105">參數</span><span class="sxs-lookup"><span data-stu-id="bd5d3-105">Parameters</span></span>  

 `address`  
 <span data-ttu-id="bd5d3-106">[in] 要寫入 `pBuffer` 內容的位址。</span><span class="sxs-lookup"><span data-stu-id="bd5d3-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="bd5d3-107">[in] 包含所要寫入之位元組的位元組陣列指標。</span><span class="sxs-lookup"><span data-stu-id="bd5d3-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="bd5d3-108">[in] `pBuffer` 中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="bd5d3-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd5d3-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="bd5d3-109">Return Value</span></span>  

 <span data-ttu-id="bd5d3-110">成功時為 `S_OK`，失敗時為任何其他 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="bd5d3-110">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd5d3-111">備註</span><span class="sxs-lookup"><span data-stu-id="bd5d3-111">Remarks</span></span>  

 <span data-ttu-id="bd5d3-112">如果無法寫入任何位元組，則方法呼叫失敗，但不變更目標位址空間中的任何位元組。</span><span class="sxs-lookup"><span data-stu-id="bd5d3-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="bd5d3-113">(否則，目標的狀態會不一致，使進一步的偵錯變得不可靠。)</span><span class="sxs-lookup"><span data-stu-id="bd5d3-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd5d3-114">需求</span><span class="sxs-lookup"><span data-stu-id="bd5d3-114">Requirements</span></span>  

 <span data-ttu-id="bd5d3-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd5d3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd5d3-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd5d3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd5d3-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd5d3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd5d3-118">**.NET Framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd5d3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd5d3-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd5d3-119">See also</span></span>

- [<span data-ttu-id="bd5d3-120">ICorDebugMutableDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="bd5d3-120">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="bd5d3-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="bd5d3-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
