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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3fb1bf3f61c78f4eb157b93363b1c06b25bee04
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119895"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="44284-102">ICorDebugModule2 介面</span><span class="sxs-lookup"><span data-stu-id="44284-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="44284-103">可做為 ICorDebugModule 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="44284-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="44284-104">方法</span><span class="sxs-lookup"><span data-stu-id="44284-104">Methods</span></span>  
  
|<span data-ttu-id="44284-105">方法</span><span class="sxs-lookup"><span data-stu-id="44284-105">Method</span></span>|<span data-ttu-id="44284-106">描述</span><span class="sxs-lookup"><span data-stu-id="44284-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="44284-107">ApplyChanges 方法</span><span class="sxs-lookup"><span data-stu-id="44284-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="44284-108">適用於執行中處理序在中繼資料中的變更和 Microsoft intermediate language (MSIL) 程式碼中的變更。</span><span class="sxs-lookup"><span data-stu-id="44284-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="44284-109">GetJITCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="44284-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="44284-110">取得旗標，控制在 just-in-time (JIT) 編譯這個`ICorDebugModule2`。</span><span class="sxs-lookup"><span data-stu-id="44284-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="44284-111">ResolveAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="44284-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="44284-112">解析指定的中繼資料語彙基元所參考的組件。</span><span class="sxs-lookup"><span data-stu-id="44284-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="44284-113">SetJITCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="44284-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="44284-114">設定控制 JIT 編譯，這個旗標`ICorDebugModule2`。</span><span class="sxs-lookup"><span data-stu-id="44284-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="44284-115">SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="44284-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="44284-116">在此設定的所有類別的所有方法的 Just My Code (JMC) 狀態`ICorDebugModule2`指定的值，不屬於`pTokens`陣列，它會設定為相反值。</span><span class="sxs-lookup"><span data-stu-id="44284-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44284-117">備註</span><span class="sxs-lookup"><span data-stu-id="44284-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44284-118">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="44284-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44284-119">需求</span><span class="sxs-lookup"><span data-stu-id="44284-119">Requirements</span></span>  
 <span data-ttu-id="44284-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44284-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44284-121">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44284-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44284-122">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44284-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44284-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44284-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44284-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44284-124">See also</span></span>

- [<span data-ttu-id="44284-125">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="44284-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
