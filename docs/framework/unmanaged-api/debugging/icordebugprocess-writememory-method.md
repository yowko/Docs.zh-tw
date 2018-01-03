---
title: "ICorDebugProcess::WriteMemory 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.WriteMemory
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a1a12d1393d1db69ea47833958fdf828b552064
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="9c747-102">ICorDebugProcess::WriteMemory 方法</span><span class="sxs-lookup"><span data-stu-id="9c747-102">ICorDebugProcess::WriteMemory Method</span></span>
<span data-ttu-id="9c747-103">將資料寫入此程序的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="9c747-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c747-104">語法</span><span class="sxs-lookup"><span data-stu-id="9c747-104">Syntax</span></span>  
  
```  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c747-105">參數</span><span class="sxs-lookup"><span data-stu-id="9c747-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="9c747-106">[in]A`CORDB_ADDRESS`寫入值，也就是基底資料的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="9c747-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="9c747-107">資料傳輸發生之前，系統會確認指定的大小，開始的基底位址的記憶體區域是可供寫入存取。</span><span class="sxs-lookup"><span data-stu-id="9c747-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="9c747-108">如果您不能存取，方法就會失敗。</span><span class="sxs-lookup"><span data-stu-id="9c747-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="9c747-109">[in]寫入記憶體區域的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="9c747-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="9c747-110">[in]包含要寫入資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9c747-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="9c747-111">[out]寫入記憶體區域，此程序中的位元組數目變數的指標。</span><span class="sxs-lookup"><span data-stu-id="9c747-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="9c747-112">如果`written`是 NULL，這個參數已忽略。</span><span class="sxs-lookup"><span data-stu-id="9c747-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c747-113">備註</span><span class="sxs-lookup"><span data-stu-id="9c747-113">Remarks</span></span>  
 <span data-ttu-id="9c747-114">任何中斷點之後，會自動寫入資料。</span><span class="sxs-lookup"><span data-stu-id="9c747-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="9c747-115">在.NET Framework 2.0 版中，原生偵錯工具不應使用這個方法將中斷點插入指令資料流。</span><span class="sxs-lookup"><span data-stu-id="9c747-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="9c747-116">使用[icordebugprocess2:: Setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)改為。</span><span class="sxs-lookup"><span data-stu-id="9c747-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="9c747-117">`WriteMemory`方法應只有外部 managed 程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="9c747-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="9c747-118">如果不當使用，這個方法可能會損毀的執行階段。</span><span class="sxs-lookup"><span data-stu-id="9c747-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c747-119">需求</span><span class="sxs-lookup"><span data-stu-id="9c747-119">Requirements</span></span>  
 <span data-ttu-id="9c747-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9c747-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c747-121">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c747-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c747-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c747-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c747-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c747-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
