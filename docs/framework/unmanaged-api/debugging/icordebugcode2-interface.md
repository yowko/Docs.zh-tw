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
ms.openlocfilehash: 1e5b92d99d8ae52c88f1517f9c3d7db8e70598ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720798"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="693df-102">ICorDebugCode2 介面</span><span class="sxs-lookup"><span data-stu-id="693df-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="693df-103">提供擴充 "ICorDebugCode" 功能的方法。</span><span class="sxs-lookup"><span data-stu-id="693df-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="693df-104">方法</span><span class="sxs-lookup"><span data-stu-id="693df-104">Methods</span></span>  
  
|<span data-ttu-id="693df-105">方法</span><span class="sxs-lookup"><span data-stu-id="693df-105">Method</span></span>|<span data-ttu-id="693df-106">描述</span><span class="sxs-lookup"><span data-stu-id="693df-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="693df-107">GetCodeChunks 方法</span><span class="sxs-lookup"><span data-stu-id="693df-107">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="693df-108">取得此程式碼物件所組成的程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="693df-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="693df-109">GetCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="693df-109">GetCompilerFlags Method</span></span>](icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="693df-110">取得旗標，指定此程式碼物件是使用原生映射產生器 ( # A0) 編譯或產生的即時 (JIT) 。</span><span class="sxs-lookup"><span data-stu-id="693df-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="693df-111">備註</span><span class="sxs-lookup"><span data-stu-id="693df-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="693df-112">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="693df-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="693df-113">需求</span><span class="sxs-lookup"><span data-stu-id="693df-113">Requirements</span></span>  

 <span data-ttu-id="693df-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="693df-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="693df-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="693df-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="693df-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="693df-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="693df-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="693df-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="693df-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="693df-118">See also</span></span>

- [<span data-ttu-id="693df-119">ICorDebugCode3 介面</span><span class="sxs-lookup"><span data-stu-id="693df-119">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="693df-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="693df-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
