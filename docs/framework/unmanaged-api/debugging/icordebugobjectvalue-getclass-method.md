---
title: ICorDebugObjectValue::GetClass 方法
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type:
- apiref
ms.openlocfilehash: d15938e94d647fd5fded23c72bdc200d198d21a7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792697"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="381d2-102">ICorDebugObjectValue::GetClass 方法</span><span class="sxs-lookup"><span data-stu-id="381d2-102">ICorDebugObjectValue::GetClass Method</span></span>
<span data-ttu-id="381d2-103">取得這個物件值的類別。</span><span class="sxs-lookup"><span data-stu-id="381d2-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="381d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="381d2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="381d2-105">參數</span><span class="sxs-lookup"><span data-stu-id="381d2-105">Parameters</span></span>  
 `ppClass`  
 <span data-ttu-id="381d2-106">脫銷"ICorDebugClass" 物件位址的指標，代表這個 "ICorDebugObjectValue" 物件所表示之物件值的類別。</span><span class="sxs-lookup"><span data-stu-id="381d2-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="381d2-107">備註</span><span class="sxs-lookup"><span data-stu-id="381d2-107">Remarks</span></span>  
 <span data-ttu-id="381d2-108">`GetClass` 和[ICorDebugValue：： GetType](icordebugvalue-gettype-method.md)方法都會傳回數值型別的相關資訊;兩者都被泛型感知[ICorDebugValue2：： GetExactType](icordebugvalue2-getexacttype-method.md)所取代。</span><span class="sxs-lookup"><span data-stu-id="381d2-108">The `GetClass` and [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="381d2-109">需求</span><span class="sxs-lookup"><span data-stu-id="381d2-109">Requirements</span></span>  
 <span data-ttu-id="381d2-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="381d2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="381d2-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="381d2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="381d2-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="381d2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="381d2-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="381d2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="381d2-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="381d2-114">See also</span></span>
