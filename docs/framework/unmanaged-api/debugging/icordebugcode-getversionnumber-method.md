---
title: ICorDebugCode::GetVersionNumber 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type:
- apiref
ms.openlocfilehash: 646c20ca1b78ff0ce513b8a3c9b578c3b1b9a696
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125607"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="73383-102">ICorDebugCode::GetVersionNumber 方法</span><span class="sxs-lookup"><span data-stu-id="73383-102">ICorDebugCode::GetVersionNumber Method</span></span>

<span data-ttu-id="73383-103">取得以1為基礎的數位，識別這個 "ICorDebugCode" 所代表的程式碼版本。</span><span class="sxs-lookup"><span data-stu-id="73383-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>

## <a name="syntax"></a><span data-ttu-id="73383-104">語法</span><span class="sxs-lookup"><span data-stu-id="73383-104">Syntax</span></span>

```cpp
HRESULT GetVersionNumber (
    [out] ULONG32    *nVersion
);
```

## <a name="parameters"></a><span data-ttu-id="73383-105">參數</span><span class="sxs-lookup"><span data-stu-id="73383-105">Parameters</span></span>

 `nVersion`  
 <span data-ttu-id="73383-106">脫銷程式碼版本號碼的指標。</span><span class="sxs-lookup"><span data-stu-id="73383-106">[out] A pointer to the version number of the code.</span></span>

## <a name="remarks"></a><span data-ttu-id="73383-107">備註</span><span class="sxs-lookup"><span data-stu-id="73383-107">Remarks</span></span>

 <span data-ttu-id="73383-108">每次對程式碼執行「編輯後繼續」（EnC）作業時，版本號碼都會遞增。</span><span class="sxs-lookup"><span data-stu-id="73383-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>

## <a name="requirements"></a><span data-ttu-id="73383-109">需求</span><span class="sxs-lookup"><span data-stu-id="73383-109">Requirements</span></span>

 <span data-ttu-id="73383-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="73383-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73383-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73383-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73383-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73383-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73383-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73383-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
