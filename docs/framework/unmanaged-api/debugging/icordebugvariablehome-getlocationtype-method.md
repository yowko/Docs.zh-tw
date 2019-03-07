---
title: ICorDebugVariableHome::GetLocationType 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba0387b84f8d32831b79dd6c361bcdbb78f8bbba
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499478"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="493bc-102">ICorDebugVariableHome::GetLocationType 方法</span><span class="sxs-lookup"><span data-stu-id="493bc-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="493bc-103">取得變數的原生位置類型。</span><span class="sxs-lookup"><span data-stu-id="493bc-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="493bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="493bc-104">Syntax</span></span>  
  
```  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="493bc-105">參數</span><span class="sxs-lookup"><span data-stu-id="493bc-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="493bc-106">[out]變數的原生位置的類型指標。</span><span class="sxs-lookup"><span data-stu-id="493bc-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="493bc-107">請參閱[VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)列舉型別，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="493bc-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="493bc-108">需求</span><span class="sxs-lookup"><span data-stu-id="493bc-108">Requirements</span></span>  
 <span data-ttu-id="493bc-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="493bc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="493bc-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="493bc-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="493bc-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="493bc-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="493bc-112">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="493bc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="493bc-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="493bc-113">See also</span></span>
- [<span data-ttu-id="493bc-114">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="493bc-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="493bc-115">VariableLocationType 列舉</span><span class="sxs-lookup"><span data-stu-id="493bc-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
