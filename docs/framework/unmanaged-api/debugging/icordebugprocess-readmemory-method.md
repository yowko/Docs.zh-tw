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
ms.openlocfilehash: ef9e339c74b2d2785d758ed9c4adfc1901073253
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139368"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="43133-102">ICorDebugProcess::ReadMemory 方法</span><span class="sxs-lookup"><span data-stu-id="43133-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="43133-103">讀取這個進程的指定記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="43133-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43133-104">語法</span><span class="sxs-lookup"><span data-stu-id="43133-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43133-105">參數</span><span class="sxs-lookup"><span data-stu-id="43133-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="43133-106">在`CORDB_ADDRESS` 值，指定要讀取之記憶體的基底位址。</span><span class="sxs-lookup"><span data-stu-id="43133-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="43133-107">在要從記憶體中讀取的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="43133-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="43133-108">脫銷接收記憶體內容的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="43133-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="43133-109">脫銷傳送到指定緩衝區的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="43133-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43133-110">備註</span><span class="sxs-lookup"><span data-stu-id="43133-110">Remarks</span></span>  
 <span data-ttu-id="43133-111">`ReadMemory` 方法主要是供 interop 偵錯工具用來檢查偵錯工具的非受控部分所使用的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="43133-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="43133-112">這個方法也可以用來讀取 Microsoft 中繼語言（MSIL）程式碼和原生 JIT 編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="43133-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="43133-113">任何受控中斷點都會從 `buffer` 參數傳回的資料中移除。</span><span class="sxs-lookup"><span data-stu-id="43133-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="43133-114">[ICorDebugProcess2：： SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)所設定的原生中斷點不會進行任何調整。</span><span class="sxs-lookup"><span data-stu-id="43133-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="43133-115">不會執行進程記憶體的快取。</span><span class="sxs-lookup"><span data-stu-id="43133-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43133-116">需求</span><span class="sxs-lookup"><span data-stu-id="43133-116">Requirements</span></span>  
 <span data-ttu-id="43133-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="43133-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43133-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43133-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43133-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43133-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43133-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43133-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
