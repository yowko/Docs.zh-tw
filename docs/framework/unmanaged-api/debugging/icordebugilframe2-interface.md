---
title: ICorDebugILFrame2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e82238fbd617d56feb5c71c6161b6fd206b8b5b6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970853"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="b79e9-102">ICorDebugILFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="b79e9-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="b79e9-103">ICorDebugILFrame 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="b79e9-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b79e9-104">方法</span><span class="sxs-lookup"><span data-stu-id="b79e9-104">Methods</span></span>  
  
|<span data-ttu-id="b79e9-105">方法</span><span class="sxs-lookup"><span data-stu-id="b79e9-105">Method</span></span>|<span data-ttu-id="b79e9-106">描述</span><span class="sxs-lookup"><span data-stu-id="b79e9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b79e9-107">EnumerateTypeParameters 方法</span><span class="sxs-lookup"><span data-stu-id="b79e9-107">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="b79e9-108">取得包含 ICorDebugTypeEnum 物件<xref:System.Type>這個框架中的參數。</span><span class="sxs-lookup"><span data-stu-id="b79e9-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="b79e9-109">RemapFunction 方法</span><span class="sxs-lookup"><span data-stu-id="b79e9-109">RemapFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="b79e9-110">將編輯過的函式中指定新的 MSIL 位移重新對應。</span><span class="sxs-lookup"><span data-stu-id="b79e9-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b79e9-111">備註</span><span class="sxs-lookup"><span data-stu-id="b79e9-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b79e9-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b79e9-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b79e9-113">需求</span><span class="sxs-lookup"><span data-stu-id="b79e9-113">Requirements</span></span>  
 <span data-ttu-id="b79e9-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b79e9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b79e9-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b79e9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b79e9-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b79e9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b79e9-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b79e9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b79e9-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b79e9-118">See also</span></span>
- [<span data-ttu-id="b79e9-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b79e9-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
