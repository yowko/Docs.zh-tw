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
ms.openlocfilehash: 5d33c917ab814083ec2f3a3f3de6bdc264d90b77
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791012"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="4f10d-102">ICorDebugVariableHome：： GetLocationType 方法</span><span class="sxs-lookup"><span data-stu-id="4f10d-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="4f10d-103">取得變數原生位置的類型。</span><span class="sxs-lookup"><span data-stu-id="4f10d-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f10d-104">語法</span><span class="sxs-lookup"><span data-stu-id="4f10d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f10d-105">參數</span><span class="sxs-lookup"><span data-stu-id="4f10d-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="4f10d-106">脫銷變數原生位置之類型的指標。</span><span class="sxs-lookup"><span data-stu-id="4f10d-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="4f10d-107">如需詳細資訊，請參閱[VariableLocationType](variablelocationtype-enumeration.md)列舉。</span><span class="sxs-lookup"><span data-stu-id="4f10d-107">See the [VariableLocationType](variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f10d-108">需求</span><span class="sxs-lookup"><span data-stu-id="4f10d-108">Requirements</span></span>  
 <span data-ttu-id="4f10d-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4f10d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f10d-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f10d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f10d-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f10d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f10d-112">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f10d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f10d-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="4f10d-113">See also</span></span>

- [<span data-ttu-id="4f10d-114">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="4f10d-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="4f10d-115">VariableLocationType 列舉</span><span class="sxs-lookup"><span data-stu-id="4f10d-115">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
