---
title: ICorDebugStringValue::GetLength 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetLength
helpviewer_keywords:
- ICorDebugStringValue::GetLength method [.NET Framework debugging]
- GetLength method [.NET Framework debugging]
ms.assetid: a1ebfc69-46a6-4225-8788-b7cfb2f15e1d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b168673e76beddd8ae0479b8daae009c5f057b2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494658"
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="c8287-102">ICorDebugStringValue::GetLength 方法</span><span class="sxs-lookup"><span data-stu-id="c8287-102">ICorDebugStringValue::GetLength Method</span></span>
<span data-ttu-id="c8287-103">取得此 ICorDebugStringValue 所參考的字串中的字元數。</span><span class="sxs-lookup"><span data-stu-id="c8287-103">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8287-104">語法</span><span class="sxs-lookup"><span data-stu-id="c8287-104">Syntax</span></span>  
  
```  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8287-105">參數</span><span class="sxs-lookup"><span data-stu-id="c8287-105">Parameters</span></span>  
 `pcchString`  
 <span data-ttu-id="c8287-106">[out]值，指定所參考的字串長度的指標`ICorDebugStringValue`物件。</span><span class="sxs-lookup"><span data-stu-id="c8287-106">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8287-107">需求</span><span class="sxs-lookup"><span data-stu-id="c8287-107">Requirements</span></span>  
 <span data-ttu-id="c8287-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8287-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8287-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8287-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8287-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8287-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8287-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8287-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
