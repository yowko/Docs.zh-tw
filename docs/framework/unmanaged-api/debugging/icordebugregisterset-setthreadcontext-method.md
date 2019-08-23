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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff1365ddb46ca28cbcaa4f1383b293681e6ec214
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956777"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="c16be-102">ICorDebugRegisterSet::SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="c16be-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="c16be-103">`SetThreadContext`不會在 .NET Framework 版本2.0 中執行。</span><span class="sxs-lookup"><span data-stu-id="c16be-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="c16be-104">請勿呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="c16be-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c16be-105">使用較高層級的作業[ICorDebugNativeFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)來設定執行緒的內容。</span><span class="sxs-lookup"><span data-stu-id="c16be-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c16be-106">語法</span><span class="sxs-lookup"><span data-stu-id="c16be-106">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c16be-107">需求</span><span class="sxs-lookup"><span data-stu-id="c16be-107">Requirements</span></span>  
 <span data-ttu-id="c16be-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c16be-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c16be-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c16be-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c16be-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c16be-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c16be-111">**.NET Framework 版本:** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="c16be-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c16be-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c16be-112">See also</span></span>

- [<span data-ttu-id="c16be-113">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="c16be-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="c16be-114">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="c16be-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
