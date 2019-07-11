---
title: ICLRDataTarget::GetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1492c6d72d68a95a79925d7789a710b5b5ed14b1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738701"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="03061-102">ICLRDataTarget::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="03061-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="03061-103">取得目標處理序中指定的執行緒目前的執行內容。</span><span class="sxs-lookup"><span data-stu-id="03061-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="03061-104">這個方法是由通用語言執行階段資料存取服務呼叫。</span><span class="sxs-lookup"><span data-stu-id="03061-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03061-105">語法</span><span class="sxs-lookup"><span data-stu-id="03061-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03061-106">參數</span><span class="sxs-lookup"><span data-stu-id="03061-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="03061-107">[in]目標處理序中的執行緒作業系統識別項。</span><span class="sxs-lookup"><span data-stu-id="03061-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="03061-108">[in]旗標，指定要傳回的內容中哪些部分。</span><span class="sxs-lookup"><span data-stu-id="03061-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="03061-109">實作會傳回至少這些組件的內容。</span><span class="sxs-lookup"><span data-stu-id="03061-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="03061-110">[in]內容的大小。</span><span class="sxs-lookup"><span data-stu-id="03061-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="03061-111">[out]在其中放置內容緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="03061-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="03061-112">中的資料`context`Win32 的格式必須是緩衝區`CONTEXT`結構。</span><span class="sxs-lookup"><span data-stu-id="03061-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="03061-113">這個內容會指定特定處理器的暫存器資料，因此 Win32 定義`CONTEXT`結構取決於處理器架構。</span><span class="sxs-lookup"><span data-stu-id="03061-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="03061-114">請參閱 WinNT.h 標頭檔來定義的 Win32`CONTEXT`結構。</span><span class="sxs-lookup"><span data-stu-id="03061-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03061-115">備註</span><span class="sxs-lookup"><span data-stu-id="03061-115">Remarks</span></span>  
 <span data-ttu-id="03061-116">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="03061-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03061-117">需求</span><span class="sxs-lookup"><span data-stu-id="03061-117">Requirements</span></span>  
 <span data-ttu-id="03061-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03061-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03061-119">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="03061-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="03061-120">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="03061-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03061-121">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03061-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03061-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03061-122">See also</span></span>

- [<span data-ttu-id="03061-123">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="03061-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
