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
ms.openlocfilehash: 3ada9e19bb1a92b3bd7e41340b99bf81b651dd37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725010"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="1ab97-102">ICorDebugILFrame2 介面</span><span class="sxs-lookup"><span data-stu-id="1ab97-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="1ab97-103">ICorDebugILFrame 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="1ab97-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1ab97-104">方法</span><span class="sxs-lookup"><span data-stu-id="1ab97-104">Methods</span></span>  
  
|<span data-ttu-id="1ab97-105">方法</span><span class="sxs-lookup"><span data-stu-id="1ab97-105">Method</span></span>|<span data-ttu-id="1ab97-106">描述</span><span class="sxs-lookup"><span data-stu-id="1ab97-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1ab97-107">EnumerateTypeParameters 方法</span><span class="sxs-lookup"><span data-stu-id="1ab97-107">EnumerateTypeParameters Method</span></span>](icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="1ab97-108">取得 ICorDebugTypeEnum 物件，其中包含 <xref:System.Type> 此框架中的參數。</span><span class="sxs-lookup"><span data-stu-id="1ab97-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="1ab97-109">RemapFunction 方法</span><span class="sxs-lookup"><span data-stu-id="1ab97-109">RemapFunction Method</span></span>](icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="1ab97-110">藉由指定新的 MSIL 位移，重新對應已編輯的函式。</span><span class="sxs-lookup"><span data-stu-id="1ab97-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ab97-111">備註</span><span class="sxs-lookup"><span data-stu-id="1ab97-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ab97-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="1ab97-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ab97-113">需求</span><span class="sxs-lookup"><span data-stu-id="1ab97-113">Requirements</span></span>  

 <span data-ttu-id="1ab97-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ab97-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ab97-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ab97-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ab97-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ab97-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ab97-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ab97-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ab97-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ab97-118">See also</span></span>

- [<span data-ttu-id="1ab97-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1ab97-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
