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
ms.openlocfilehash: f20ae6977504f958b7bfa8e2f073b7db6e8b822b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731471"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="b3234-102">ICorDebugAppDomain2 介面</span><span class="sxs-lookup"><span data-stu-id="b3234-102">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="b3234-103">提供使用陣列、指標、函式指標和參考型別的方法。</span><span class="sxs-lookup"><span data-stu-id="b3234-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="b3234-104">此介面是 ICorDebugAppDomain 介面的延伸。</span><span class="sxs-lookup"><span data-stu-id="b3234-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b3234-105">方法</span><span class="sxs-lookup"><span data-stu-id="b3234-105">Methods</span></span>  
  
|<span data-ttu-id="b3234-106">方法</span><span class="sxs-lookup"><span data-stu-id="b3234-106">Method</span></span>|<span data-ttu-id="b3234-107">描述</span><span class="sxs-lookup"><span data-stu-id="b3234-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b3234-108">GetArrayOrPointerType 方法</span><span class="sxs-lookup"><span data-stu-id="b3234-108">GetArrayOrPointerType Method</span></span>](icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="b3234-109">取得指定類型的陣列，或指定類型的指標或參考。</span><span class="sxs-lookup"><span data-stu-id="b3234-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="b3234-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="b3234-110">GetFunctionPointerType</span></span>](icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="b3234-111">取得具有指定簽章之函式的指標。</span><span class="sxs-lookup"><span data-stu-id="b3234-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3234-112">備註</span><span class="sxs-lookup"><span data-stu-id="b3234-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3234-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b3234-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3234-114">需求</span><span class="sxs-lookup"><span data-stu-id="b3234-114">Requirements</span></span>  

 <span data-ttu-id="b3234-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3234-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3234-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3234-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3234-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3234-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3234-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3234-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3234-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3234-119">See also</span></span>

- [<span data-ttu-id="b3234-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b3234-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
