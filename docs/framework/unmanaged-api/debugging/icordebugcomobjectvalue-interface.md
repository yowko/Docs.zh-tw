---
title: ICorDebugComObjectValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3387985ebf6027b9cd9dee372190da65939dbae3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749692"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="546ee-102">ICorDebugComObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="546ee-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="546ee-103">提供方法來擷取執行階段可呼叫包裝函式 (RCW) 相關聯的資訊。</span><span class="sxs-lookup"><span data-stu-id="546ee-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="546ee-104">方法</span><span class="sxs-lookup"><span data-stu-id="546ee-104">Methods</span></span>  
  
|<span data-ttu-id="546ee-105">方法</span><span class="sxs-lookup"><span data-stu-id="546ee-105">Method</span></span>|<span data-ttu-id="546ee-106">描述</span><span class="sxs-lookup"><span data-stu-id="546ee-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="546ee-107">GetCachedInterfacePointers 方法</span><span class="sxs-lookup"><span data-stu-id="546ee-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="546ee-108">取得在目前的 RCW 上快取的原始介面指標。</span><span class="sxs-lookup"><span data-stu-id="546ee-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="546ee-109">GetCachedInterfaceTypes 方法</span><span class="sxs-lookup"><span data-stu-id="546ee-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="546ee-110">目前的物件具有要使用的大小寫或做為介面類型提供列舉值。</span><span class="sxs-lookup"><span data-stu-id="546ee-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="546ee-111">備註</span><span class="sxs-lookup"><span data-stu-id="546ee-111">Remarks</span></span>  
 <span data-ttu-id="546ee-112">若要檢查 「 ICorDebugValue 」 介面的執行個體是否代表 RCW，偵錯工具會呼叫`QueryInterface`"ICorDebugValue 」 與上`IID_ICorDebugComObjectValue`。</span><span class="sxs-lookup"><span data-stu-id="546ee-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="546ee-113">需求</span><span class="sxs-lookup"><span data-stu-id="546ee-113">Requirements</span></span>  
 <span data-ttu-id="546ee-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="546ee-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="546ee-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="546ee-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="546ee-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="546ee-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="546ee-117">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="546ee-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="546ee-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="546ee-118">See also</span></span>

- [<span data-ttu-id="546ee-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="546ee-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="546ee-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="546ee-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
