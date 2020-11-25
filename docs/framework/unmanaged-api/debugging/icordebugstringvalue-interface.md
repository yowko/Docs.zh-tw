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
ms.openlocfilehash: cd6c5726b9a938d04cf4eb018ec9851c81d9c745
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697047"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="458dc-102">ICorDebugStringValue 介面</span><span class="sxs-lookup"><span data-stu-id="458dc-102">ICorDebugStringValue Interface</span></span>

<span data-ttu-id="458dc-103">套用至字串值之 ICorDebugHeapValue 的子類別。</span><span class="sxs-lookup"><span data-stu-id="458dc-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="458dc-104">方法</span><span class="sxs-lookup"><span data-stu-id="458dc-104">Methods</span></span>  
  
|<span data-ttu-id="458dc-105">方法</span><span class="sxs-lookup"><span data-stu-id="458dc-105">Method</span></span>|<span data-ttu-id="458dc-106">描述</span><span class="sxs-lookup"><span data-stu-id="458dc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="458dc-107">GetLength 方法</span><span class="sxs-lookup"><span data-stu-id="458dc-107">GetLength Method</span></span>](icordebugstringvalue-getlength-method.md)|<span data-ttu-id="458dc-108">取得這個所參考之字串中的字元數 `ICorDebugStringValue` 。</span><span class="sxs-lookup"><span data-stu-id="458dc-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="458dc-109">GetString 方法</span><span class="sxs-lookup"><span data-stu-id="458dc-109">GetString Method</span></span>](icordebugstringvalue-getstring-method.md)|<span data-ttu-id="458dc-110">取得這個所參考的字串 `ICorDebugStringValue` 。</span><span class="sxs-lookup"><span data-stu-id="458dc-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="458dc-111">備註</span><span class="sxs-lookup"><span data-stu-id="458dc-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="458dc-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="458dc-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="458dc-113">需求</span><span class="sxs-lookup"><span data-stu-id="458dc-113">Requirements</span></span>  

 <span data-ttu-id="458dc-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="458dc-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="458dc-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="458dc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="458dc-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="458dc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="458dc-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="458dc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="458dc-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="458dc-118">See also</span></span>

- [<span data-ttu-id="458dc-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="458dc-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
