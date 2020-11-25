---
title: ICorDebugInternalFrame 介面
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
ms.openlocfilehash: b7e738f06f9a9a06caedec2bdd0de4ab57f6d9b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719719"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="4dc51-102">ICorDebugInternalFrame 介面</span><span class="sxs-lookup"><span data-stu-id="4dc51-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="4dc51-103">代表堆疊上的執行時間內部框架。</span><span class="sxs-lookup"><span data-stu-id="4dc51-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="4dc51-104">此介面是 ICorDebugFrame 介面的子類別。</span><span class="sxs-lookup"><span data-stu-id="4dc51-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4dc51-105">方法</span><span class="sxs-lookup"><span data-stu-id="4dc51-105">Methods</span></span>  
  
|<span data-ttu-id="4dc51-106">方法</span><span class="sxs-lookup"><span data-stu-id="4dc51-106">Method</span></span>|<span data-ttu-id="4dc51-107">描述</span><span class="sxs-lookup"><span data-stu-id="4dc51-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4dc51-108">GetFrameType 方法</span><span class="sxs-lookup"><span data-stu-id="4dc51-108">GetFrameType Method</span></span>](icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="4dc51-109">取得此內部框架的型別。</span><span class="sxs-lookup"><span data-stu-id="4dc51-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4dc51-110">備註</span><span class="sxs-lookup"><span data-stu-id="4dc51-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4dc51-111">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="4dc51-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dc51-112">需求</span><span class="sxs-lookup"><span data-stu-id="4dc51-112">Requirements</span></span>  

 <span data-ttu-id="4dc51-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4dc51-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dc51-114">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4dc51-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4dc51-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4dc51-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dc51-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dc51-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc51-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4dc51-117">See also</span></span>

- [<span data-ttu-id="4dc51-118">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4dc51-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
