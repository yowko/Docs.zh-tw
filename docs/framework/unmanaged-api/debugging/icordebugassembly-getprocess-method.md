---
title: ICorDebugAssembly::GetProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetProcess
helpviewer_keywords:
- ICorDebugAssembly::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: ea52be06-0a16-4f57-afca-4287d72e76c4
topic_type:
- apiref
ms.openlocfilehash: c9cb599dd27a809ed5245c9570cddb8110be8172
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894921"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="9d7d3-102">ICorDebugAssembly::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="9d7d3-102">ICorDebugAssembly::GetProcess Method</span></span>
<span data-ttu-id="9d7d3-103">取得此 ICorDebugAssembly 實例執行所在之進程的介面指標。</span><span class="sxs-lookup"><span data-stu-id="9d7d3-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d7d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="9d7d3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d7d3-105">參數</span><span class="sxs-lookup"><span data-stu-id="9d7d3-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="9d7d3-106">脫銷代表進程之 ICorDebugProcess 介面的指標。</span><span class="sxs-lookup"><span data-stu-id="9d7d3-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d7d3-107">需求</span><span class="sxs-lookup"><span data-stu-id="9d7d3-107">Requirements</span></span>  
 <span data-ttu-id="9d7d3-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9d7d3-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d7d3-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d7d3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d7d3-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d7d3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d7d3-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d7d3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
