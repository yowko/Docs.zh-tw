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
ms.openlocfilehash: af879cbbf8edfd05e79d9b77b0c1fb71b2c835c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993651"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="0dec9-102">ICorDebugVariableHome::GetLocationType 方法</span><span class="sxs-lookup"><span data-stu-id="0dec9-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="0dec9-103">取得變數的原生位置類型。</span><span class="sxs-lookup"><span data-stu-id="0dec9-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dec9-104">語法</span><span class="sxs-lookup"><span data-stu-id="0dec9-104">Syntax</span></span>  
  
```  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dec9-105">參數</span><span class="sxs-lookup"><span data-stu-id="0dec9-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="0dec9-106">[out]變數的原生位置的類型指標。</span><span class="sxs-lookup"><span data-stu-id="0dec9-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="0dec9-107">請參閱[VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)列舉型別，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0dec9-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dec9-108">需求</span><span class="sxs-lookup"><span data-stu-id="0dec9-108">Requirements</span></span>  
 <span data-ttu-id="0dec9-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0dec9-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dec9-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0dec9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0dec9-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0dec9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0dec9-112">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dec9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dec9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0dec9-113">See also</span></span>

- [<span data-ttu-id="0dec9-114">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="0dec9-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="0dec9-115">VariableLocationType 列舉</span><span class="sxs-lookup"><span data-stu-id="0dec9-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
