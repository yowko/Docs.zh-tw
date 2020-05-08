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
ms.openlocfilehash: a2b76cb59a95082e0cf9c0884b8277cca3c8fe8d
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976066"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="23c05-102">ICorDebugEval2::NewStringWithLength 方法</span><span class="sxs-lookup"><span data-stu-id="23c05-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="23c05-103">使用指定的內容，建立指定長度的字串。</span><span class="sxs-lookup"><span data-stu-id="23c05-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23c05-104">語法</span><span class="sxs-lookup"><span data-stu-id="23c05-104">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23c05-105">參數</span><span class="sxs-lookup"><span data-stu-id="23c05-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="23c05-106">在字串值的指標。</span><span class="sxs-lookup"><span data-stu-id="23c05-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="23c05-107">在字串的長度。</span><span class="sxs-lookup"><span data-stu-id="23c05-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23c05-108">備註</span><span class="sxs-lookup"><span data-stu-id="23c05-108">Remarks</span></span>  
 <span data-ttu-id="23c05-109">如果字串尾端的 null 字元應該在 managed 字串中，則`NewStringWithLength`方法的呼叫端必須確保字串長度包含尾端的 null 字元。</span><span class="sxs-lookup"><span data-stu-id="23c05-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="23c05-110">此字串一律會線上程目前執行所在的應用程式域中建立。</span><span class="sxs-lookup"><span data-stu-id="23c05-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23c05-111">需求</span><span class="sxs-lookup"><span data-stu-id="23c05-111">Requirements</span></span>  
 <span data-ttu-id="23c05-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23c05-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23c05-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23c05-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23c05-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23c05-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23c05-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23c05-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
