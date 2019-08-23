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
ms.openlocfilehash: 1cfaf886d09d843f4dbf61af55a9388454b050ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957419"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="82492-102">ICorDebugStringValue 介面</span><span class="sxs-lookup"><span data-stu-id="82492-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="82492-103">適用于字串值之 ICorDebugHeapValue 的子類別。</span><span class="sxs-lookup"><span data-stu-id="82492-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82492-104">方法</span><span class="sxs-lookup"><span data-stu-id="82492-104">Methods</span></span>  
  
|<span data-ttu-id="82492-105">方法</span><span class="sxs-lookup"><span data-stu-id="82492-105">Method</span></span>|<span data-ttu-id="82492-106">說明</span><span class="sxs-lookup"><span data-stu-id="82492-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82492-107">GetLength 方法</span><span class="sxs-lookup"><span data-stu-id="82492-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="82492-108">取得這個`ICorDebugStringValue`所參考字串中的字元數。</span><span class="sxs-lookup"><span data-stu-id="82492-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="82492-109">GetString 方法</span><span class="sxs-lookup"><span data-stu-id="82492-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="82492-110">取得這個`ICorDebugStringValue`所參考的字串。</span><span class="sxs-lookup"><span data-stu-id="82492-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82492-111">備註</span><span class="sxs-lookup"><span data-stu-id="82492-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82492-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="82492-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82492-113">需求</span><span class="sxs-lookup"><span data-stu-id="82492-113">Requirements</span></span>  
 <span data-ttu-id="82492-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="82492-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82492-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82492-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82492-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82492-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82492-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82492-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82492-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82492-118">See also</span></span>

- [<span data-ttu-id="82492-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="82492-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
