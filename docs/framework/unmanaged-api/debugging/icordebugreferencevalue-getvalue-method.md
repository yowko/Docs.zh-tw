---
title: "ICorDebugReferenceValue::GetValue 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugReferenceValue.GetValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugReferenceValue::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::GetValue method [.NET Framework debugging]
ms.assetid: 5da07f99-6c70-46ec-b997-5ab6fb7106cd
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6d7be70ec41b2044b4af10e102218ce487e4a5e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugreferencevaluegetvalue-method"></a><span data-ttu-id="8403f-102">ICorDebugReferenceValue::GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="8403f-102">ICorDebugReferenceValue::GetValue Method</span></span>
<span data-ttu-id="8403f-103">取得參考物件的目前記憶體位址。</span><span class="sxs-lookup"><span data-stu-id="8403f-103">Gets the current memory address of the referenced object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8403f-104">語法</span><span class="sxs-lookup"><span data-stu-id="8403f-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] CORDB_ADDRESS   *pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8403f-105">參數</span><span class="sxs-lookup"><span data-stu-id="8403f-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="8403f-106">[out]指標`CORDB_ADDRESS`值，指定這個 ICorDebugReferenceValue 物件指向的物件的位址。</span><span class="sxs-lookup"><span data-stu-id="8403f-106">[out] A pointer to a `CORDB_ADDRESS` value that specifies the address of the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8403f-107">需求</span><span class="sxs-lookup"><span data-stu-id="8403f-107">Requirements</span></span>  
 <span data-ttu-id="8403f-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8403f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8403f-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8403f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8403f-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8403f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8403f-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8403f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
