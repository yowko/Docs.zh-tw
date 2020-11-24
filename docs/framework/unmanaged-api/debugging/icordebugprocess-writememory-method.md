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
ms.openlocfilehash: 18416954517c3cac09d013b8075bd097305a1dca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673952"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="8ce98-102">ICorDebugProcess::WriteMemory 方法</span><span class="sxs-lookup"><span data-stu-id="8ce98-102">ICorDebugProcess::WriteMemory Method</span></span>

<span data-ttu-id="8ce98-103">將資料寫入此進程中的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="8ce98-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ce98-104">語法</span><span class="sxs-lookup"><span data-stu-id="8ce98-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ce98-105">參數</span><span class="sxs-lookup"><span data-stu-id="8ce98-105">Parameters</span></span>  

 `address`  
 <span data-ttu-id="8ce98-106">在 `CORDB_ADDRESS` 值，這個值是寫入資料的記憶體區域基底位址。</span><span class="sxs-lookup"><span data-stu-id="8ce98-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="8ce98-107">在進行資料傳輸之前，系統會先確認指定大小的記憶體區域（從基底位址開始）可以進行寫入。</span><span class="sxs-lookup"><span data-stu-id="8ce98-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="8ce98-108">如果無法存取，方法將會失敗。</span><span class="sxs-lookup"><span data-stu-id="8ce98-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="8ce98-109">在要寫入記憶體區域的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="8ce98-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="8ce98-110">在包含要寫入之資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8ce98-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="8ce98-111">擴展變數的指標，此變數會接收此進程中寫入記憶體區域的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="8ce98-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="8ce98-112">如果 `written` 是 Null，則會忽略這個參數。</span><span class="sxs-lookup"><span data-stu-id="8ce98-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ce98-113">備註</span><span class="sxs-lookup"><span data-stu-id="8ce98-113">Remarks</span></span>  

 <span data-ttu-id="8ce98-114">資料會自動寫入任何中斷點後方。</span><span class="sxs-lookup"><span data-stu-id="8ce98-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="8ce98-115">在 .NET Framework 2.0 版中，原生偵錯工具不應該使用這個方法將中斷點插入指令資料流程中。</span><span class="sxs-lookup"><span data-stu-id="8ce98-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="8ce98-116">請改用 [ICorDebugProcess2：： SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="8ce98-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="8ce98-117">`WriteMemory`方法只能在 managed 程式碼之外使用。</span><span class="sxs-lookup"><span data-stu-id="8ce98-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="8ce98-118">如果使用不正確，此方法可能會損毀執行時間。</span><span class="sxs-lookup"><span data-stu-id="8ce98-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ce98-119">需求</span><span class="sxs-lookup"><span data-stu-id="8ce98-119">Requirements</span></span>  

 <span data-ttu-id="8ce98-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8ce98-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ce98-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ce98-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ce98-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ce98-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ce98-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ce98-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
