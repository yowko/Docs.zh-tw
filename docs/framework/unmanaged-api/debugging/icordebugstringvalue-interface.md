---
title: ICorDebugStringValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStringValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStringValue
helpviewer_keywords: ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9958e6f5ad73658b278d83c78e58cf4166d5642
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstringvalue-interface1"></a><span data-ttu-id="eba76-102">ICorDebugStringValue Interface1</span><span class="sxs-lookup"><span data-stu-id="eba76-102">ICorDebugStringValue Interface1</span></span>
<span data-ttu-id="eba76-103">ICorDebugHeapValue 套用至字串值的子類別。</span><span class="sxs-lookup"><span data-stu-id="eba76-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eba76-104">方法</span><span class="sxs-lookup"><span data-stu-id="eba76-104">Methods</span></span>  
  
|<span data-ttu-id="eba76-105">方法</span><span class="sxs-lookup"><span data-stu-id="eba76-105">Method</span></span>|<span data-ttu-id="eba76-106">描述</span><span class="sxs-lookup"><span data-stu-id="eba76-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eba76-107">GetLength 方法</span><span class="sxs-lookup"><span data-stu-id="eba76-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="eba76-108">取得所參考的字串中的字元數目`ICorDebugStringValue`。</span><span class="sxs-lookup"><span data-stu-id="eba76-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="eba76-109">GetString 方法</span><span class="sxs-lookup"><span data-stu-id="eba76-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="eba76-110">取得所參考的字串`ICorDebugStringValue`。</span><span class="sxs-lookup"><span data-stu-id="eba76-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eba76-111">備註</span><span class="sxs-lookup"><span data-stu-id="eba76-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eba76-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="eba76-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eba76-113">需求</span><span class="sxs-lookup"><span data-stu-id="eba76-113">Requirements</span></span>  
 <span data-ttu-id="eba76-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eba76-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eba76-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eba76-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eba76-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eba76-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eba76-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eba76-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba76-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="eba76-118">See Also</span></span>  
 [<span data-ttu-id="eba76-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="eba76-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
