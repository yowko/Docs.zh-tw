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
ms.openlocfilehash: 82b58780472443874f2dae93c2d8568006db2e8a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978562"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="a5b2e-102">ICorDebugAppDomain2 介面</span><span class="sxs-lookup"><span data-stu-id="a5b2e-102">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="a5b2e-103">提供方法來使用陣列、 指標、 函式指標和參考型別。</span><span class="sxs-lookup"><span data-stu-id="a5b2e-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="a5b2e-104">這個介面是 ICorDebugAppDomain 介面的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="a5b2e-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5b2e-105">方法</span><span class="sxs-lookup"><span data-stu-id="a5b2e-105">Methods</span></span>  
  
|<span data-ttu-id="a5b2e-106">方法</span><span class="sxs-lookup"><span data-stu-id="a5b2e-106">Method</span></span>|<span data-ttu-id="a5b2e-107">描述</span><span class="sxs-lookup"><span data-stu-id="a5b2e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5b2e-108">GetArrayOrPointerType 方法</span><span class="sxs-lookup"><span data-stu-id="a5b2e-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="a5b2e-109">取得指定的型別，或是指標或參考指定的型別陣列。</span><span class="sxs-lookup"><span data-stu-id="a5b2e-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="a5b2e-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="a5b2e-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="a5b2e-111">取得具有指定的簽章的函式的指標。</span><span class="sxs-lookup"><span data-stu-id="a5b2e-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5b2e-112">備註</span><span class="sxs-lookup"><span data-stu-id="a5b2e-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5b2e-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="a5b2e-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5b2e-114">需求</span><span class="sxs-lookup"><span data-stu-id="a5b2e-114">Requirements</span></span>  
 <span data-ttu-id="a5b2e-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5b2e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5b2e-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5b2e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5b2e-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5b2e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5b2e-118">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5b2e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b2e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5b2e-119">See also</span></span>
- [<span data-ttu-id="a5b2e-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a5b2e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
