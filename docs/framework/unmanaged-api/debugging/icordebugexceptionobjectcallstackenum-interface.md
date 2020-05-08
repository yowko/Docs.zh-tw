---
title: ICorDebugExceptionObjectCallStackEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
ms.openlocfilehash: e6dd951b0f432d455d95bb60f4c42df64d5bee24
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975988"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a><span data-ttu-id="5bf6a-102">ICorDebugExceptionObjectCallStackEnum 介面</span><span class="sxs-lookup"><span data-stu-id="5bf6a-102">ICorDebugExceptionObjectCallStackEnum Interface</span></span>
<span data-ttu-id="5bf6a-103">提供例外狀況物件中內嵌之呼叫堆疊資訊的列舉值。</span><span class="sxs-lookup"><span data-stu-id="5bf6a-103">Provides an enumerator for call stack information that is embedded in an exception object.</span></span> <span data-ttu-id="5bf6a-104">這個介面是 ICorDebugEnum 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="5bf6a-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5bf6a-105">方法</span><span class="sxs-lookup"><span data-stu-id="5bf6a-105">Methods</span></span>  
  
|<span data-ttu-id="5bf6a-106">方法</span><span class="sxs-lookup"><span data-stu-id="5bf6a-106">Method</span></span>|<span data-ttu-id="5bf6a-107">描述</span><span class="sxs-lookup"><span data-stu-id="5bf6a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5bf6a-108">ICorDebugExceptionObjectCallStackEnum：： Next</span><span class="sxs-lookup"><span data-stu-id="5bf6a-108">ICorDebugExceptionObjectCallStackEnum::Next</span></span>](icordebugexceptionobjectcallstackenum-next-method.md)|<span data-ttu-id="5bf6a-109">取得指定數目的[CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md)物件，其中包含例外狀況物件之呼叫堆疊的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5bf6a-109">Gets a specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects that contain information about an exception object's call stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bf6a-110">備註</span><span class="sxs-lookup"><span data-stu-id="5bf6a-110">Remarks</span></span>  
 <span data-ttu-id="5bf6a-111">`ICorDebugExceptionObjectCallStackEnum`介面會實 ICorDebugEnum 介面。</span><span class="sxs-lookup"><span data-stu-id="5bf6a-111">The `ICorDebugExceptionObjectCallStackEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="5bf6a-112">`ICorDebugExceptionObjectCallStackEnum`實例會藉由呼叫[ICorDebugExceptionObjectValue：： EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)方法來填入[CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md)物件。</span><span class="sxs-lookup"><span data-stu-id="5bf6a-112">An `ICorDebugExceptionObjectCallStackEnum` instance is populated with [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) objects by calling the [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) method.</span></span> <span data-ttu-id="5bf6a-113">您可以藉由呼叫[ICorDebugExceptionObjectCallStackEnum：： Next](icordebugexceptionobjectcallstackenum-next-method.md)方法來列舉集合中的呼叫堆疊專案。</span><span class="sxs-lookup"><span data-stu-id="5bf6a-113">The call stack items in the collection can be enumerated by calling the [ICorDebugExceptionObjectCallStackEnum::Next](icordebugexceptionobjectcallstackenum-next-method.md) method</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bf6a-114">需求</span><span class="sxs-lookup"><span data-stu-id="5bf6a-114">Requirements</span></span>  
 <span data-ttu-id="5bf6a-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5bf6a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bf6a-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5bf6a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5bf6a-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bf6a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bf6a-118">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bf6a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf6a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bf6a-119">See also</span></span>

- [<span data-ttu-id="5bf6a-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5bf6a-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5bf6a-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="5bf6a-121">Debugging</span></span>](index.md)
