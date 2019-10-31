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
ms.openlocfilehash: 49c1b97540644fb48509be3bb988c51c5d11fd8b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084864"
---
# <a name="icordebugeval2-interface"></a><span data-ttu-id="55203-102">ICorDebugEval2 介面</span><span class="sxs-lookup"><span data-stu-id="55203-102">ICorDebugEval2 Interface</span></span>

<span data-ttu-id="55203-103">擴充 "ICorDebugEval" 以提供泛型型別的支援。</span><span class="sxs-lookup"><span data-stu-id="55203-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="55203-104">方法</span><span class="sxs-lookup"><span data-stu-id="55203-104">Methods</span></span>  
  
|<span data-ttu-id="55203-105">方法</span><span class="sxs-lookup"><span data-stu-id="55203-105">Method</span></span>|<span data-ttu-id="55203-106">描述</span><span class="sxs-lookup"><span data-stu-id="55203-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="55203-107">CallParameterizedFunction 方法</span><span class="sxs-lookup"><span data-stu-id="55203-107">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="55203-108">設定對指定 "ICorDebugFunction" 的呼叫，其可以嵌套在型別中，而此類型的函式會採用型別參數，或者本身可以接受型別參數。</span><span class="sxs-lookup"><span data-stu-id="55203-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="55203-109">CreateValueForType 方法</span><span class="sxs-lookup"><span data-stu-id="55203-109">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="55203-110">取得指定類型之新 "ICorDebugValue" 的指標，其初始值為 null 或零。</span><span class="sxs-lookup"><span data-stu-id="55203-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="55203-111">NewParameterizedArray 方法</span><span class="sxs-lookup"><span data-stu-id="55203-111">NewParameterizedArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="55203-112">配置指定之元素類型和維度的新陣列。</span><span class="sxs-lookup"><span data-stu-id="55203-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="55203-113">NewParameterizedObject 方法</span><span class="sxs-lookup"><span data-stu-id="55203-113">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="55203-114">具現化新的參數化型別物件，並呼叫物件的函式方法。</span><span class="sxs-lookup"><span data-stu-id="55203-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="55203-115">NewParameterizedObjectNoConstructor 方法</span><span class="sxs-lookup"><span data-stu-id="55203-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="55203-116">在不嘗試呼叫函式方法的情況下，具現化指定類別的新參數化型別物件</span><span class="sxs-lookup"><span data-stu-id="55203-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="55203-117">NewStringWithLength 方法</span><span class="sxs-lookup"><span data-stu-id="55203-117">NewStringWithLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="55203-118">使用指定的內容，建立指定長度的新字串。</span><span class="sxs-lookup"><span data-stu-id="55203-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="55203-119">RudeAbort 方法</span><span class="sxs-lookup"><span data-stu-id="55203-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|<span data-ttu-id="55203-120">中止此 `ICorDebugEval2` 目前正在執行的計算。</span><span class="sxs-lookup"><span data-stu-id="55203-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55203-121">備註</span><span class="sxs-lookup"><span data-stu-id="55203-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55203-122">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="55203-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55203-123">需求</span><span class="sxs-lookup"><span data-stu-id="55203-123">Requirements</span></span>  
 <span data-ttu-id="55203-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="55203-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55203-125">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55203-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55203-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55203-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55203-127">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55203-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55203-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="55203-128">See also</span></span>

- [<span data-ttu-id="55203-129">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="55203-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
