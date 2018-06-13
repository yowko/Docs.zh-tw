---
title: ICorDebugStringValue Interface1
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
ms.openlocfilehash: 2814f6164f383c36bb5b8e20ce8996b30eef0f1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421696"
---
# <a name="icordebugstringvalue-interface1"></a><span data-ttu-id="39c47-102">ICorDebugStringValue Interface1</span><span class="sxs-lookup"><span data-stu-id="39c47-102">ICorDebugStringValue Interface1</span></span>
<span data-ttu-id="39c47-103">ICorDebugHeapValue 套用至字串值的子類別。</span><span class="sxs-lookup"><span data-stu-id="39c47-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="39c47-104">方法</span><span class="sxs-lookup"><span data-stu-id="39c47-104">Methods</span></span>  
  
|<span data-ttu-id="39c47-105">方法</span><span class="sxs-lookup"><span data-stu-id="39c47-105">Method</span></span>|<span data-ttu-id="39c47-106">描述</span><span class="sxs-lookup"><span data-stu-id="39c47-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="39c47-107">GetLength 方法</span><span class="sxs-lookup"><span data-stu-id="39c47-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="39c47-108">取得所參考的字串中的字元數目`ICorDebugStringValue`。</span><span class="sxs-lookup"><span data-stu-id="39c47-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="39c47-109">GetString 方法</span><span class="sxs-lookup"><span data-stu-id="39c47-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="39c47-110">取得所參考的字串`ICorDebugStringValue`。</span><span class="sxs-lookup"><span data-stu-id="39c47-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39c47-111">備註</span><span class="sxs-lookup"><span data-stu-id="39c47-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39c47-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="39c47-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39c47-113">需求</span><span class="sxs-lookup"><span data-stu-id="39c47-113">Requirements</span></span>  
 <span data-ttu-id="39c47-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39c47-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39c47-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39c47-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39c47-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39c47-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39c47-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39c47-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39c47-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39c47-118">See Also</span></span>  
 [<span data-ttu-id="39c47-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="39c47-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
