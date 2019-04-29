---
title: ICorDebugRegisterSet::GetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fecbcff0fd124b94aeeecf82e23d9875c34ebb9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782892"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="57060-102">ICorDebugRegisterSet::GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="57060-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="57060-103">取得目前執行緒的內容。</span><span class="sxs-lookup"><span data-stu-id="57060-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57060-104">語法</span><span class="sxs-lookup"><span data-stu-id="57060-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57060-105">參數</span><span class="sxs-lookup"><span data-stu-id="57060-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="57060-106">[in]大小，以位元組為單位的`context`陣列。</span><span class="sxs-lookup"><span data-stu-id="57060-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="57060-107">[in、 out]撰寫 Win32 的位元組陣列`CONTEXT`結構目前的平台。</span><span class="sxs-lookup"><span data-stu-id="57060-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57060-108">備註</span><span class="sxs-lookup"><span data-stu-id="57060-108">Remarks</span></span>  
 <span data-ttu-id="57060-109">偵錯工具應該呼叫此函式，而不是 Win32`GetThreadContext`函式，因為執行緒可能處於 「 攔截 」 狀態，其中已暫時變更其內容。</span><span class="sxs-lookup"><span data-stu-id="57060-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="57060-110">傳回的資料是 Win32`CONTEXT`結構目前的平台。</span><span class="sxs-lookup"><span data-stu-id="57060-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="57060-111">非分葉框架，用戶端應該檢查哪些暫存器是使用有效[icordebugregisterset:: Getregistersavailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)。</span><span class="sxs-lookup"><span data-stu-id="57060-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57060-112">需求</span><span class="sxs-lookup"><span data-stu-id="57060-112">Requirements</span></span>  
 <span data-ttu-id="57060-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="57060-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57060-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57060-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57060-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57060-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57060-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57060-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57060-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57060-117">See also</span></span>

- [<span data-ttu-id="57060-118">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="57060-118">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="57060-119">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="57060-119">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
