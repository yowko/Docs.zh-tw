---
title: "ICorDebugStringValue::GetLength 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 129998bc2e7530aefefb2655a83cb04a9aa4cc6c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="225a9-102">ICorDebugStringValue::GetLength 方法</span><span class="sxs-lookup"><span data-stu-id="225a9-102">ICorDebugStringValue::GetLength Method</span></span>
<span data-ttu-id="225a9-103">在此 ICorDebugStringValue 所參考的字串中取得字元的數。</span><span class="sxs-lookup"><span data-stu-id="225a9-103">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="225a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="225a9-104">Syntax</span></span>  
  
```  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="225a9-105">參數</span><span class="sxs-lookup"><span data-stu-id="225a9-105">Parameters</span></span>  
 `pcchString`  
 <span data-ttu-id="225a9-106">[out]值，指定所參考的字串長度的指標`ICorDebugStringValue`物件。</span><span class="sxs-lookup"><span data-stu-id="225a9-106">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="225a9-107">需求</span><span class="sxs-lookup"><span data-stu-id="225a9-107">Requirements</span></span>  
 <span data-ttu-id="225a9-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="225a9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="225a9-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="225a9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="225a9-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="225a9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="225a9-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="225a9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
