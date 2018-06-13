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
ms.openlocfilehash: 11afee9c2a84999ccad2cdc12e2a14a4dc17d542
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412511"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="b8f4d-102">ICorDebugComObjectValue 介面</span><span class="sxs-lookup"><span data-stu-id="b8f4d-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="b8f4d-103">提供方法來擷取執行階段可呼叫包裝函式 (RCW) 相關聯的資訊。</span><span class="sxs-lookup"><span data-stu-id="b8f4d-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b8f4d-104">方法</span><span class="sxs-lookup"><span data-stu-id="b8f4d-104">Methods</span></span>  
  
|<span data-ttu-id="b8f4d-105">方法</span><span class="sxs-lookup"><span data-stu-id="b8f4d-105">Method</span></span>|<span data-ttu-id="b8f4d-106">描述</span><span class="sxs-lookup"><span data-stu-id="b8f4d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b8f4d-107">GetCachedInterfacePointers 方法</span><span class="sxs-lookup"><span data-stu-id="b8f4d-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="b8f4d-108">取得目前的 RCW 上快取的原始介面指標。</span><span class="sxs-lookup"><span data-stu-id="b8f4d-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="b8f4d-109">GetCachedInterfaceTypes 方法</span><span class="sxs-lookup"><span data-stu-id="b8f4d-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="b8f4d-110">目前的物件有大小寫，以或做為提供的介面類型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="b8f4d-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8f4d-111">備註</span><span class="sxs-lookup"><span data-stu-id="b8f4d-111">Remarks</span></span>  
 <span data-ttu-id="b8f4d-112">若要檢查 「 ICorDebugValue 」 介面的執行個體是否表示 RCW，偵錯工具呼叫`QueryInterface`上 「 ICorDebugValue"與`IID_ICorDebugComObjectValue`。</span><span class="sxs-lookup"><span data-stu-id="b8f4d-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8f4d-113">需求</span><span class="sxs-lookup"><span data-stu-id="b8f4d-113">Requirements</span></span>  
 <span data-ttu-id="b8f4d-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b8f4d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8f4d-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8f4d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8f4d-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8f4d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8f4d-117">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8f4d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8f4d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8f4d-118">See Also</span></span>  
 [<span data-ttu-id="b8f4d-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b8f4d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b8f4d-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="b8f4d-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
