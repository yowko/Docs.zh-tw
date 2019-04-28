---
title: ICorDebugAppDomain2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2
helpviewer_keywords:
- ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c6ef901f43cd6568f17657ed8e58bc2cc2cc0a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922261"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="865a2-102">ICorDebugAppDomain2 介面</span><span class="sxs-lookup"><span data-stu-id="865a2-102">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="865a2-103">提供方法來使用陣列、 指標、 函式指標和參考型別。</span><span class="sxs-lookup"><span data-stu-id="865a2-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="865a2-104">這個介面是 ICorDebugAppDomain 介面的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="865a2-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="865a2-105">方法</span><span class="sxs-lookup"><span data-stu-id="865a2-105">Methods</span></span>  
  
|<span data-ttu-id="865a2-106">方法</span><span class="sxs-lookup"><span data-stu-id="865a2-106">Method</span></span>|<span data-ttu-id="865a2-107">描述</span><span class="sxs-lookup"><span data-stu-id="865a2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="865a2-108">GetArrayOrPointerType 方法</span><span class="sxs-lookup"><span data-stu-id="865a2-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="865a2-109">取得指定的型別，或是指標或參考指定的型別陣列。</span><span class="sxs-lookup"><span data-stu-id="865a2-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="865a2-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="865a2-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="865a2-111">取得具有指定的簽章的函式的指標。</span><span class="sxs-lookup"><span data-stu-id="865a2-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="865a2-112">備註</span><span class="sxs-lookup"><span data-stu-id="865a2-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="865a2-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="865a2-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="865a2-114">需求</span><span class="sxs-lookup"><span data-stu-id="865a2-114">Requirements</span></span>  
 <span data-ttu-id="865a2-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="865a2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="865a2-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="865a2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="865a2-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="865a2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="865a2-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="865a2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="865a2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="865a2-119">See also</span></span>

- [<span data-ttu-id="865a2-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="865a2-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
