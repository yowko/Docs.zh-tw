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
ms.openlocfilehash: 1f6a8b0ead430ffdd0e4e30cacae54d68fa9d730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969267"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="d87a2-102">ICorDebugClass2 介面</span><span class="sxs-lookup"><span data-stu-id="d87a2-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="d87a2-103">表示泛型類別，或是具有 <xref:System.Type> 類型之方法參數的類別。</span><span class="sxs-lookup"><span data-stu-id="d87a2-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="d87a2-104">這個介面會擴充[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="d87a2-104">This interface extends [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d87a2-105">方法</span><span class="sxs-lookup"><span data-stu-id="d87a2-105">Methods</span></span>  
  
|<span data-ttu-id="d87a2-106">方法</span><span class="sxs-lookup"><span data-stu-id="d87a2-106">Method</span></span>|<span data-ttu-id="d87a2-107">說明</span><span class="sxs-lookup"><span data-stu-id="d87a2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d87a2-108">GetParameterizedType 方法</span><span class="sxs-lookup"><span data-stu-id="d87a2-108">GetParameterizedType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="d87a2-109">取得這個類別的類型宣告。</span><span class="sxs-lookup"><span data-stu-id="d87a2-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="d87a2-110">SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="d87a2-110">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="d87a2-111">針對這個類別的每個方法, 設定一個值, 指出此方法是否為使用者定義的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d87a2-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d87a2-112">備註</span><span class="sxs-lookup"><span data-stu-id="d87a2-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d87a2-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="d87a2-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d87a2-114">需求</span><span class="sxs-lookup"><span data-stu-id="d87a2-114">Requirements</span></span>  
 <span data-ttu-id="d87a2-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d87a2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d87a2-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d87a2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d87a2-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d87a2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d87a2-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d87a2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d87a2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d87a2-119">See also</span></span>

- [<span data-ttu-id="d87a2-120">ICorDebugClass 介面</span><span class="sxs-lookup"><span data-stu-id="d87a2-120">ICorDebugClass Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)
- [<span data-ttu-id="d87a2-121">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d87a2-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
