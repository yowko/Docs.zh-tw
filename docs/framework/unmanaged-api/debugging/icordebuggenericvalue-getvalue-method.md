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
ms.openlocfilehash: 646b2661148e38f3c918fc18fce5c9cd0b1134a1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213019"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="19a02-102">ICorDebugGenericValue::GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="19a02-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="19a02-103">將這個泛型的值複製到指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="19a02-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19a02-104">語法</span><span class="sxs-lookup"><span data-stu-id="19a02-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19a02-105">參數</span><span class="sxs-lookup"><span data-stu-id="19a02-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="19a02-106">脫銷這個 ICorDebugGenericValue 物件所表示之值的指標。</span><span class="sxs-lookup"><span data-stu-id="19a02-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="19a02-107">此值可以是簡單類型或參考型別（也就是指標）。</span><span class="sxs-lookup"><span data-stu-id="19a02-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19a02-108">需求</span><span class="sxs-lookup"><span data-stu-id="19a02-108">Requirements</span></span>  
 <span data-ttu-id="19a02-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19a02-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19a02-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19a02-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19a02-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19a02-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19a02-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19a02-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
