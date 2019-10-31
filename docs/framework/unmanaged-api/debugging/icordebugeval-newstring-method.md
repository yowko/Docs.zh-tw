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
ms.openlocfilehash: 8a5d421bf0eb8ec5a34fe21d6efc79bbe56c294c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137648"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="9bf03-102">ICorDebugEval::NewString 方法</span><span class="sxs-lookup"><span data-stu-id="9bf03-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="9bf03-103">使用指定的內容，配置新的字串實例。</span><span class="sxs-lookup"><span data-stu-id="9bf03-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bf03-104">語法</span><span class="sxs-lookup"><span data-stu-id="9bf03-104">Syntax</span></span>  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9bf03-105">參數</span><span class="sxs-lookup"><span data-stu-id="9bf03-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="9bf03-106">在字串內容的指標。</span><span class="sxs-lookup"><span data-stu-id="9bf03-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bf03-107">備註</span><span class="sxs-lookup"><span data-stu-id="9bf03-107">Remarks</span></span>  
 <span data-ttu-id="9bf03-108">此字串一律會線上程目前執行所在的應用程式域中建立。</span><span class="sxs-lookup"><span data-stu-id="9bf03-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bf03-109">需求</span><span class="sxs-lookup"><span data-stu-id="9bf03-109">Requirements</span></span>  
 <span data-ttu-id="9bf03-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9bf03-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bf03-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9bf03-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bf03-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bf03-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bf03-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bf03-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
