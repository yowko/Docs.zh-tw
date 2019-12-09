---
title: ICorDebugRegisterSet::SetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetThreadContext
helpviewer_keywords:
- ICorDebugRegisterSet::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 73afa930-32cb-4c40-81f8-83e8e6fbe213
topic_type:
- apiref
ms.openlocfilehash: 8731b57206f7987efc2498a5abe62295cd1cfae5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131331"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="1d754-102">ICorDebugRegisterSet::SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="1d754-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="1d754-103">`SetThreadContext` 不會在 .NET Framework 版本2.0 中執行。</span><span class="sxs-lookup"><span data-stu-id="1d754-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="1d754-104">請勿呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="1d754-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d754-105">使用較高層級的作業[ICorDebugNativeFrame：： SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)來設定執行緒的內容。</span><span class="sxs-lookup"><span data-stu-id="1d754-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d754-106">語法</span><span class="sxs-lookup"><span data-stu-id="1d754-106">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="1d754-107">需求</span><span class="sxs-lookup"><span data-stu-id="1d754-107">Requirements</span></span>  
 <span data-ttu-id="1d754-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d754-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d754-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d754-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d754-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d754-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d754-111">**.NET Framework 版本：** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="1d754-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d754-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="1d754-112">See also</span></span>

- [<span data-ttu-id="1d754-113">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="1d754-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="1d754-114">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="1d754-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
