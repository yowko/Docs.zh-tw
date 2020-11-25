---
title: ICorDebugValue2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2
helpviewer_keywords:
- ICorDebugValue2 interface [.NET Framework debugging]
ms.assetid: 3ff2ad2a-da5a-461b-8627-1a8eba49df9c
topic_type:
- apiref
ms.openlocfilehash: 7aca5fcb5a55331756b4f98c08eb46fc4db1e289
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720330"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="dc1fb-102">ICorDebugValue2 介面</span><span class="sxs-lookup"><span data-stu-id="dc1fb-102">ICorDebugValue2 Interface</span></span>

<span data-ttu-id="dc1fb-103">擴充 "ICorDebugValue" 介面，以提供 "ICorDebugType" 物件的支援。</span><span class="sxs-lookup"><span data-stu-id="dc1fb-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dc1fb-104">方法</span><span class="sxs-lookup"><span data-stu-id="dc1fb-104">Methods</span></span>  
  
|<span data-ttu-id="dc1fb-105">方法</span><span class="sxs-lookup"><span data-stu-id="dc1fb-105">Method</span></span>|<span data-ttu-id="dc1fb-106">描述</span><span class="sxs-lookup"><span data-stu-id="dc1fb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dc1fb-107">GetExactType 方法</span><span class="sxs-lookup"><span data-stu-id="dc1fb-107">GetExactType Method</span></span>](icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="dc1fb-108">取得物件的介面指標 `ICorDebugType` ，該物件代表 <xref:System.Type> 此值的。</span><span class="sxs-lookup"><span data-stu-id="dc1fb-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc1fb-109">備註</span><span class="sxs-lookup"><span data-stu-id="dc1fb-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc1fb-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="dc1fb-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc1fb-111">需求</span><span class="sxs-lookup"><span data-stu-id="dc1fb-111">Requirements</span></span>  

 <span data-ttu-id="dc1fb-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc1fb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc1fb-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc1fb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc1fb-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc1fb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc1fb-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc1fb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc1fb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc1fb-116">See also</span></span>

- [<span data-ttu-id="dc1fb-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="dc1fb-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

- [<span data-ttu-id="dc1fb-118">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="dc1fb-118">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
