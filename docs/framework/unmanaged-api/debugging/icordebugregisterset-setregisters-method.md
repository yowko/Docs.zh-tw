---
title: "ICorDebugRegisterSet::SetRegisters 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8ddf1eab6ea4689e330137fba1a676fd86ed2187
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregistersetsetregisters-method"></a><span data-ttu-id="7d0ad-102">ICorDebugRegisterSet::SetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="7d0ad-102">ICorDebugRegisterSet::SetRegisters Method</span></span>
<span data-ttu-id="7d0ad-103">`SetRegisters`未實作.NET Framework 2.0 版中。</span><span class="sxs-lookup"><span data-stu-id="7d0ad-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="7d0ad-104">請勿呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="7d0ad-104">Do not call this method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d0ad-105">使用較高層級的作業，例如[icordebugilframe:: Setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)或[icordebugnativeframe:: Setip](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)。</span><span class="sxs-lookup"><span data-stu-id="7d0ad-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d0ad-106">語法</span><span class="sxs-lookup"><span data-stu-id="7d0ad-106">Syntax</span></span>  
  
```  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="7d0ad-107">需求</span><span class="sxs-lookup"><span data-stu-id="7d0ad-107">Requirements</span></span>  
 <span data-ttu-id="7d0ad-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7d0ad-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d0ad-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7d0ad-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7d0ad-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7d0ad-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d0ad-111">**.NET framework 版本：** 1.1、 1.0</span><span class="sxs-lookup"><span data-stu-id="7d0ad-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d0ad-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="7d0ad-112">See Also</span></span>  
 [<span data-ttu-id="7d0ad-113">ICorDebugRegisterSet 介面</span><span class="sxs-lookup"><span data-stu-id="7d0ad-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="7d0ad-114">ICorDebugRegisterSet2 介面</span><span class="sxs-lookup"><span data-stu-id="7d0ad-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
