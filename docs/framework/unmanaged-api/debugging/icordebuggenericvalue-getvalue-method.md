---
title: ICorDebugGenericValue::GetValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type:
- apiref
ms.openlocfilehash: 7923008eecb9011bead685fbbb7f05f81f12329b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138583"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="a22f1-102">ICorDebugGenericValue::GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="a22f1-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="a22f1-103">將這個泛型的值複製到指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a22f1-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a22f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="a22f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a22f1-105">參數</span><span class="sxs-lookup"><span data-stu-id="a22f1-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="a22f1-106">脫銷這個 ICorDebugGenericValue 物件所表示之值的指標。</span><span class="sxs-lookup"><span data-stu-id="a22f1-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="a22f1-107">此值可以是簡單類型或參考型別（也就是指標）。</span><span class="sxs-lookup"><span data-stu-id="a22f1-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a22f1-108">需求</span><span class="sxs-lookup"><span data-stu-id="a22f1-108">Requirements</span></span>  
 <span data-ttu-id="a22f1-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a22f1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a22f1-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a22f1-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a22f1-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a22f1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a22f1-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a22f1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
