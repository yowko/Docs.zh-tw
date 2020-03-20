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
ms.openlocfilehash: 3777ad4b12c7d0593c095c470aba81088137a859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179173"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="07cd3-102">ICLRDataTarget::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="07cd3-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="07cd3-103">獲取目標進程中給定執行緒的當前執行上下文。</span><span class="sxs-lookup"><span data-stu-id="07cd3-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="07cd3-104">此方法由通用語言運行時資料訪問服務調用。</span><span class="sxs-lookup"><span data-stu-id="07cd3-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07cd3-105">語法</span><span class="sxs-lookup"><span data-stu-id="07cd3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07cd3-106">參數</span><span class="sxs-lookup"><span data-stu-id="07cd3-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="07cd3-107">[在]目標進程中線程的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="07cd3-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="07cd3-108">[在]指定要返回上下文的哪些部分的標誌。</span><span class="sxs-lookup"><span data-stu-id="07cd3-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="07cd3-109">實現將至少返回上下文的這些部分。</span><span class="sxs-lookup"><span data-stu-id="07cd3-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="07cd3-110">[在]上下文的大小。</span><span class="sxs-lookup"><span data-stu-id="07cd3-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="07cd3-111">[出]指向要在其中放置上下文的緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="07cd3-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="07cd3-112">緩衝區中`context`的資料必須採用 Win32`CONTEXT`結構的格式。</span><span class="sxs-lookup"><span data-stu-id="07cd3-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="07cd3-113">上下文指定特定于處理器的寄存器資料，因此 Win32`CONTEXT`結構的定義取決於處理器的體系結構。</span><span class="sxs-lookup"><span data-stu-id="07cd3-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="07cd3-114">有關 Win32`CONTEXT`結構的定義，請參閱 WinNT.h 標標頭檔。</span><span class="sxs-lookup"><span data-stu-id="07cd3-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07cd3-115">備註</span><span class="sxs-lookup"><span data-stu-id="07cd3-115">Remarks</span></span>  
 <span data-ttu-id="07cd3-116">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="07cd3-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07cd3-117">需求</span><span class="sxs-lookup"><span data-stu-id="07cd3-117">Requirements</span></span>  
 <span data-ttu-id="07cd3-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07cd3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07cd3-119">**標題：** ClrData.idl， ClrData.h</span><span class="sxs-lookup"><span data-stu-id="07cd3-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="07cd3-120">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07cd3-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07cd3-121">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07cd3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07cd3-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07cd3-122">See also</span></span>

- [<span data-ttu-id="07cd3-123">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="07cd3-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
