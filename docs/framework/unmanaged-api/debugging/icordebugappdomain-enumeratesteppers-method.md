---
title: ICorDebugAppDomain::EnumerateSteppers 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateSteppers
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateSteppers
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateSteppers method [.NET Framework debugging]
- EnumerateSteppers method [.NET Framework debugging]
ms.assetid: 3f3c4503-570e-44c1-ae6a-a3c6b840c732
topic_type:
- apiref
ms.openlocfilehash: fd9243d9e0c12b572613694538661fd553e8a487
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715923"
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="15bea-102">ICorDebugAppDomain::EnumerateSteppers 方法</span><span class="sxs-lookup"><span data-stu-id="15bea-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>

<span data-ttu-id="15bea-103">取得應用程式域中所有使用中 steppers 的列舉值。</span><span class="sxs-lookup"><span data-stu-id="15bea-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15bea-104">語法</span><span class="sxs-lookup"><span data-stu-id="15bea-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15bea-105">參數</span><span class="sxs-lookup"><span data-stu-id="15bea-105">Parameters</span></span>  

 `ppSteppers`  
 <span data-ttu-id="15bea-106">擴展ICorDebugStepperEnum 物件位址的指標，該物件是應用程式域中所有使用中 steppers 的列舉值。</span><span class="sxs-lookup"><span data-stu-id="15bea-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15bea-107">需求</span><span class="sxs-lookup"><span data-stu-id="15bea-107">Requirements</span></span>  

 <span data-ttu-id="15bea-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15bea-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15bea-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="15bea-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15bea-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15bea-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15bea-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15bea-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
