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
ms.openlocfilehash: 34e1dd6adaa9906babca80f4cc610c157bd00534
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648241"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="a96c9-102">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="a96c9-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="a96c9-103">擴充的 」 ICorDebugValue"和"ICorDebugValue2 」 介面以支援大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="a96c9-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a96c9-104">方法</span><span class="sxs-lookup"><span data-stu-id="a96c9-104">Methods</span></span>  
  
|<span data-ttu-id="a96c9-105">方法</span><span class="sxs-lookup"><span data-stu-id="a96c9-105">Method</span></span>|<span data-ttu-id="a96c9-106">描述</span><span class="sxs-lookup"><span data-stu-id="a96c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a96c9-107">GetSize64 方法</span><span class="sxs-lookup"><span data-stu-id="a96c9-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="a96c9-108">取得大小，以位元組為單位，這個`ICorDebugValue3`物件。</span><span class="sxs-lookup"><span data-stu-id="a96c9-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a96c9-109">備註</span><span class="sxs-lookup"><span data-stu-id="a96c9-109">Remarks</span></span>  
 <span data-ttu-id="a96c9-110">[Icordebugvalue:: Getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)方法會傳回物件大小，範圍從 0 到 2,147,483,647 個位元組。</span><span class="sxs-lookup"><span data-stu-id="a96c9-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="a96c9-111">在  [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]，陣列的大小可以超過 2 GB。</span><span class="sxs-lookup"><span data-stu-id="a96c9-111">In the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="a96c9-112">`ICorDebugValue3`介面可讓您判斷這些陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="a96c9-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a96c9-113">需求</span><span class="sxs-lookup"><span data-stu-id="a96c9-113">Requirements</span></span>  
 <span data-ttu-id="a96c9-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a96c9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a96c9-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a96c9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a96c9-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a96c9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a96c9-117">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a96c9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a96c9-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a96c9-118">See also</span></span>


- [<span data-ttu-id="a96c9-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a96c9-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a96c9-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="a96c9-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
