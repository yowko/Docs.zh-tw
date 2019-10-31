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
ms.openlocfilehash: 4ff5c0d470e6eb84eb8b526f5e8f74e5e1a8118a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125480"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="f8a20-102">ICorDebugComObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="f8a20-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="f8a20-103">提供方法來取得與執行時間可呼叫包裝函式（RCW）相關聯的資訊。</span><span class="sxs-lookup"><span data-stu-id="f8a20-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8a20-104">方法</span><span class="sxs-lookup"><span data-stu-id="f8a20-104">Methods</span></span>  
  
|<span data-ttu-id="f8a20-105">方法</span><span class="sxs-lookup"><span data-stu-id="f8a20-105">Method</span></span>|<span data-ttu-id="f8a20-106">描述</span><span class="sxs-lookup"><span data-stu-id="f8a20-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8a20-107">GetCachedInterfacePointers 方法</span><span class="sxs-lookup"><span data-stu-id="f8a20-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="f8a20-108">取得目前 RCW 上快取的原始介面指標。</span><span class="sxs-lookup"><span data-stu-id="f8a20-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="f8a20-109">GetCachedInterfaceTypes 方法</span><span class="sxs-lookup"><span data-stu-id="f8a20-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="f8a20-110">提供目前物件已做為大小寫或當做使用之介面類別型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="f8a20-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8a20-111">備註</span><span class="sxs-lookup"><span data-stu-id="f8a20-111">Remarks</span></span>  
 <span data-ttu-id="f8a20-112">若要檢查 "ICorDebugValue" 介面的實例是否代表 RCW，偵錯工具會使用 `IID_ICorDebugComObjectValue`呼叫 "ICorDebugValue" 上的 `QueryInterface`。</span><span class="sxs-lookup"><span data-stu-id="f8a20-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8a20-113">需求</span><span class="sxs-lookup"><span data-stu-id="f8a20-113">Requirements</span></span>  
 <span data-ttu-id="f8a20-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f8a20-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8a20-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8a20-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8a20-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8a20-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8a20-117">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8a20-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8a20-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="f8a20-118">See also</span></span>

- [<span data-ttu-id="f8a20-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="f8a20-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f8a20-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="f8a20-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
