---
title: "ICorDebugEval2::NewStringWithLength 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1cd2bc201210bc9af8c13c83553b581c080f658a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="6b5a0-102">ICorDebugEval2::NewStringWithLength 方法</span><span class="sxs-lookup"><span data-stu-id="6b5a0-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="6b5a0-103">具有指定的內容建立指定之長度的字串。</span><span class="sxs-lookup"><span data-stu-id="6b5a0-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b5a0-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b5a0-104">Syntax</span></span>  
  
```  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b5a0-105">參數</span><span class="sxs-lookup"><span data-stu-id="6b5a0-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="6b5a0-106">[in]字串值的指標。</span><span class="sxs-lookup"><span data-stu-id="6b5a0-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="6b5a0-107">[in]字串的長度。</span><span class="sxs-lookup"><span data-stu-id="6b5a0-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b5a0-108">備註</span><span class="sxs-lookup"><span data-stu-id="6b5a0-108">Remarks</span></span>  
 <span data-ttu-id="6b5a0-109">如果字串的尾端的 null 字元預計要採用的 managed 字串，呼叫端的`NewStringWithLength`方法必須確定字串長度包含之尾端的 null 字元。</span><span class="sxs-lookup"><span data-stu-id="6b5a0-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="6b5a0-110">字串，永遠會建立所在的執行緒目前正在執行的應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="6b5a0-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b5a0-111">需求</span><span class="sxs-lookup"><span data-stu-id="6b5a0-111">Requirements</span></span>  
 <span data-ttu-id="6b5a0-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b5a0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b5a0-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b5a0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b5a0-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b5a0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b5a0-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b5a0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
