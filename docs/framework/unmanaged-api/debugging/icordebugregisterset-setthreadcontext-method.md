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
ms.openlocfilehash: 66e8cf3f73e92f58765b1fa98b3eef11b976094c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712270"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="cb3e2-102">ICorDebugRegisterSet::SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="cb3e2-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>

<span data-ttu-id="cb3e2-103">`SetThreadContext` 不是在 .NET Framework 版本2.0 中執行。</span><span class="sxs-lookup"><span data-stu-id="cb3e2-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="cb3e2-104">請不要呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="cb3e2-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb3e2-105">使用較高層級的 operation [ICorDebugNativeFrame：： SetIP](icordebugnativeframe-setip-method.md) 來設定執行緒的內容。</span><span class="sxs-lookup"><span data-stu-id="cb3e2-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb3e2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="cb3e2-106">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="cb3e2-107">需求</span><span class="sxs-lookup"><span data-stu-id="cb3e2-107">Requirements</span></span>  

 <span data-ttu-id="cb3e2-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb3e2-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb3e2-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb3e2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb3e2-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb3e2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb3e2-111">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="cb3e2-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb3e2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb3e2-112">See also</span></span>

- [<span data-ttu-id="cb3e2-113">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="cb3e2-113">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="cb3e2-114">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="cb3e2-114">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
