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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6709b14ce8e7bc131f9feb7a277fb41851ee4352
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173988"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="81124-102">ICorDebugStringValue 介面</span><span class="sxs-lookup"><span data-stu-id="81124-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="81124-103">ICorDebugHeapValue 套用至字串值的子類別。</span><span class="sxs-lookup"><span data-stu-id="81124-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="81124-104">方法</span><span class="sxs-lookup"><span data-stu-id="81124-104">Methods</span></span>  
  
|<span data-ttu-id="81124-105">方法</span><span class="sxs-lookup"><span data-stu-id="81124-105">Method</span></span>|<span data-ttu-id="81124-106">描述</span><span class="sxs-lookup"><span data-stu-id="81124-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="81124-107">GetLength 方法</span><span class="sxs-lookup"><span data-stu-id="81124-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="81124-108">取得所參考的字串中的字元數目`ICorDebugStringValue`。</span><span class="sxs-lookup"><span data-stu-id="81124-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="81124-109">GetString 方法</span><span class="sxs-lookup"><span data-stu-id="81124-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="81124-110">取得所參考的字串`ICorDebugStringValue`。</span><span class="sxs-lookup"><span data-stu-id="81124-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81124-111">備註</span><span class="sxs-lookup"><span data-stu-id="81124-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81124-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="81124-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81124-113">需求</span><span class="sxs-lookup"><span data-stu-id="81124-113">Requirements</span></span>  
 <span data-ttu-id="81124-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81124-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81124-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81124-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81124-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81124-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="81124-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="81124-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="81124-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81124-118">See also</span></span>

- [<span data-ttu-id="81124-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="81124-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
