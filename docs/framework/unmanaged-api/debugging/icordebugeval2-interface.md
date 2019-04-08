---
title: ICorDebugEval2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3767368c9da8c97cd081787c0945a15552a1da46
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092665"
---
# <a name="icordebugeval2-interface"></a><span data-ttu-id="70edf-102">ICorDebugEval2 介面</span><span class="sxs-lookup"><span data-stu-id="70edf-102">ICorDebugEval2 Interface</span></span>

<span data-ttu-id="70edf-103">擴充"ICorDebugEval 」 以支援泛型型別。</span><span class="sxs-lookup"><span data-stu-id="70edf-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70edf-104">方法</span><span class="sxs-lookup"><span data-stu-id="70edf-104">Methods</span></span>  
  
|<span data-ttu-id="70edf-105">方法</span><span class="sxs-lookup"><span data-stu-id="70edf-105">Method</span></span>|<span data-ttu-id="70edf-106">描述</span><span class="sxs-lookup"><span data-stu-id="70edf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70edf-107">CallParameterizedFunction 方法</span><span class="sxs-lookup"><span data-stu-id="70edf-107">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="70edf-108">設定指定"ICorDebugFunction 」，這可以巢狀的建構函式會採用型別參數，或本身可以採用型別參數的類型內部呼叫。</span><span class="sxs-lookup"><span data-stu-id="70edf-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="70edf-109">CreateValueForType 方法</span><span class="sxs-lookup"><span data-stu-id="70edf-109">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="70edf-110">取得指標至新的 「 ICorDebugValue"指定的類型，與初始值為 null 或零。</span><span class="sxs-lookup"><span data-stu-id="70edf-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="70edf-111">NewParameterizedArray 方法</span><span class="sxs-lookup"><span data-stu-id="70edf-111">NewParameterizedArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="70edf-112">配置的指定項目類型和維度的新陣列。</span><span class="sxs-lookup"><span data-stu-id="70edf-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="70edf-113">NewParameterizedObject 方法</span><span class="sxs-lookup"><span data-stu-id="70edf-113">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="70edf-114">具現化新的參數化的型別物件，並呼叫物件的建構函式方法。</span><span class="sxs-lookup"><span data-stu-id="70edf-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="70edf-115">NewParameterizedObjectNoConstructor 方法</span><span class="sxs-lookup"><span data-stu-id="70edf-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="70edf-116">產生指定類別的新參數化型的別物件，而不會嘗試呼叫建構函式方法</span><span class="sxs-lookup"><span data-stu-id="70edf-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="70edf-117">NewStringWithLength 方法</span><span class="sxs-lookup"><span data-stu-id="70edf-117">NewStringWithLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="70edf-118">使用指定的內容中建立新的字串，指定長度。</span><span class="sxs-lookup"><span data-stu-id="70edf-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="70edf-119">RudeAbort 方法</span><span class="sxs-lookup"><span data-stu-id="70edf-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|<span data-ttu-id="70edf-120">中止計算這個`ICorDebugEval2`目前正在執行。</span><span class="sxs-lookup"><span data-stu-id="70edf-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70edf-121">備註</span><span class="sxs-lookup"><span data-stu-id="70edf-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70edf-122">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="70edf-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70edf-123">需求</span><span class="sxs-lookup"><span data-stu-id="70edf-123">Requirements</span></span>  
 <span data-ttu-id="70edf-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="70edf-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70edf-125">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70edf-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70edf-126">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70edf-126">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="70edf-127">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="70edf-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="70edf-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70edf-128">See also</span></span>

- [<span data-ttu-id="70edf-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="70edf-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
