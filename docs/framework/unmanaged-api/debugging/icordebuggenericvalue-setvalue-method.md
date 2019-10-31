---
title: ICorDebugGenericValue::SetValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type:
- apiref
ms.openlocfilehash: 4cd03895b4e33c3e42c71acca12eaf950fc9a145
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138550"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="7a21f-102">ICorDebugGenericValue::SetValue 方法</span><span class="sxs-lookup"><span data-stu-id="7a21f-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="7a21f-103">從指定的緩衝區複製新的值。</span><span class="sxs-lookup"><span data-stu-id="7a21f-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a21f-104">語法</span><span class="sxs-lookup"><span data-stu-id="7a21f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a21f-105">參數</span><span class="sxs-lookup"><span data-stu-id="7a21f-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="7a21f-106">在要從中複製值之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="7a21f-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a21f-107">備註</span><span class="sxs-lookup"><span data-stu-id="7a21f-107">Remarks</span></span>  
 <span data-ttu-id="7a21f-108">對於參考型別，此值為參考，而非內容。</span><span class="sxs-lookup"><span data-stu-id="7a21f-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a21f-109">需求</span><span class="sxs-lookup"><span data-stu-id="7a21f-109">Requirements</span></span>  
 <span data-ttu-id="7a21f-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a21f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a21f-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a21f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a21f-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a21f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a21f-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a21f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
