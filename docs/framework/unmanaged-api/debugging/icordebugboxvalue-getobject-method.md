---
title: "ICorDebugBoxValue::GetObject 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBoxValue.GetObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e71da40af57d00e4651c094ddad9c86fc6fe636
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="5c31c-102">ICorDebugBoxValue::GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="5c31c-102">ICorDebugBoxValue::GetObject Method</span></span>
<span data-ttu-id="5c31c-103">取得 boxed 的值。</span><span class="sxs-lookup"><span data-stu-id="5c31c-103">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c31c-104">語法</span><span class="sxs-lookup"><span data-stu-id="5c31c-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c31c-105">參數</span><span class="sxs-lookup"><span data-stu-id="5c31c-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="5c31c-106">[out]ICorDebugObjectValue 物件，表示 boxed 的值的位址指標。</span><span class="sxs-lookup"><span data-stu-id="5c31c-106">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c31c-107">需求</span><span class="sxs-lookup"><span data-stu-id="5c31c-107">Requirements</span></span>  
 <span data-ttu-id="5c31c-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c31c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c31c-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c31c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c31c-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c31c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c31c-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c31c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
