---
title: "ICorDebugBreakpoint::IsActive 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBreakpoint.IsActive
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBreakpoint::IsActive
helpviewer_keywords:
- ICorDebugBreakpoint::IsActive method [.NET Framework debugging]
- IsActive method, ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: 06e583d6-d88a-4ff5-bb95-5c48618a461c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ebb5c448da6a2ff47bc7c2451c4270677eeb93a8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugbreakpointisactive-method"></a><span data-ttu-id="93f74-102">ICorDebugBreakpoint::IsActive 方法</span><span class="sxs-lookup"><span data-stu-id="93f74-102">ICorDebugBreakpoint::IsActive Method</span></span>
<span data-ttu-id="93f74-103">取得值，指出是否此`ICorDebugBreakpoint`為作用中。</span><span class="sxs-lookup"><span data-stu-id="93f74-103">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93f74-104">語法</span><span class="sxs-lookup"><span data-stu-id="93f74-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL *pbActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93f74-105">參數</span><span class="sxs-lookup"><span data-stu-id="93f74-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="93f74-106">[out]`true`此中斷點為作用中; 否則如果`false`。</span><span class="sxs-lookup"><span data-stu-id="93f74-106">[out] `true` if this breakpoint is active; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93f74-107">需求</span><span class="sxs-lookup"><span data-stu-id="93f74-107">Requirements</span></span>  
 <span data-ttu-id="93f74-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93f74-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93f74-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93f74-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93f74-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93f74-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93f74-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93f74-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
