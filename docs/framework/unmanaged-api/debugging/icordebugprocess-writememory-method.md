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
ms.openlocfilehash: fb3e0ccb57cf3b056bd25e643706e49b8bc75531
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792546"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="0b26f-102">ICorDebugProcess::WriteMemory 方法</span><span class="sxs-lookup"><span data-stu-id="0b26f-102">ICorDebugProcess::WriteMemory Method</span></span>
<span data-ttu-id="0b26f-103">將資料寫入此進程中的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="0b26f-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b26f-104">語法</span><span class="sxs-lookup"><span data-stu-id="0b26f-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b26f-105">參數</span><span class="sxs-lookup"><span data-stu-id="0b26f-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="0b26f-106">在`CORDB_ADDRESS` 值，這是寫入資料之記憶體區域的基底位址。</span><span class="sxs-lookup"><span data-stu-id="0b26f-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="0b26f-107">在資料傳輸之前，系統會確認可存取指定大小的記憶體區域（從基底位址開始），以便進行寫入。</span><span class="sxs-lookup"><span data-stu-id="0b26f-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="0b26f-108">如果無法存取，方法就會失敗。</span><span class="sxs-lookup"><span data-stu-id="0b26f-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="0b26f-109">在要寫入記憶體區域的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="0b26f-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="0b26f-110">在包含要寫入之資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0b26f-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="0b26f-111">脫銷變數的指標，這個變數會接收寫入此進程中記憶體區域的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="0b26f-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="0b26f-112">如果 `written` 為 Null，則會忽略這個參數。</span><span class="sxs-lookup"><span data-stu-id="0b26f-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b26f-113">備註</span><span class="sxs-lookup"><span data-stu-id="0b26f-113">Remarks</span></span>  
 <span data-ttu-id="0b26f-114">資料會在任何中斷點之後自動寫入。</span><span class="sxs-lookup"><span data-stu-id="0b26f-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="0b26f-115">在 .NET Framework 版本2.0 中，原生偵錯工具不應該使用這個方法將中斷點插入指令資料流程中。</span><span class="sxs-lookup"><span data-stu-id="0b26f-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="0b26f-116">請改用[ICorDebugProcess2：： SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="0b26f-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="0b26f-117">`WriteMemory` 方法只能在 managed 程式碼外部使用。</span><span class="sxs-lookup"><span data-stu-id="0b26f-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="0b26f-118">如果未正確使用，這個方法可能會損毀執行時間。</span><span class="sxs-lookup"><span data-stu-id="0b26f-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b26f-119">需求</span><span class="sxs-lookup"><span data-stu-id="0b26f-119">Requirements</span></span>  
 <span data-ttu-id="0b26f-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0b26f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b26f-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b26f-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b26f-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b26f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b26f-123">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b26f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
