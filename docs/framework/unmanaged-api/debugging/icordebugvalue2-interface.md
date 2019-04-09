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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6718bbfdb1825b9f01698d76deec3fab16cb2ac6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091599"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="941e9-102">ICorDebugValue2 介面</span><span class="sxs-lookup"><span data-stu-id="941e9-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="941e9-103">延伸以支援 「 ICorDebugType 「 物件 」 ICorDebugValue"介面。</span><span class="sxs-lookup"><span data-stu-id="941e9-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="941e9-104">方法</span><span class="sxs-lookup"><span data-stu-id="941e9-104">Methods</span></span>  
  
|<span data-ttu-id="941e9-105">方法</span><span class="sxs-lookup"><span data-stu-id="941e9-105">Method</span></span>|<span data-ttu-id="941e9-106">描述</span><span class="sxs-lookup"><span data-stu-id="941e9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="941e9-107">GetExactType 方法</span><span class="sxs-lookup"><span data-stu-id="941e9-107">GetExactType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="941e9-108">取得的介面指標`ICorDebugType`物件，表示<xref:System.Type>此值。</span><span class="sxs-lookup"><span data-stu-id="941e9-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="941e9-109">備註</span><span class="sxs-lookup"><span data-stu-id="941e9-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="941e9-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="941e9-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="941e9-111">需求</span><span class="sxs-lookup"><span data-stu-id="941e9-111">Requirements</span></span>  
 <span data-ttu-id="941e9-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="941e9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="941e9-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="941e9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="941e9-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="941e9-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="941e9-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="941e9-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="941e9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="941e9-116">See also</span></span>

- [<span data-ttu-id="941e9-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="941e9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

- [<span data-ttu-id="941e9-118">ICorDebugValue3 介面</span><span class="sxs-lookup"><span data-stu-id="941e9-118">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
