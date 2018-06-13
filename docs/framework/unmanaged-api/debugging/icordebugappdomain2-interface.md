---
title: ICorDebugAppDomain2 Interface1
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
ms.openlocfilehash: ff6ffdd733cf6e7b923d88d057d7cd230c8d8541
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407111"
---
# <a name="icordebugappdomain2-interface1"></a><span data-ttu-id="b4fd2-102">ICorDebugAppDomain2 Interface1</span><span class="sxs-lookup"><span data-stu-id="b4fd2-102">ICorDebugAppDomain2 Interface1</span></span>
<span data-ttu-id="b4fd2-103">提供方法來處理陣列、 指標、 函式指標和參考型別。</span><span class="sxs-lookup"><span data-stu-id="b4fd2-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="b4fd2-104">這個介面是 ICorDebugAppDomain 介面的擴充功能。</span><span class="sxs-lookup"><span data-stu-id="b4fd2-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4fd2-105">方法</span><span class="sxs-lookup"><span data-stu-id="b4fd2-105">Methods</span></span>  
  
|<span data-ttu-id="b4fd2-106">方法</span><span class="sxs-lookup"><span data-stu-id="b4fd2-106">Method</span></span>|<span data-ttu-id="b4fd2-107">描述</span><span class="sxs-lookup"><span data-stu-id="b4fd2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4fd2-108">GetArrayOrPointerType 方法</span><span class="sxs-lookup"><span data-stu-id="b4fd2-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="b4fd2-109">取得指定的型別，或是指標或參考指定之類型的陣列。</span><span class="sxs-lookup"><span data-stu-id="b4fd2-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="b4fd2-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="b4fd2-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="b4fd2-111">取得具有指定簽章的函式指標。</span><span class="sxs-lookup"><span data-stu-id="b4fd2-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4fd2-112">備註</span><span class="sxs-lookup"><span data-stu-id="b4fd2-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4fd2-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b4fd2-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4fd2-114">需求</span><span class="sxs-lookup"><span data-stu-id="b4fd2-114">Requirements</span></span>  
 <span data-ttu-id="b4fd2-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4fd2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4fd2-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4fd2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4fd2-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4fd2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4fd2-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4fd2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4fd2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4fd2-119">See Also</span></span>  
 [<span data-ttu-id="b4fd2-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b4fd2-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
