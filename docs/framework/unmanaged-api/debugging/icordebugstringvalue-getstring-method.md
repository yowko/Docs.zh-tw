---
title: ICorDebugStringValue::GetString 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetString
helpviewer_keywords:
- ICorDebugStringValue::GetString method [.NET Framework debugging]
- GetString method, ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: 2b94bda7-09ee-435d-91b9-c4e31af1896c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bf62d8855b3f9de5629b9cfc6e0bcd0878a0d17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987359"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="22b21-102">ICorDebugStringValue::GetString 方法</span><span class="sxs-lookup"><span data-stu-id="22b21-102">ICorDebugStringValue::GetString Method</span></span>
<span data-ttu-id="22b21-103">取得此 ICorDebugStringValue 所參考的字串。</span><span class="sxs-lookup"><span data-stu-id="22b21-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22b21-104">語法</span><span class="sxs-lookup"><span data-stu-id="22b21-104">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]   
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22b21-105">參數</span><span class="sxs-lookup"><span data-stu-id="22b21-105">Parameters</span></span>  
 `cchString`  
 <span data-ttu-id="22b21-106">[in] `szString` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="22b21-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="22b21-107">[out]傳入的字元數的指標`szString`陣列。</span><span class="sxs-lookup"><span data-stu-id="22b21-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="22b21-108">[out]儲存擷取的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="22b21-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22b21-109">需求</span><span class="sxs-lookup"><span data-stu-id="22b21-109">Requirements</span></span>  
 <span data-ttu-id="22b21-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22b21-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22b21-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22b21-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22b21-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22b21-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22b21-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22b21-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
