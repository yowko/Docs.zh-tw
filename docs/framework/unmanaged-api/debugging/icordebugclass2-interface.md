---
title: ICorDebugClass2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 015085cff23028814937dfef9aea19af7438b4f5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750601"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="c6d5f-102">ICorDebugClass2 介面</span><span class="sxs-lookup"><span data-stu-id="c6d5f-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="c6d5f-103">表示泛型類別，或是具有 <xref:System.Type> 類型之方法參數的類別。</span><span class="sxs-lookup"><span data-stu-id="c6d5f-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="c6d5f-104">這個介面會擴充[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="c6d5f-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c6d5f-105">方法</span><span class="sxs-lookup"><span data-stu-id="c6d5f-105">Methods</span></span>  
  
|<span data-ttu-id="c6d5f-106">方法</span><span class="sxs-lookup"><span data-stu-id="c6d5f-106">Method</span></span>|<span data-ttu-id="c6d5f-107">描述</span><span class="sxs-lookup"><span data-stu-id="c6d5f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c6d5f-108">GetParameterizedType 方法</span><span class="sxs-lookup"><span data-stu-id="c6d5f-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="c6d5f-109">取得這個類別的型別宣告。</span><span class="sxs-lookup"><span data-stu-id="c6d5f-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="c6d5f-110">SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="c6d5f-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="c6d5f-111">這個類別的每個方法，設定值，指出方法是否為使用者定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c6d5f-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6d5f-112">備註</span><span class="sxs-lookup"><span data-stu-id="c6d5f-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6d5f-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="c6d5f-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6d5f-114">需求</span><span class="sxs-lookup"><span data-stu-id="c6d5f-114">Requirements</span></span>  
 <span data-ttu-id="c6d5f-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c6d5f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6d5f-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6d5f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6d5f-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6d5f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6d5f-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6d5f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6d5f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6d5f-119">See also</span></span>

- [<span data-ttu-id="c6d5f-120">ICorDebugClass 介面</span><span class="sxs-lookup"><span data-stu-id="c6d5f-120">ICorDebugClass Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)
- [<span data-ttu-id="c6d5f-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="c6d5f-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
