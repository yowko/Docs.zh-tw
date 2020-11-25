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
ms.openlocfilehash: e5bab32f6d18c87b030f484a47bc3f1d525d2338
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729625"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="1ef5b-102">ICorDebugEval2::NewStringWithLength 方法</span><span class="sxs-lookup"><span data-stu-id="1ef5b-102">ICorDebugEval2::NewStringWithLength Method</span></span>

<span data-ttu-id="1ef5b-103">使用指定的內容，建立指定長度的字串。</span><span class="sxs-lookup"><span data-stu-id="1ef5b-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef5b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ef5b-104">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ef5b-105">參數</span><span class="sxs-lookup"><span data-stu-id="1ef5b-105">Parameters</span></span>  

 `string`  
 <span data-ttu-id="1ef5b-106">在字串值的指標。</span><span class="sxs-lookup"><span data-stu-id="1ef5b-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="1ef5b-107">在字串的長度。</span><span class="sxs-lookup"><span data-stu-id="1ef5b-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ef5b-108">備註</span><span class="sxs-lookup"><span data-stu-id="1ef5b-108">Remarks</span></span>  

 <span data-ttu-id="1ef5b-109">如果字串的尾端 null 字元應該在 managed 字串中，則方法的呼叫端 `NewStringWithLength` 必須確定字串長度包含尾端的 null 字元。</span><span class="sxs-lookup"><span data-stu-id="1ef5b-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="1ef5b-110">字串一律會建立線上程目前執行所在的應用程式域中。</span><span class="sxs-lookup"><span data-stu-id="1ef5b-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ef5b-111">需求</span><span class="sxs-lookup"><span data-stu-id="1ef5b-111">Requirements</span></span>  

 <span data-ttu-id="1ef5b-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ef5b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ef5b-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ef5b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ef5b-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ef5b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ef5b-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ef5b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
