---
title: ICorDebugAppDomain2 介面 1
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
ms.openlocfilehash: f4549b0fe6379979a7b9bd6344d65ff465f33f17
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506130"
---
# <a name="icordebugappdomain2-interface1"></a><span data-ttu-id="74802-102">ICorDebugAppDomain2 介面 1</span><span class="sxs-lookup"><span data-stu-id="74802-102">ICorDebugAppDomain2 Interface1</span></span>
<span data-ttu-id="74802-103">提供方法來使用陣列、 指標、 函式指標和參考型別。</span><span class="sxs-lookup"><span data-stu-id="74802-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="74802-104">這個介面是 ICorDebugAppDomain 介面的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="74802-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74802-105">方法</span><span class="sxs-lookup"><span data-stu-id="74802-105">Methods</span></span>  
  
|<span data-ttu-id="74802-106">方法</span><span class="sxs-lookup"><span data-stu-id="74802-106">Method</span></span>|<span data-ttu-id="74802-107">描述</span><span class="sxs-lookup"><span data-stu-id="74802-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74802-108">GetArrayOrPointerType 方法</span><span class="sxs-lookup"><span data-stu-id="74802-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="74802-109">取得指定的型別，或是指標或參考指定的型別陣列。</span><span class="sxs-lookup"><span data-stu-id="74802-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="74802-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="74802-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="74802-111">取得具有指定的簽章的函式的指標。</span><span class="sxs-lookup"><span data-stu-id="74802-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74802-112">備註</span><span class="sxs-lookup"><span data-stu-id="74802-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74802-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="74802-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74802-114">需求</span><span class="sxs-lookup"><span data-stu-id="74802-114">Requirements</span></span>  
 <span data-ttu-id="74802-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74802-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74802-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74802-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74802-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74802-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74802-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74802-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74802-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74802-119">See also</span></span>
- [<span data-ttu-id="74802-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="74802-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
