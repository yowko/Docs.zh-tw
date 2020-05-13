---
title: ICorDebugStepper2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2
helpviewer_keywords:
- ICorDebugStepper2 interface [.NET Framework debugging]
ms.assetid: 7a191c2a-95ea-4d47-83b0-44de2b632d63
topic_type:
- apiref
ms.openlocfilehash: ef7aa164c43751fa39e49d0ab6486a9f29e23c20
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379482"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="6f2c2-102">ICorDebugStepper2 介面</span><span class="sxs-lookup"><span data-stu-id="6f2c2-102">ICorDebugStepper2 Interface</span></span>
<span data-ttu-id="6f2c2-103">僅提供 my code （JMC）偵錯工具的支援。</span><span class="sxs-lookup"><span data-stu-id="6f2c2-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f2c2-104">方法</span><span class="sxs-lookup"><span data-stu-id="6f2c2-104">Methods</span></span>  
  
|<span data-ttu-id="6f2c2-105">方法</span><span class="sxs-lookup"><span data-stu-id="6f2c2-105">Method</span></span>|<span data-ttu-id="6f2c2-106">描述</span><span class="sxs-lookup"><span data-stu-id="6f2c2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f2c2-107">SetJMC 方法</span><span class="sxs-lookup"><span data-stu-id="6f2c2-107">SetJMC Method</span></span>](icordebugstepper2-setjmc-method.md)|<span data-ttu-id="6f2c2-108">設定值，指定此 ICorDebugStepper 步驟是否只透過應用程式開發人員所撰寫的程式碼進行。</span><span class="sxs-lookup"><span data-stu-id="6f2c2-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f2c2-109">備註</span><span class="sxs-lookup"><span data-stu-id="6f2c2-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f2c2-110">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="6f2c2-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f2c2-111">需求</span><span class="sxs-lookup"><span data-stu-id="6f2c2-111">Requirements</span></span>  
 <span data-ttu-id="6f2c2-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f2c2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f2c2-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f2c2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f2c2-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f2c2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f2c2-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f2c2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f2c2-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="6f2c2-116">See also</span></span>

- [<span data-ttu-id="6f2c2-117">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6f2c2-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
