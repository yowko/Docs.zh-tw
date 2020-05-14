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
ms.openlocfilehash: d036ddf353aa3a622ade05e1e2daa7f170d28f63
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396782"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="6c53d-102">ICorDebugValue2 介面</span><span class="sxs-lookup"><span data-stu-id="6c53d-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="6c53d-103">擴充 "ICorDebugValue" 介面，以提供對 "ICorDebugType" 物件的支援。</span><span class="sxs-lookup"><span data-stu-id="6c53d-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c53d-104">方法</span><span class="sxs-lookup"><span data-stu-id="6c53d-104">Methods</span></span>  
  
|<span data-ttu-id="6c53d-105">方法</span><span class="sxs-lookup"><span data-stu-id="6c53d-105">Method</span></span>|<span data-ttu-id="6c53d-106">描述</span><span class="sxs-lookup"><span data-stu-id="6c53d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c53d-107">GetExactType 方法</span><span class="sxs-lookup"><span data-stu-id="6c53d-107">GetExactType Method</span></span>](icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="6c53d-108">取得 `ICorDebugType` 物件的介面指標，表示 <xref:System.Type> 這個值的。</span><span class="sxs-lookup"><span data-stu-id="6c53d-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c53d-109">備註</span><span class="sxs-lookup"><span data-stu-id="6c53d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6c53d-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="6c53d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c53d-111">需求</span><span class="sxs-lookup"><span data-stu-id="6c53d-111">Requirements</span></span>  
 <span data-ttu-id="6c53d-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c53d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c53d-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c53d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c53d-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c53d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c53d-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c53d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c53d-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="6c53d-116">See also</span></span>

- [<span data-ttu-id="6c53d-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6c53d-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

- [<span data-ttu-id="6c53d-118">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="6c53d-118">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
