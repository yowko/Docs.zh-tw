---
title: ICorDebugEval::NewString 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db609bdee7975b6c067271f99529e2cf2240f720
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480178"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="42385-102">ICorDebugEval::NewString 方法</span><span class="sxs-lookup"><span data-stu-id="42385-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="42385-103">會配置新的字串執行個體具有指定的內容。</span><span class="sxs-lookup"><span data-stu-id="42385-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42385-104">語法</span><span class="sxs-lookup"><span data-stu-id="42385-104">Syntax</span></span>  
  
```  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42385-105">參數</span><span class="sxs-lookup"><span data-stu-id="42385-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="42385-106">[in]字串內容的指標。</span><span class="sxs-lookup"><span data-stu-id="42385-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42385-107">備註</span><span class="sxs-lookup"><span data-stu-id="42385-107">Remarks</span></span>  
 <span data-ttu-id="42385-108">字串一律會建立目前執行所在之執行緒的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="42385-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42385-109">需求</span><span class="sxs-lookup"><span data-stu-id="42385-109">Requirements</span></span>  
 <span data-ttu-id="42385-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42385-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42385-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42385-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42385-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42385-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42385-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42385-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
