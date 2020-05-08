---
title: ICorDebugChainEnum 介面
ms.date: 03/30/2017
api_name:
- ICorDebugChainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum
helpviewer_keywords:
- ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6639335c-48e1-4e74-a4f3-70a6a0f54af1
topic_type:
- apiref
ms.openlocfilehash: 4556ebbd05e0660da14fb59d806c8feb0b45b9bb
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894222"
---
# <a name="icordebugchainenum-interface"></a><span data-ttu-id="2203f-102">ICorDebugChainEnum 介面</span><span class="sxs-lookup"><span data-stu-id="2203f-102">ICorDebugChainEnum Interface</span></span>

<span data-ttu-id="2203f-103">會執行 ICorDebugEnum 方法，並列舉 ICorDebugChain 陣列。</span><span class="sxs-lookup"><span data-stu-id="2203f-103">Implements ICorDebugEnum methods, and enumerates ICorDebugChain arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2203f-104">方法</span><span class="sxs-lookup"><span data-stu-id="2203f-104">Methods</span></span>  
  
|<span data-ttu-id="2203f-105">方法</span><span class="sxs-lookup"><span data-stu-id="2203f-105">Method</span></span>|<span data-ttu-id="2203f-106">描述</span><span class="sxs-lookup"><span data-stu-id="2203f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2203f-107">下一個方法</span><span class="sxs-lookup"><span data-stu-id="2203f-107">Next Method</span></span>](icordebugchainenum-next-method.md)|<span data-ttu-id="2203f-108">從列舉中取得指定`ICorDebugChain`的實例數目，從目前位置開始。</span><span class="sxs-lookup"><span data-stu-id="2203f-108">Gets the specified number of `ICorDebugChain` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2203f-109">備註</span><span class="sxs-lookup"><span data-stu-id="2203f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2203f-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="2203f-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2203f-111">需求</span><span class="sxs-lookup"><span data-stu-id="2203f-111">Requirements</span></span>  
 <span data-ttu-id="2203f-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2203f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2203f-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2203f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2203f-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2203f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2203f-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2203f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2203f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2203f-116">See also</span></span>

- [<span data-ttu-id="2203f-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="2203f-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
