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
ms.openlocfilehash: 4be5d2d9d891010e68cd6eb96cd4456e04d8c8b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712283"
---
# <a name="icordebugregistersetsetregisters-method"></a><span data-ttu-id="a6f6d-102">ICorDebugRegisterSet::SetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="a6f6d-102">ICorDebugRegisterSet::SetRegisters Method</span></span>

<span data-ttu-id="a6f6d-103">`SetRegisters` 不是在 .NET Framework 版本2.0 中執行。</span><span class="sxs-lookup"><span data-stu-id="a6f6d-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="a6f6d-104">請不要呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="a6f6d-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6f6d-105">使用較高層級的作業，例如 [ICorDebugILFrame：： setip](icordebugilframe-setip-method.md) 或 [ICorDebugNativeFrame：： setip](icordebugnativeframe-setip-method.md)。</span><span class="sxs-lookup"><span data-stu-id="a6f6d-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6f6d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a6f6d-106">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a6f6d-107">需求</span><span class="sxs-lookup"><span data-stu-id="a6f6d-107">Requirements</span></span>  

 <span data-ttu-id="a6f6d-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a6f6d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6f6d-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6f6d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6f6d-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6f6d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6f6d-111">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="a6f6d-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6f6d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6f6d-112">See also</span></span>

- [<span data-ttu-id="a6f6d-113">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="a6f6d-113">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="a6f6d-114">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="a6f6d-114">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
