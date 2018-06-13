---
title: ICorDebugMutableDataTarget::WriteVirtual 方法
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 184ae290b3a7d86a3c0351d4cfb072bce37337d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417410"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="60dbc-102">ICorDebugMutableDataTarget::WriteVirtual 方法</span><span class="sxs-lookup"><span data-stu-id="60dbc-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="60dbc-103">將記憶體寫入目標處理序位址空間。</span><span class="sxs-lookup"><span data-stu-id="60dbc-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60dbc-104">語法</span><span class="sxs-lookup"><span data-stu-id="60dbc-104">Syntax</span></span>  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60dbc-105">參數</span><span class="sxs-lookup"><span data-stu-id="60dbc-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="60dbc-106">[in] 要寫入 `pBuffer` 內容的位址。</span><span class="sxs-lookup"><span data-stu-id="60dbc-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="60dbc-107">[in] 包含所要寫入之位元組的位元組陣列指標。</span><span class="sxs-lookup"><span data-stu-id="60dbc-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="60dbc-108">[in] `pBuffer` 中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="60dbc-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60dbc-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="60dbc-109">Return Value</span></span>  
 <span data-ttu-id="60dbc-110">成功時為 `S_OK`，失敗時為任何其他 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="60dbc-110">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60dbc-111">備註</span><span class="sxs-lookup"><span data-stu-id="60dbc-111">Remarks</span></span>  
 <span data-ttu-id="60dbc-112">如果無法寫入任何位元組，則方法呼叫失敗，但不變更目標位址空間中的任何位元組。</span><span class="sxs-lookup"><span data-stu-id="60dbc-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="60dbc-113">(否則，目標的狀態會不一致，使進一步的偵錯變得不可靠。)</span><span class="sxs-lookup"><span data-stu-id="60dbc-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60dbc-114">需求</span><span class="sxs-lookup"><span data-stu-id="60dbc-114">Requirements</span></span>  
 <span data-ttu-id="60dbc-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="60dbc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60dbc-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60dbc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60dbc-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60dbc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60dbc-118">**.NET framework 版本：** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60dbc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60dbc-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60dbc-119">See Also</span></span>  
 [<span data-ttu-id="60dbc-120">ICorDebugMutableDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="60dbc-120">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="60dbc-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="60dbc-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
