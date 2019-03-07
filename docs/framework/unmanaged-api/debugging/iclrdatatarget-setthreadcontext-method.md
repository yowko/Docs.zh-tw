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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4ab183bbe82c8e64b833c8fcdbc1e05ceb18e1f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482245"
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="37bfe-102">ICLRDataTarget::SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="37bfe-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="37bfe-103">目標處理序中設定指定之執行緒的目前內容。</span><span class="sxs-lookup"><span data-stu-id="37bfe-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="37bfe-104">這個方法是由通用語言執行平台 (CLR) 資料存取服務呼叫。</span><span class="sxs-lookup"><span data-stu-id="37bfe-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37bfe-105">語法</span><span class="sxs-lookup"><span data-stu-id="37bfe-105">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37bfe-106">參數</span><span class="sxs-lookup"><span data-stu-id="37bfe-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="37bfe-107">[in]目標處理序中的執行緒作業系統識別項。</span><span class="sxs-lookup"><span data-stu-id="37bfe-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="37bfe-108">[in]內容的大小。</span><span class="sxs-lookup"><span data-stu-id="37bfe-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="37bfe-109">[in]包含內容之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="37bfe-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="37bfe-110">中的資料`context`緩衝區會在 Win32 格式`CONTEXT`結構。</span><span class="sxs-lookup"><span data-stu-id="37bfe-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="37bfe-111">這個內容會指定特定處理器的暫存器資料，因此 Win32 定義`CONTEXT`結構取決於處理器架構。</span><span class="sxs-lookup"><span data-stu-id="37bfe-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="37bfe-112">請參閱 WinNT.h 標頭檔來定義的 Win32`CONTEXT`結構。</span><span class="sxs-lookup"><span data-stu-id="37bfe-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37bfe-113">備註</span><span class="sxs-lookup"><span data-stu-id="37bfe-113">Remarks</span></span>  
 <span data-ttu-id="37bfe-114">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="37bfe-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37bfe-115">需求</span><span class="sxs-lookup"><span data-stu-id="37bfe-115">Requirements</span></span>  
 <span data-ttu-id="37bfe-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="37bfe-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37bfe-117">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="37bfe-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="37bfe-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37bfe-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37bfe-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37bfe-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37bfe-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37bfe-120">See also</span></span>
- [<span data-ttu-id="37bfe-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="37bfe-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
