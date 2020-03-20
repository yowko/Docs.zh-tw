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
ms.openlocfilehash: 383e3f8990a1f355c94ff5e9f9daa69bdbdd97bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178656"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="13271-102">ICorDebugProcess::ReadMemory 方法</span><span class="sxs-lookup"><span data-stu-id="13271-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="13271-103">讀取此過程的指定記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="13271-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13271-104">語法</span><span class="sxs-lookup"><span data-stu-id="13271-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13271-105">參數</span><span class="sxs-lookup"><span data-stu-id="13271-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="13271-106">[在]指定`CORDB_ADDRESS`要讀取的記憶體的基本位址的值。</span><span class="sxs-lookup"><span data-stu-id="13271-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="13271-107">[在]要從記憶體中讀取的位元組數。</span><span class="sxs-lookup"><span data-stu-id="13271-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="13271-108">[出]接收記憶體內容的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="13271-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="13271-109">[出]指向傳輸到指定緩衝區的位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="13271-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13271-110">備註</span><span class="sxs-lookup"><span data-stu-id="13271-110">Remarks</span></span>  
 <span data-ttu-id="13271-111">該方法`ReadMemory`主要用於內部調試，以檢查調試器的非託管部分正在使用的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="13271-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="13271-112">此方法還可用於讀取 Microsoft 中間語言 （MSIL） 代碼和本機 JIT 編譯代碼。</span><span class="sxs-lookup"><span data-stu-id="13271-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="13271-113">任何託管中斷點都將從`buffer`參數中返回的資料中刪除。</span><span class="sxs-lookup"><span data-stu-id="13271-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="13271-114">[ICorDebugProcess2：：：setUn託管中斷點](icordebugprocess2-setunmanagedbreakpoint-method.md)設置的本機中斷點不會進行調整。</span><span class="sxs-lookup"><span data-stu-id="13271-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="13271-115">不執行進程記憶體的緩存。</span><span class="sxs-lookup"><span data-stu-id="13271-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13271-116">需求</span><span class="sxs-lookup"><span data-stu-id="13271-116">Requirements</span></span>  
 <span data-ttu-id="13271-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="13271-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13271-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13271-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13271-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13271-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13271-120">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13271-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
