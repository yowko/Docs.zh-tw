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
ms.openlocfilehash: 7b1ea34c187de99d23b05b5e1a30c53bc54a6c0c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197395"
---
# <a name="icordebugregistersetsetthreadcontext-method"></a><span data-ttu-id="51603-102">ICorDebugRegisterSet::SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="51603-102">ICorDebugRegisterSet::SetThreadContext Method</span></span>
<span data-ttu-id="51603-103">`SetThreadContext` 未實作在.NET Framework 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="51603-103">`SetThreadContext` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="51603-104">請勿呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="51603-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51603-105">使用較高層級的作業[icordebugnativeframe:: Setip](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)來設定執行緒的內容。</span><span class="sxs-lookup"><span data-stu-id="51603-105">Use the higher-level operation [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) to set the context of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51603-106">語法</span><span class="sxs-lookup"><span data-stu-id="51603-106">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize),  
         size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="51603-107">需求</span><span class="sxs-lookup"><span data-stu-id="51603-107">Requirements</span></span>  
 <span data-ttu-id="51603-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51603-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51603-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51603-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51603-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51603-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51603-111">**.NET framework 版本：** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="51603-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51603-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51603-112">See also</span></span>

- [<span data-ttu-id="51603-113">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="51603-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="51603-114">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="51603-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
