---
title: ICorDebugVariableHome：： GetLocationType 方法
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
ms.openlocfilehash: 8874deede8b46b93df0e298fb3970fa153b51415
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396565"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="5bbda-102">ICorDebugVariableHome：： GetLocationType 方法</span><span class="sxs-lookup"><span data-stu-id="5bbda-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="5bbda-103">取得變數原生位置的類型。</span><span class="sxs-lookup"><span data-stu-id="5bbda-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bbda-104">語法</span><span class="sxs-lookup"><span data-stu-id="5bbda-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bbda-105">參數</span><span class="sxs-lookup"><span data-stu-id="5bbda-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="5bbda-106">脫銷變數原生位置之類型的指標。</span><span class="sxs-lookup"><span data-stu-id="5bbda-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="5bbda-107">如需詳細資訊，請參閱[VariableLocationType](variablelocationtype-enumeration.md)列舉。</span><span class="sxs-lookup"><span data-stu-id="5bbda-107">See the [VariableLocationType](variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bbda-108">需求</span><span class="sxs-lookup"><span data-stu-id="5bbda-108">Requirements</span></span>  
 <span data-ttu-id="5bbda-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5bbda-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bbda-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5bbda-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5bbda-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bbda-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bbda-112">**.NET Framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bbda-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bbda-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="5bbda-113">See also</span></span>

- [<span data-ttu-id="5bbda-114">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="5bbda-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="5bbda-115">VariableLocationType 列舉</span><span class="sxs-lookup"><span data-stu-id="5bbda-115">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
