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
ms.openlocfilehash: c4b01b2c346d3173b2a5ecc144474d7fb1e6dce5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138977"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="39e46-102">ICorDebugStringValue::GetString 方法</span><span class="sxs-lookup"><span data-stu-id="39e46-102">ICorDebugStringValue::GetString Method</span></span>
<span data-ttu-id="39e46-103">取得此 ICorDebugStringValue 所參考的字串。</span><span class="sxs-lookup"><span data-stu-id="39e46-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39e46-104">語法</span><span class="sxs-lookup"><span data-stu-id="39e46-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]   
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39e46-105">參數</span><span class="sxs-lookup"><span data-stu-id="39e46-105">Parameters</span></span>  
 `cchString`  
 <span data-ttu-id="39e46-106">[in] `szString` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="39e46-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="39e46-107">脫銷`szString` 陣列中傳回的字元數指標。</span><span class="sxs-lookup"><span data-stu-id="39e46-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="39e46-108">脫銷儲存已抓取字串的陣列。</span><span class="sxs-lookup"><span data-stu-id="39e46-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39e46-109">需求</span><span class="sxs-lookup"><span data-stu-id="39e46-109">Requirements</span></span>  
 <span data-ttu-id="39e46-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="39e46-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39e46-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39e46-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39e46-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39e46-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39e46-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39e46-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
