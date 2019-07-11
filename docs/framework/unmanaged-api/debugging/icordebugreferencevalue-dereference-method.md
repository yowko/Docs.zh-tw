---
title: ICorDebugReferenceValue::Dereference 方法
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2ea7ebff122622a0db46160d23574619664f8ad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745030"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="8823a-102">ICorDebugReferenceValue::Dereference 方法</span><span class="sxs-lookup"><span data-stu-id="8823a-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="8823a-103">取得參考的物件。</span><span class="sxs-lookup"><span data-stu-id="8823a-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8823a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8823a-104">Syntax</span></span>  
  
```cpp  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8823a-105">參數</span><span class="sxs-lookup"><span data-stu-id="8823a-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="8823a-106">[out]ICorDebugValue，表示這個 ICorDebugReferenceValue 物件指向的物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="8823a-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8823a-107">備註</span><span class="sxs-lookup"><span data-stu-id="8823a-107">Remarks</span></span>  
 <span data-ttu-id="8823a-108">`ICorDebugValue`物件是有效的只有當尚未停其參考時。</span><span class="sxs-lookup"><span data-stu-id="8823a-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8823a-109">需求</span><span class="sxs-lookup"><span data-stu-id="8823a-109">Requirements</span></span>  
 <span data-ttu-id="8823a-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8823a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8823a-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8823a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8823a-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8823a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8823a-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8823a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
