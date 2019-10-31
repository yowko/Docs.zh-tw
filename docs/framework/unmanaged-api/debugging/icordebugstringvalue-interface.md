---
title: ICorDebugStringValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue
helpviewer_keywords:
- ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type:
- apiref
ms.openlocfilehash: d1d3a5eb6e0b24b40a35c13a99465dd3c7032a91
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138948"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="e2e1f-102">ICorDebugStringValue 介面</span><span class="sxs-lookup"><span data-stu-id="e2e1f-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="e2e1f-103">適用于字串值之 ICorDebugHeapValue 的子類別。</span><span class="sxs-lookup"><span data-stu-id="e2e1f-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2e1f-104">方法</span><span class="sxs-lookup"><span data-stu-id="e2e1f-104">Methods</span></span>  
  
|<span data-ttu-id="e2e1f-105">方法</span><span class="sxs-lookup"><span data-stu-id="e2e1f-105">Method</span></span>|<span data-ttu-id="e2e1f-106">描述</span><span class="sxs-lookup"><span data-stu-id="e2e1f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2e1f-107">GetLength 方法</span><span class="sxs-lookup"><span data-stu-id="e2e1f-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="e2e1f-108">取得此 `ICorDebugStringValue`所參考字串中的字元數。</span><span class="sxs-lookup"><span data-stu-id="e2e1f-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="e2e1f-109">GetString 方法</span><span class="sxs-lookup"><span data-stu-id="e2e1f-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="e2e1f-110">取得此 `ICorDebugStringValue`所參考的字串。</span><span class="sxs-lookup"><span data-stu-id="e2e1f-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2e1f-111">備註</span><span class="sxs-lookup"><span data-stu-id="e2e1f-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2e1f-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="e2e1f-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2e1f-113">需求</span><span class="sxs-lookup"><span data-stu-id="e2e1f-113">Requirements</span></span>  
 <span data-ttu-id="e2e1f-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e2e1f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2e1f-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2e1f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2e1f-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2e1f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2e1f-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2e1f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2e1f-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="e2e1f-118">See also</span></span>

- [<span data-ttu-id="e2e1f-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e2e1f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
