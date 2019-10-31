---
title: ICorDebugEval2::NewStringWithLength 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
ms.openlocfilehash: 3836b6c08098d38516c8a25260fb28998a2317fe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084787"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="096e8-102">ICorDebugEval2::NewStringWithLength 方法</span><span class="sxs-lookup"><span data-stu-id="096e8-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="096e8-103">使用指定的內容，建立指定長度的字串。</span><span class="sxs-lookup"><span data-stu-id="096e8-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="096e8-104">語法</span><span class="sxs-lookup"><span data-stu-id="096e8-104">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="096e8-105">參數</span><span class="sxs-lookup"><span data-stu-id="096e8-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="096e8-106">在字串值的指標。</span><span class="sxs-lookup"><span data-stu-id="096e8-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="096e8-107">在字串的長度。</span><span class="sxs-lookup"><span data-stu-id="096e8-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="096e8-108">備註</span><span class="sxs-lookup"><span data-stu-id="096e8-108">Remarks</span></span>  
 <span data-ttu-id="096e8-109">如果字串尾端的 null 字元必須位於 managed 字串中，則 `NewStringWithLength` 方法的呼叫端必須確保字串長度包含尾端的 null 字元。</span><span class="sxs-lookup"><span data-stu-id="096e8-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="096e8-110">此字串一律會線上程目前執行所在的應用程式域中建立。</span><span class="sxs-lookup"><span data-stu-id="096e8-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="096e8-111">需求</span><span class="sxs-lookup"><span data-stu-id="096e8-111">Requirements</span></span>  
 <span data-ttu-id="096e8-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="096e8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="096e8-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="096e8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="096e8-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="096e8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="096e8-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="096e8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
