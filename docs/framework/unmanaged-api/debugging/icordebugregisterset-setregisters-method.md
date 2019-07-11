---
title: ICorDebugRegisterSet::SetRegisters 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetRegisters
helpviewer_keywords:
- SetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::SetRegisters method [.NET Framework debugging]
ms.assetid: ac6244b9-54ba-475f-b72a-abed6afc46ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 472e92e4e7a69c437c66cc9f221ab357292c345e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769587"
---
# <a name="icordebugregistersetsetregisters-method"></a><span data-ttu-id="f903f-102">ICorDebugRegisterSet::SetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="f903f-102">ICorDebugRegisterSet::SetRegisters Method</span></span>
<span data-ttu-id="f903f-103">`SetRegisters` 未實作在.NET Framework 2.0 版。</span><span class="sxs-lookup"><span data-stu-id="f903f-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="f903f-104">請勿呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="f903f-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f903f-105">使用較高層級的作業，例如[icordebugilframe:: Setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)或是[icordebugnativeframe:: Setip](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)。</span><span class="sxs-lookup"><span data-stu-id="f903f-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f903f-106">語法</span><span class="sxs-lookup"><span data-stu-id="f903f-106">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f903f-107">需求</span><span class="sxs-lookup"><span data-stu-id="f903f-107">Requirements</span></span>  
 <span data-ttu-id="f903f-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f903f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f903f-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f903f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f903f-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f903f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f903f-111">**.NET framework 版本：** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="f903f-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f903f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f903f-112">See also</span></span>

- [<span data-ttu-id="f903f-113">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="f903f-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="f903f-114">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="f903f-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
