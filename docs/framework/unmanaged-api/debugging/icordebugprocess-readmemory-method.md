---
title: "ICorDebugProcess::ReadMemory 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.ReadMemory
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33345ada6606bc1a43a630340251d3ba1404b2f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="af705-102">ICorDebugProcess::ReadMemory 方法</span><span class="sxs-lookup"><span data-stu-id="af705-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="af705-103">讀取指定的這個處理序的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="af705-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af705-104">語法</span><span class="sxs-lookup"><span data-stu-id="af705-104">Syntax</span></span>  
  
```  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,   
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af705-105">參數</span><span class="sxs-lookup"><span data-stu-id="af705-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="af705-106">[in]A`CORDB_ADDRESS`值，指定讀取記憶體的基底位址。</span><span class="sxs-lookup"><span data-stu-id="af705-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="af705-107">[in]要從記憶體讀取的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="af705-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="af705-108">[out]接收內容的記憶體緩衝區。</span><span class="sxs-lookup"><span data-stu-id="af705-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="af705-109">[out]位元組數目的指標傳送至指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="af705-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af705-110">備註</span><span class="sxs-lookup"><span data-stu-id="af705-110">Remarks</span></span>  
 <span data-ttu-id="af705-111">`ReadMemory`方法主要是要用來檢查正在使用的 unmanaged 偵錯項目一部分的記憶體區域的 interop 偵錯。</span><span class="sxs-lookup"><span data-stu-id="af705-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="af705-112">這個方法也可用來讀取 Microsoft intermediate language (MSIL) 程式碼和原生的 JIT 編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="af705-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="af705-113">任何受管理的中斷點會移除資料中傳回`buffer`參數。</span><span class="sxs-lookup"><span data-stu-id="af705-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="af705-114">沒有進行調整將成為所設定的原生中斷點[icordebugprocess2:: Setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)。</span><span class="sxs-lookup"><span data-stu-id="af705-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="af705-115">執行任何快取的處理序記憶體。</span><span class="sxs-lookup"><span data-stu-id="af705-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af705-116">需求</span><span class="sxs-lookup"><span data-stu-id="af705-116">Requirements</span></span>  
 <span data-ttu-id="af705-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="af705-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af705-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af705-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af705-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af705-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af705-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af705-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
