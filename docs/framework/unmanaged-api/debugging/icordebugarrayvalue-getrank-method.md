---
title: "ICorDebugArrayValue::GetRank 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue.GetRank
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue::GetRank
helpviewer_keywords:
- ICorDebugArrayValue::GetRank method [.NET Framework debugging]
- GetRank method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 5e83c82c-593d-4691-90b0-383d218b415e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a7e92a0edfe220bda820550cc385bf2eb3846b08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugarrayvaluegetrank-method"></a><span data-ttu-id="eaca6-102">ICorDebugArrayValue::GetRank 方法</span><span class="sxs-lookup"><span data-stu-id="eaca6-102">ICorDebugArrayValue::GetRank Method</span></span>
<span data-ttu-id="eaca6-103">取得陣列的維度數目。</span><span class="sxs-lookup"><span data-stu-id="eaca6-103">Gets the number of dimensions in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaca6-104">語法</span><span class="sxs-lookup"><span data-stu-id="eaca6-104">Syntax</span></span>  
  
```  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eaca6-105">參數</span><span class="sxs-lookup"><span data-stu-id="eaca6-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="eaca6-106">[out]在這個維度數目的指標`ICorDebugArrayValue`物件。</span><span class="sxs-lookup"><span data-stu-id="eaca6-106">[out] A pointer to the number of dimensions in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaca6-107">需求</span><span class="sxs-lookup"><span data-stu-id="eaca6-107">Requirements</span></span>  
 <span data-ttu-id="eaca6-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eaca6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaca6-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eaca6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eaca6-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eaca6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eaca6-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaca6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
