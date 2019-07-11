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
ms.openlocfilehash: 50a18f435063b74b837dbfe9e4f1d986bb735039
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753350"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="e25cb-102">ICorDebugEval::NewString 方法</span><span class="sxs-lookup"><span data-stu-id="e25cb-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="e25cb-103">會配置新的字串執行個體具有指定的內容。</span><span class="sxs-lookup"><span data-stu-id="e25cb-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e25cb-104">語法</span><span class="sxs-lookup"><span data-stu-id="e25cb-104">Syntax</span></span>  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e25cb-105">參數</span><span class="sxs-lookup"><span data-stu-id="e25cb-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="e25cb-106">[in]字串內容的指標。</span><span class="sxs-lookup"><span data-stu-id="e25cb-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e25cb-107">備註</span><span class="sxs-lookup"><span data-stu-id="e25cb-107">Remarks</span></span>  
 <span data-ttu-id="e25cb-108">字串一律會建立目前執行所在之執行緒的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="e25cb-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e25cb-109">需求</span><span class="sxs-lookup"><span data-stu-id="e25cb-109">Requirements</span></span>  
 <span data-ttu-id="e25cb-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e25cb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e25cb-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e25cb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e25cb-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e25cb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e25cb-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e25cb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
