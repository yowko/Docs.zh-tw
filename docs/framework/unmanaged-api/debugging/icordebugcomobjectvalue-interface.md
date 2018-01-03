---
title: "ICorDebugComObjectValue 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugComObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugComObjectValue
helpviewer_keywords: ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9adeec14e102ef575f24566980477a285f87ba40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="5e38f-102">ICorDebugComObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="5e38f-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="5e38f-103">提供方法來擷取執行階段可呼叫包裝函式 (RCW) 相關聯的資訊。</span><span class="sxs-lookup"><span data-stu-id="5e38f-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e38f-104">方法</span><span class="sxs-lookup"><span data-stu-id="5e38f-104">Methods</span></span>  
  
|<span data-ttu-id="5e38f-105">方法</span><span class="sxs-lookup"><span data-stu-id="5e38f-105">Method</span></span>|<span data-ttu-id="5e38f-106">描述</span><span class="sxs-lookup"><span data-stu-id="5e38f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e38f-107">GetCachedInterfacePointers 方法</span><span class="sxs-lookup"><span data-stu-id="5e38f-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="5e38f-108">取得目前的 RCW 上快取的原始介面指標。</span><span class="sxs-lookup"><span data-stu-id="5e38f-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="5e38f-109">GetCachedInterfaceTypes 方法</span><span class="sxs-lookup"><span data-stu-id="5e38f-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="5e38f-110">目前的物件有大小寫，以或做為提供的介面類型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="5e38f-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e38f-111">備註</span><span class="sxs-lookup"><span data-stu-id="5e38f-111">Remarks</span></span>  
 <span data-ttu-id="5e38f-112">若要檢查 「 ICorDebugValue 」 介面的執行個體是否表示 RCW，偵錯工具呼叫`QueryInterface`上 「 ICorDebugValue"與`IID_ICorDebugComObjectValue`。</span><span class="sxs-lookup"><span data-stu-id="5e38f-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e38f-113">需求</span><span class="sxs-lookup"><span data-stu-id="5e38f-113">Requirements</span></span>  
 <span data-ttu-id="5e38f-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e38f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e38f-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e38f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e38f-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e38f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e38f-117">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e38f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e38f-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="5e38f-118">See Also</span></span>  
 [<span data-ttu-id="5e38f-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5e38f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="5e38f-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="5e38f-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
