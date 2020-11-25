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
ms.openlocfilehash: 3979ed19f8a61ac1fc045b83c52e23d7255ac364
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711867"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="4a58b-102">ICorDebugVariableHome：： GetLocationType 方法</span><span class="sxs-lookup"><span data-stu-id="4a58b-102">ICorDebugVariableHome::GetLocationType Method</span></span>

<span data-ttu-id="4a58b-103">取得變數原生位置的型別。</span><span class="sxs-lookup"><span data-stu-id="4a58b-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a58b-104">語法</span><span class="sxs-lookup"><span data-stu-id="4a58b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a58b-105">參數</span><span class="sxs-lookup"><span data-stu-id="4a58b-105">Parameters</span></span>  

 `pLocationType`  
 <span data-ttu-id="4a58b-106">擴展變數原生位置的型別指標。</span><span class="sxs-lookup"><span data-stu-id="4a58b-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="4a58b-107">如需詳細資訊，請參閱 [VariableLocationType](variablelocationtype-enumeration.md) 列舉。</span><span class="sxs-lookup"><span data-stu-id="4a58b-107">See the [VariableLocationType](variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a58b-108">需求</span><span class="sxs-lookup"><span data-stu-id="4a58b-108">Requirements</span></span>  

 <span data-ttu-id="4a58b-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a58b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a58b-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a58b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a58b-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a58b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a58b-112">**.NET Framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a58b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a58b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a58b-113">See also</span></span>

- [<span data-ttu-id="4a58b-114">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="4a58b-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="4a58b-115">VariableLocationType 列舉</span><span class="sxs-lookup"><span data-stu-id="4a58b-115">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
