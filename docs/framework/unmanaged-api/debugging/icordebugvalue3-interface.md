---
title: ICorDebugValue3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4bf3605331e6900fd890e49bb3f71f4ca4409c7
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377588"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="e1e8a-102">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="e1e8a-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="e1e8a-103">擴充的 」 ICorDebugValue"和"ICorDebugValue2 」 介面以支援大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="e1e8a-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e1e8a-104">方法</span><span class="sxs-lookup"><span data-stu-id="e1e8a-104">Methods</span></span>  
  
|<span data-ttu-id="e1e8a-105">方法</span><span class="sxs-lookup"><span data-stu-id="e1e8a-105">Method</span></span>|<span data-ttu-id="e1e8a-106">描述</span><span class="sxs-lookup"><span data-stu-id="e1e8a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e1e8a-107">GetSize64 方法</span><span class="sxs-lookup"><span data-stu-id="e1e8a-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="e1e8a-108">取得大小，以位元組為單位，這個`ICorDebugValue3`物件。</span><span class="sxs-lookup"><span data-stu-id="e1e8a-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1e8a-109">備註</span><span class="sxs-lookup"><span data-stu-id="e1e8a-109">Remarks</span></span>  
 <span data-ttu-id="e1e8a-110">[Icordebugvalue:: Getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)方法會傳回物件大小，範圍從 0 到 2,147,483,647 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e1e8a-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="e1e8a-111">在.NET Framework 4.5 中，陣列的大小可以超過 2 GB。</span><span class="sxs-lookup"><span data-stu-id="e1e8a-111">In the .NET Framework 4.5, the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="e1e8a-112">`ICorDebugValue3`介面可讓您判斷這些陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="e1e8a-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1e8a-113">需求</span><span class="sxs-lookup"><span data-stu-id="e1e8a-113">Requirements</span></span>  
 <span data-ttu-id="e1e8a-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1e8a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1e8a-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1e8a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1e8a-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1e8a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1e8a-117">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1e8a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1e8a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1e8a-118">See also</span></span>

- [<span data-ttu-id="e1e8a-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e1e8a-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e1e8a-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="e1e8a-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
