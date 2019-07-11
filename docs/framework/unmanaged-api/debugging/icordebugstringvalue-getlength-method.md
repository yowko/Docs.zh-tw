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
ms.openlocfilehash: b13fe65f892a222abb126aa9237b802507738b7f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771603"
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="5bd8b-102">ICorDebugStringValue::GetLength 方法</span><span class="sxs-lookup"><span data-stu-id="5bd8b-102">ICorDebugStringValue::GetLength Method</span></span>
<span data-ttu-id="5bd8b-103">取得此 ICorDebugStringValue 所參考的字串中的字元數。</span><span class="sxs-lookup"><span data-stu-id="5bd8b-103">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bd8b-104">語法</span><span class="sxs-lookup"><span data-stu-id="5bd8b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bd8b-105">參數</span><span class="sxs-lookup"><span data-stu-id="5bd8b-105">Parameters</span></span>  
 `pcchString`  
 <span data-ttu-id="5bd8b-106">[out]值，指定所參考的字串長度的指標`ICorDebugStringValue`物件。</span><span class="sxs-lookup"><span data-stu-id="5bd8b-106">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bd8b-107">需求</span><span class="sxs-lookup"><span data-stu-id="5bd8b-107">Requirements</span></span>  
 <span data-ttu-id="5bd8b-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5bd8b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bd8b-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5bd8b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5bd8b-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bd8b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bd8b-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bd8b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
