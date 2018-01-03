---
title: "ICorDebugHandleValue::GetHandleType 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHandleValue.GetHandleType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHandleValue::GetHandleType
helpviewer_keywords:
- GetHandleType method [.NET Framework debugging]
- ICorDebugHandleValue::GetHandleType method [.NET Framework debugging]
ms.assetid: d5e7b12d-835a-4e86-ae2f-d658d4f1c67c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b41e7c14fd0abdd957f0661345a6372074f2ed7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebughandlevaluegethandletype-method"></a><span data-ttu-id="27f04-102">ICorDebugHandleValue::GetHandleType 方法</span><span class="sxs-lookup"><span data-stu-id="27f04-102">ICorDebugHandleValue::GetHandleType Method</span></span>
<span data-ttu-id="27f04-103">取得值，指出此 ICorDebugHandleValue 物件所參考的控制代碼的類型。</span><span class="sxs-lookup"><span data-stu-id="27f04-103">Gets a value that indicates the kind of handle referenced by this ICorDebugHandleValue object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27f04-104">語法</span><span class="sxs-lookup"><span data-stu-id="27f04-104">Syntax</span></span>  
  
```  
HRESULT GetHandleType (  
    [out] CorDebugHandleType  *pType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27f04-105">參數</span><span class="sxs-lookup"><span data-stu-id="27f04-105">Parameters</span></span>  
 `pType`  
 <span data-ttu-id="27f04-106">[out]CorDebugHandleType 列舉，指出這個控制代碼類型的值的指標。</span><span class="sxs-lookup"><span data-stu-id="27f04-106">[out] A pointer to a value of the CorDebugHandleType enumeration that indicates the type of this handle.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27f04-107">需求</span><span class="sxs-lookup"><span data-stu-id="27f04-107">Requirements</span></span>  
 <span data-ttu-id="27f04-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27f04-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27f04-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27f04-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27f04-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27f04-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27f04-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27f04-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
