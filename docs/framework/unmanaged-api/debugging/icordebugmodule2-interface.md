---
title: ICorDebugModule2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
ms.openlocfilehash: 2b8e6048dd6b8df71ac3dddcc4397f6d512127c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695877"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="7302b-102">ICorDebugModule2 介面</span><span class="sxs-lookup"><span data-stu-id="7302b-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="7302b-103">作為 ICorDebugModule 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="7302b-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7302b-104">方法</span><span class="sxs-lookup"><span data-stu-id="7302b-104">Methods</span></span>  
  
|<span data-ttu-id="7302b-105">方法</span><span class="sxs-lookup"><span data-stu-id="7302b-105">Method</span></span>|<span data-ttu-id="7302b-106">描述</span><span class="sxs-lookup"><span data-stu-id="7302b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7302b-107">ApplyChanges 方法</span><span class="sxs-lookup"><span data-stu-id="7302b-107">ApplyChanges Method</span></span>](icordebugmodule2-applychanges-method.md)|<span data-ttu-id="7302b-108">將中繼資料中的變更，以及 Microsoft 中繼語言 (MSIL) 程式碼中的變更套用至執行中的進程。</span><span class="sxs-lookup"><span data-stu-id="7302b-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="7302b-109">GetJITCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="7302b-109">GetJITCompilerFlags Method</span></span>](icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="7302b-110">取得旗標，這些旗標會控制這個的即時 (JIT) 編譯 `ICorDebugModule2` 。</span><span class="sxs-lookup"><span data-stu-id="7302b-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="7302b-111">ResolveAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="7302b-111">ResolveAssembly Method</span></span>](icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="7302b-112">解析指定的元資料標記所參考的元件。</span><span class="sxs-lookup"><span data-stu-id="7302b-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="7302b-113">SetJITCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="7302b-113">SetJITCompilerFlags Method</span></span>](icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="7302b-114">設定用來控制這個之 JIT 編譯的旗標 `ICorDebugModule2` 。</span><span class="sxs-lookup"><span data-stu-id="7302b-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="7302b-115">SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="7302b-115">SetJMCStatus Method</span></span>](icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="7302b-116">將此 Just My Code (JMC 的所有方法) 狀態設定 `ICorDebugModule2` 為指定的值，但陣列中的這些方法 `pTokens` 會將其設定為相反值。</span><span class="sxs-lookup"><span data-stu-id="7302b-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7302b-117">備註</span><span class="sxs-lookup"><span data-stu-id="7302b-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7302b-118">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="7302b-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7302b-119">需求</span><span class="sxs-lookup"><span data-stu-id="7302b-119">Requirements</span></span>  

 <span data-ttu-id="7302b-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7302b-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7302b-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7302b-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7302b-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7302b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7302b-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7302b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7302b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7302b-124">See also</span></span>

- [<span data-ttu-id="7302b-125">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7302b-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
