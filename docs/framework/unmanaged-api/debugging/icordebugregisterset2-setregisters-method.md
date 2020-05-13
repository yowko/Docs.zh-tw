---
title: ICorDebugRegisterSet2::SetRegisters 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::SetRegisters
helpviewer_keywords:
- ICorDebugRegisterSet2::SetRegisters method [.NET Framework debugging]
- SetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: fe0ac7e7-c9e1-4ec1-9f4e-1c56d63d73ac
topic_type:
- apiref
ms.openlocfilehash: ebbd8dc2b715541850ed3b3bc530c0dd28993e1d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378120"
---
# <a name="icordebugregisterset2setregisters-method"></a><span data-ttu-id="87203-102">ICorDebugRegisterSet2::SetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="87203-102">ICorDebugRegisterSet2::SetRegisters Method</span></span>
<span data-ttu-id="87203-103">`SetRegisters`不會在 .NET Framework 版本2.0 中執行。</span><span class="sxs-lookup"><span data-stu-id="87203-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="87203-104">請不要呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="87203-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87203-105">使用較高層級的作業，例如[ICorDebugILFrame：： SetIP](icordebugilframe-setip-method.md)或[ICorDebugNativeFrame：： setip](icordebugnativeframe-setip-method.md)。</span><span class="sxs-lookup"><span data-stu-id="87203-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87203-106">語法</span><span class="sxs-lookup"><span data-stu-id="87203-106">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="87203-107">需求</span><span class="sxs-lookup"><span data-stu-id="87203-107">Requirements</span></span>  
 <span data-ttu-id="87203-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87203-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87203-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="87203-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87203-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87203-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87203-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87203-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87203-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="87203-112">See also</span></span>

- [<span data-ttu-id="87203-113">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="87203-113">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="87203-114">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="87203-114">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
