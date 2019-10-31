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
ms.openlocfilehash: 49b234b065eb66dc2ec0bc7e991117c5b54a92f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196354"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="46379-102">ICorDebugAssembly::GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="46379-102">ICorDebugAssembly::GetProcess Method</span></span>
<span data-ttu-id="46379-103">取得此 ICorDebugAssembly 實例執行所在之進程的介面指標。</span><span class="sxs-lookup"><span data-stu-id="46379-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46379-104">語法</span><span class="sxs-lookup"><span data-stu-id="46379-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46379-105">參數</span><span class="sxs-lookup"><span data-stu-id="46379-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="46379-106">脫銷代表進程之 ICorDebugProcess 介面的指標。</span><span class="sxs-lookup"><span data-stu-id="46379-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46379-107">需求</span><span class="sxs-lookup"><span data-stu-id="46379-107">Requirements</span></span>  
 <span data-ttu-id="46379-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="46379-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46379-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46379-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46379-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46379-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46379-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46379-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
