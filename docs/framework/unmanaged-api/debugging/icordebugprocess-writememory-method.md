---
title: ICorDebugProcess::WriteMemory 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4599bf310a0b819bc662b90a5a86e87ac27c37b1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737014"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="2730c-102">ICorDebugProcess::WriteMemory 方法</span><span class="sxs-lookup"><span data-stu-id="2730c-102">ICorDebugProcess::WriteMemory Method</span></span>
<span data-ttu-id="2730c-103">將資料寫入至這個處理程序中的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="2730c-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2730c-104">語法</span><span class="sxs-lookup"><span data-stu-id="2730c-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2730c-105">參數</span><span class="sxs-lookup"><span data-stu-id="2730c-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="2730c-106">[in]A`CORDB_ADDRESS`寫入資料的記憶體區域的基底位址的值。</span><span class="sxs-lookup"><span data-stu-id="2730c-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="2730c-107">傳送資料之前，系統會驗證指定的大小，在基底的位址，從開始的記憶體區域是可供寫入存取。</span><span class="sxs-lookup"><span data-stu-id="2730c-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="2730c-108">如果您不能存取，方法就會失敗。</span><span class="sxs-lookup"><span data-stu-id="2730c-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="2730c-109">[in]要寫入的記憶體區域的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="2730c-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="2730c-110">[in]這種緩衝區包含要寫入的資料。</span><span class="sxs-lookup"><span data-stu-id="2730c-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="2730c-111">[out]在此程序的記憶體區域寫入的位元組數目接收變數的指標。</span><span class="sxs-lookup"><span data-stu-id="2730c-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="2730c-112">如果`written`為 NULL，就會忽略這個參數。</span><span class="sxs-lookup"><span data-stu-id="2730c-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2730c-113">備註</span><span class="sxs-lookup"><span data-stu-id="2730c-113">Remarks</span></span>  
 <span data-ttu-id="2730c-114">任何中斷點之後，會自動寫入資料。</span><span class="sxs-lookup"><span data-stu-id="2730c-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="2730c-115">在.NET Framework 2.0 版中，原生偵錯工具應該使用這個方法來插入指令資料流中的中斷點。</span><span class="sxs-lookup"><span data-stu-id="2730c-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="2730c-116">使用[ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)改。</span><span class="sxs-lookup"><span data-stu-id="2730c-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="2730c-117">`WriteMemory`方法應該只在 managed 程式碼之外使用。</span><span class="sxs-lookup"><span data-stu-id="2730c-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="2730c-118">如果不當使用，這個方法可能會損毀的執行階段。</span><span class="sxs-lookup"><span data-stu-id="2730c-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2730c-119">需求</span><span class="sxs-lookup"><span data-stu-id="2730c-119">Requirements</span></span>  
 <span data-ttu-id="2730c-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2730c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2730c-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2730c-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2730c-122">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2730c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2730c-123">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2730c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
