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
ms.openlocfilehash: e5eb86bb80aea5fc65a7362467b78b16a59794d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412226"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="358c9-102">ICorDebugEval::NewString 方法</span><span class="sxs-lookup"><span data-stu-id="358c9-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="358c9-103">會配置新的字串執行個體具有指定的內容。</span><span class="sxs-lookup"><span data-stu-id="358c9-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="358c9-104">語法</span><span class="sxs-lookup"><span data-stu-id="358c9-104">Syntax</span></span>  
  
```  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="358c9-105">參數</span><span class="sxs-lookup"><span data-stu-id="358c9-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="358c9-106">[in]字串內容的指標。</span><span class="sxs-lookup"><span data-stu-id="358c9-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="358c9-107">備註</span><span class="sxs-lookup"><span data-stu-id="358c9-107">Remarks</span></span>  
 <span data-ttu-id="358c9-108">字串，永遠會建立所在的執行緒目前正在執行的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="358c9-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="358c9-109">需求</span><span class="sxs-lookup"><span data-stu-id="358c9-109">Requirements</span></span>  
 <span data-ttu-id="358c9-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="358c9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="358c9-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="358c9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="358c9-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="358c9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="358c9-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="358c9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
