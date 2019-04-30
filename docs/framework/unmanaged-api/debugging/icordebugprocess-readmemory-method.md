---
title: ICorDebugProcess::ReadMemory 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 218279684304b766a9bf009f5891ac4910254a3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994379"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="5a4f3-102">ICorDebugProcess::ReadMemory 方法</span><span class="sxs-lookup"><span data-stu-id="5a4f3-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="5a4f3-103">讀取指定的此程序的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="5a4f3-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a4f3-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a4f3-104">Syntax</span></span>  
  
```  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a4f3-105">參數</span><span class="sxs-lookup"><span data-stu-id="5a4f3-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="5a4f3-106">[in]A`CORDB_ADDRESS`值，指定要讀取的記憶體的基底位址。</span><span class="sxs-lookup"><span data-stu-id="5a4f3-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="5a4f3-107">[in]若要從記憶體讀取的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="5a4f3-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="5a4f3-108">[out]接收內容的記憶體緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5a4f3-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="5a4f3-109">[out]指標的位元組數傳送至指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="5a4f3-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a4f3-110">備註</span><span class="sxs-lookup"><span data-stu-id="5a4f3-110">Remarks</span></span>  
 <span data-ttu-id="5a4f3-111">`ReadMemory`方法主要是用來檢查正在使用的 unmanaged 偵錯項目一部分的記憶體區域的 interop 偵錯。</span><span class="sxs-lookup"><span data-stu-id="5a4f3-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="5a4f3-112">這個方法也可用來讀取 Microsoft intermediate language (MSIL) 程式碼和原生的 JIT 編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="5a4f3-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="5a4f3-113">將移除任何受管理的中斷點，從資料中傳回的`buffer`參數。</span><span class="sxs-lookup"><span data-stu-id="5a4f3-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="5a4f3-114">將進行不會調整，藉由設定原生的中斷點[ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)。</span><span class="sxs-lookup"><span data-stu-id="5a4f3-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="5a4f3-115">無快取的程序記憶體會執行。</span><span class="sxs-lookup"><span data-stu-id="5a4f3-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a4f3-116">需求</span><span class="sxs-lookup"><span data-stu-id="5a4f3-116">Requirements</span></span>  
 <span data-ttu-id="5a4f3-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a4f3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a4f3-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a4f3-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a4f3-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a4f3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a4f3-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a4f3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
