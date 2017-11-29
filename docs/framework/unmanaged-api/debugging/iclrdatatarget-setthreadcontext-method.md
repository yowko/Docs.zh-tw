---
title: "ICLRDataTarget::SetThreadContext 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.SetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e51cbafda76933d58bd60be8db7dd163a2dd59d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="19278-102">ICLRDataTarget::SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="19278-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="19278-103">目標處理序中，設定指定之執行緒的目前內容。</span><span class="sxs-lookup"><span data-stu-id="19278-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="19278-104">這個方法是由通用語言執行平台 (CLR) 資料存取服務呼叫。</span><span class="sxs-lookup"><span data-stu-id="19278-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19278-105">語法</span><span class="sxs-lookup"><span data-stu-id="19278-105">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19278-106">參數</span><span class="sxs-lookup"><span data-stu-id="19278-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="19278-107">[in]目標處理序中執行緒的作業系統識別項。</span><span class="sxs-lookup"><span data-stu-id="19278-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="19278-108">[in]內容的大小。</span><span class="sxs-lookup"><span data-stu-id="19278-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="19278-109">[in]包含內容之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="19278-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="19278-110">中的資料`context`緩衝區將 Win32 格式`CONTEXT`結構。</span><span class="sxs-lookup"><span data-stu-id="19278-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="19278-111">內容指定處理器特定暫存器的資料，因此 Win32 定義`CONTEXT`結構取決於處理器架構。</span><span class="sxs-lookup"><span data-stu-id="19278-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="19278-112">請參閱 WinNT.h 標頭檔定義的 Win32`CONTEXT`結構。</span><span class="sxs-lookup"><span data-stu-id="19278-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19278-113">備註</span><span class="sxs-lookup"><span data-stu-id="19278-113">Remarks</span></span>  
 <span data-ttu-id="19278-114">此方法是由偵錯應用程式的作者來實作。</span><span class="sxs-lookup"><span data-stu-id="19278-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19278-115">需求</span><span class="sxs-lookup"><span data-stu-id="19278-115">Requirements</span></span>  
 <span data-ttu-id="19278-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19278-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19278-117">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="19278-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="19278-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19278-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19278-119">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19278-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19278-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19278-120">See Also</span></span>  
 [<span data-ttu-id="19278-121">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="19278-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
