---
title: ICorDebugModule2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2
helpviewer_keywords: ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 97259783d34babe3f0f229f5d62b3e945c0ac624
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2-interface1"></a><span data-ttu-id="b331f-102">ICorDebugModule2 Interface1</span><span class="sxs-lookup"><span data-stu-id="b331f-102">ICorDebugModule2 Interface1</span></span>
<span data-ttu-id="b331f-103">可做為 ICorDebugModule 介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="b331f-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b331f-104">方法</span><span class="sxs-lookup"><span data-stu-id="b331f-104">Methods</span></span>  
  
|<span data-ttu-id="b331f-105">方法</span><span class="sxs-lookup"><span data-stu-id="b331f-105">Method</span></span>|<span data-ttu-id="b331f-106">說明</span><span class="sxs-lookup"><span data-stu-id="b331f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b331f-107">ApplyChanges 方法</span><span class="sxs-lookup"><span data-stu-id="b331f-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="b331f-108">適用於執行的處理序的中繼資料中的變更和 Microsoft intermediate language (MSIL) 程式碼中的變更。</span><span class="sxs-lookup"><span data-stu-id="b331f-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="b331f-109">GetJITCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="b331f-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="b331f-110">取得旗標，控制在 just-in-time (JIT) 編譯這個`ICorDebugModule2`。</span><span class="sxs-lookup"><span data-stu-id="b331f-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="b331f-111">ResolveAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="b331f-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="b331f-112">解析指定的中繼資料語彙基元所參考的組件。</span><span class="sxs-lookup"><span data-stu-id="b331f-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="b331f-113">SetJITCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="b331f-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="b331f-114">設定旗標，以控制 JIT 編譯這個`ICorDebugModule2`。</span><span class="sxs-lookup"><span data-stu-id="b331f-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="b331f-115">SetJMCStatus 方法</span><span class="sxs-lookup"><span data-stu-id="b331f-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="b331f-116">在此設定的所有類別的所有方法的 Just My Code (JMC) 狀態`ICorDebugModule2`和指定的值以外的`pTokens`陣列，它會設定為相反側的值。</span><span class="sxs-lookup"><span data-stu-id="b331f-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b331f-117">備註</span><span class="sxs-lookup"><span data-stu-id="b331f-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b331f-118">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b331f-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b331f-119">需求</span><span class="sxs-lookup"><span data-stu-id="b331f-119">Requirements</span></span>  
 <span data-ttu-id="b331f-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b331f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b331f-121">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b331f-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b331f-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b331f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b331f-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b331f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b331f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b331f-124">See Also</span></span>  
 [<span data-ttu-id="b331f-125">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b331f-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
