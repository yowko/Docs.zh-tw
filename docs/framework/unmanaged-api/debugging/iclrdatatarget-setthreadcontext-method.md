---
title: ICLRDataTarget::SetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type:
- apiref
ms.openlocfilehash: d76a907434b12b85aaedeef169390ec6f0df724a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179120"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="f175a-102">ICLRDataTarget::SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="f175a-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="f175a-103">設置目標進程中指定執行緒的當前上下文。</span><span class="sxs-lookup"><span data-stu-id="f175a-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="f175a-104">此方法由通用語言運行時 （CLR） 資料訪問服務調用。</span><span class="sxs-lookup"><span data-stu-id="f175a-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f175a-105">語法</span><span class="sxs-lookup"><span data-stu-id="f175a-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f175a-106">參數</span><span class="sxs-lookup"><span data-stu-id="f175a-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="f175a-107">[在]目標進程中線程的作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="f175a-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="f175a-108">[在]上下文的大小。</span><span class="sxs-lookup"><span data-stu-id="f175a-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="f175a-109">[在]指向包含上下文的緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="f175a-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="f175a-110">緩衝區中`context`的資料將以 Win32`CONTEXT`結構的格式表示。</span><span class="sxs-lookup"><span data-stu-id="f175a-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="f175a-111">上下文指定特定于處理器的寄存器資料，因此 Win32`CONTEXT`結構的定義取決於處理器的體系結構。</span><span class="sxs-lookup"><span data-stu-id="f175a-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="f175a-112">有關 Win32`CONTEXT`結構的定義，請參閱 WinNT.h 標標頭檔。</span><span class="sxs-lookup"><span data-stu-id="f175a-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f175a-113">備註</span><span class="sxs-lookup"><span data-stu-id="f175a-113">Remarks</span></span>  
 <span data-ttu-id="f175a-114">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="f175a-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f175a-115">需求</span><span class="sxs-lookup"><span data-stu-id="f175a-115">Requirements</span></span>  
 <span data-ttu-id="f175a-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f175a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f175a-117">**標題：** ClrData.idl， ClrData.h</span><span class="sxs-lookup"><span data-stu-id="f175a-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f175a-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f175a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f175a-119">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f175a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f175a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f175a-120">See also</span></span>

- [<span data-ttu-id="f175a-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="f175a-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
