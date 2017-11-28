---
title: "ICorDebugModule2::ResolveAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule2.ResolveAssembly
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 37ddb0e8871d9ec5f8eed4f00d81098feafb01de
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="c2531-102">ICorDebugModule2::ResolveAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="c2531-102">ICorDebugModule2::ResolveAssembly Method</span></span>
<span data-ttu-id="c2531-103">解析指定的中繼資料語彙基元所參考的組件。</span><span class="sxs-lookup"><span data-stu-id="c2531-103">Resolves the assembly referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2531-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2531-104">Syntax</span></span>  
  
```  
HRESULT ResolveAssembly (  
    [in]  mdToken             tkAssemblyRef,  
    [out] ICorDebugAssembly   **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2531-105">參數</span><span class="sxs-lookup"><span data-stu-id="c2531-105">Parameters</span></span>  
 `tkAsemblyRef`  
 <span data-ttu-id="c2531-106">[in]`mdToken`參考組件的值。</span><span class="sxs-lookup"><span data-stu-id="c2531-106">[in] An `mdToken` value that references the assembly.</span></span>  
  
 `ppAssembly`  
 <span data-ttu-id="c2531-107">[out]ICorDebugAssembly 物件，表示組件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="c2531-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2531-108">備註</span><span class="sxs-lookup"><span data-stu-id="c2531-108">Remarks</span></span>  
 <span data-ttu-id="c2531-109">如果組件尚未載入時`ResolveAssembly`呼叫時，HRESULT 傳回 CORDBG_E_CANNOT_RESOLVE_ASSEMBLY 的值。</span><span class="sxs-lookup"><span data-stu-id="c2531-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2531-110">需求</span><span class="sxs-lookup"><span data-stu-id="c2531-110">Requirements</span></span>  
 <span data-ttu-id="c2531-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c2531-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2531-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2531-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2531-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2531-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2531-114">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2531-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
