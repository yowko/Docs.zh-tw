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
ms.openlocfilehash: 9f521eb942f37b8cf1d00bcc672071a69692b876
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396640"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="8f83f-102">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="8f83f-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="8f83f-103">擴充 "ICorDebugValue" 和 "ICorDebugValue2" 介面，以提供大於 2 GB 的陣列支援。</span><span class="sxs-lookup"><span data-stu-id="8f83f-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8f83f-104">方法</span><span class="sxs-lookup"><span data-stu-id="8f83f-104">Methods</span></span>  
  
|<span data-ttu-id="8f83f-105">方法</span><span class="sxs-lookup"><span data-stu-id="8f83f-105">Method</span></span>|<span data-ttu-id="8f83f-106">描述</span><span class="sxs-lookup"><span data-stu-id="8f83f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8f83f-107">GetSize64 方法</span><span class="sxs-lookup"><span data-stu-id="8f83f-107">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)|<span data-ttu-id="8f83f-108">取得這個物件的大小（以位元組為單位） `ICorDebugValue3` 。</span><span class="sxs-lookup"><span data-stu-id="8f83f-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f83f-109">備註</span><span class="sxs-lookup"><span data-stu-id="8f83f-109">Remarks</span></span>  
 <span data-ttu-id="8f83f-110">[ICorDebugValue：： GetSize](icordebugvalue3-getsize64-method.md)方法會傳回範圍從0到2147483647個位元組的物件大小。</span><span class="sxs-lookup"><span data-stu-id="8f83f-110">The [ICorDebugValue::GetSize](icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="8f83f-111">在 .NET Framework 4.5 中，陣列的大小可以超過 2 GB。</span><span class="sxs-lookup"><span data-stu-id="8f83f-111">In the .NET Framework 4.5, the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="8f83f-112">`ICorDebugValue3`介面可讓您判斷這些陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="8f83f-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f83f-113">需求</span><span class="sxs-lookup"><span data-stu-id="8f83f-113">Requirements</span></span>  
 <span data-ttu-id="8f83f-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f83f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f83f-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f83f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f83f-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f83f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f83f-117">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f83f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f83f-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="8f83f-118">See also</span></span>

- [<span data-ttu-id="8f83f-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8f83f-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8f83f-120">偵錯</span><span class="sxs-lookup"><span data-stu-id="8f83f-120">Debugging</span></span>](index.md)
