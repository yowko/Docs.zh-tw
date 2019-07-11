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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a90f0a0319d88654d0310530749ef35b7095e0fb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754422"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="be4ad-102">ICorDebugEval2::NewStringWithLength 方法</span><span class="sxs-lookup"><span data-stu-id="be4ad-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="be4ad-103">使用指定的內容中建立的指定長度的字串。</span><span class="sxs-lookup"><span data-stu-id="be4ad-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be4ad-104">語法</span><span class="sxs-lookup"><span data-stu-id="be4ad-104">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be4ad-105">參數</span><span class="sxs-lookup"><span data-stu-id="be4ad-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="be4ad-106">[in]字串值的指標。</span><span class="sxs-lookup"><span data-stu-id="be4ad-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="be4ad-107">[in]字串的長度。</span><span class="sxs-lookup"><span data-stu-id="be4ad-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be4ad-108">備註</span><span class="sxs-lookup"><span data-stu-id="be4ad-108">Remarks</span></span>  
 <span data-ttu-id="be4ad-109">如果字串的尾端預期的 null 字元會在受管理的字串中，呼叫端`NewStringWithLength`方法必須確保字串長度包含之尾端的 null 字元。</span><span class="sxs-lookup"><span data-stu-id="be4ad-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="be4ad-110">字串一律會建立目前執行所在之執行緒的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="be4ad-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be4ad-111">需求</span><span class="sxs-lookup"><span data-stu-id="be4ad-111">Requirements</span></span>  
 <span data-ttu-id="be4ad-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be4ad-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be4ad-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be4ad-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be4ad-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be4ad-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be4ad-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be4ad-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
