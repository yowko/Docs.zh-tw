---
title: ICorDebugReferenceValue::GetValue 方法
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::GetValue method [.NET Framework debugging]
ms.assetid: 5da07f99-6c70-46ec-b997-5ab6fb7106cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5542cf5895bc60c5880f2f082a9c14d722e02478
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744918"
---
# <a name="icordebugreferencevaluegetvalue-method"></a><span data-ttu-id="1d073-102">ICorDebugReferenceValue::GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="1d073-102">ICorDebugReferenceValue::GetValue Method</span></span>
<span data-ttu-id="1d073-103">取得參考物件的目前記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="1d073-103">Gets the current memory address of the referenced object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d073-104">語法</span><span class="sxs-lookup"><span data-stu-id="1d073-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] CORDB_ADDRESS   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d073-105">參數</span><span class="sxs-lookup"><span data-stu-id="1d073-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="1d073-106">[out]指標`CORDB_ADDRESS`值，指定這個 ICorDebugReferenceValue 物件指向的物件的位址。</span><span class="sxs-lookup"><span data-stu-id="1d073-106">[out] A pointer to a `CORDB_ADDRESS` value that specifies the address of the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d073-107">需求</span><span class="sxs-lookup"><span data-stu-id="1d073-107">Requirements</span></span>  
 <span data-ttu-id="1d073-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d073-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d073-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d073-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d073-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d073-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d073-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d073-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
