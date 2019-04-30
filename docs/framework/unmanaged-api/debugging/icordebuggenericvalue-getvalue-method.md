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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53db4dcb13303c9e7bdd77a46b3c9526364bac06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995640"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="428ff-102">ICorDebugGenericValue::GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="428ff-102">ICorDebugGenericValue::GetValue Method</span></span>
<span data-ttu-id="428ff-103">將此泛型的值複製到指定的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="428ff-103">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="428ff-104">語法</span><span class="sxs-lookup"><span data-stu-id="428ff-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="428ff-105">參數</span><span class="sxs-lookup"><span data-stu-id="428ff-105">Parameters</span></span>  
 `pTo`  
 <span data-ttu-id="428ff-106">[out]此 ICorDebugGenericValue 物件所代表的值的指標。</span><span class="sxs-lookup"><span data-stu-id="428ff-106">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="428ff-107">值可能是簡單類型或參考類型 （也就是指標）。</span><span class="sxs-lookup"><span data-stu-id="428ff-107">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="428ff-108">需求</span><span class="sxs-lookup"><span data-stu-id="428ff-108">Requirements</span></span>  
 <span data-ttu-id="428ff-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="428ff-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="428ff-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="428ff-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="428ff-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="428ff-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="428ff-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="428ff-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
