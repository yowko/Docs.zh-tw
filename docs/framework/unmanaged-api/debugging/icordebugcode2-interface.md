---
title: ICorDebugCode2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
ms.openlocfilehash: a9ce778cfa1aed4dcf6117c4fe2eca23ccda37a3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777955"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="8f8a0-102">ICorDebugCode2 介面</span><span class="sxs-lookup"><span data-stu-id="8f8a0-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="8f8a0-103">提供擴充 "ICorDebugCode" 功能的方法。</span><span class="sxs-lookup"><span data-stu-id="8f8a0-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8f8a0-104">方法</span><span class="sxs-lookup"><span data-stu-id="8f8a0-104">Methods</span></span>  
  
|<span data-ttu-id="8f8a0-105">方法</span><span class="sxs-lookup"><span data-stu-id="8f8a0-105">Method</span></span>|<span data-ttu-id="8f8a0-106">描述</span><span class="sxs-lookup"><span data-stu-id="8f8a0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8f8a0-107">GetCodeChunks 方法</span><span class="sxs-lookup"><span data-stu-id="8f8a0-107">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="8f8a0-108">取得此程式碼物件所組成的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="8f8a0-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="8f8a0-109">GetCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="8f8a0-109">GetCompilerFlags Method</span></span>](icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="8f8a0-110">取得指定條件的旗標，此程式碼物件是使用原生映射產生器（Ngen.exe）編譯或產生的即時（JIT）。</span><span class="sxs-lookup"><span data-stu-id="8f8a0-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f8a0-111">備註</span><span class="sxs-lookup"><span data-stu-id="8f8a0-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f8a0-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="8f8a0-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f8a0-113">需求</span><span class="sxs-lookup"><span data-stu-id="8f8a0-113">Requirements</span></span>  
 <span data-ttu-id="8f8a0-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f8a0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f8a0-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f8a0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f8a0-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f8a0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f8a0-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f8a0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f8a0-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="8f8a0-118">See also</span></span>

- [<span data-ttu-id="8f8a0-119">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="8f8a0-119">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="8f8a0-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8f8a0-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
