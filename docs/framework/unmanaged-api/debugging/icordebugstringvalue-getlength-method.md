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
ms.openlocfilehash: a6f2f536d360ffe41caf2a96c8b051f9167343c2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138961"
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="c8cb4-102">ICorDebugStringValue::GetLength 方法</span><span class="sxs-lookup"><span data-stu-id="c8cb4-102">ICorDebugStringValue::GetLength Method</span></span>
<span data-ttu-id="c8cb4-103">取得此 ICorDebugStringValue 所參考字串中的字元數。</span><span class="sxs-lookup"><span data-stu-id="c8cb4-103">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8cb4-104">語法</span><span class="sxs-lookup"><span data-stu-id="c8cb4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8cb4-105">參數</span><span class="sxs-lookup"><span data-stu-id="c8cb4-105">Parameters</span></span>  
 `pcchString`  
 <span data-ttu-id="c8cb4-106">脫銷值的指標，指定這個 `ICorDebugStringValue` 物件所參考的字串長度。</span><span class="sxs-lookup"><span data-stu-id="c8cb4-106">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8cb4-107">需求</span><span class="sxs-lookup"><span data-stu-id="c8cb4-107">Requirements</span></span>  
 <span data-ttu-id="c8cb4-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8cb4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8cb4-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8cb4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8cb4-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8cb4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8cb4-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8cb4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
