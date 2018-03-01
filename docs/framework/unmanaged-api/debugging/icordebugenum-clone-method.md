---
title: "ICorDebugEnum::Clone 方法"
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
- ICorDebugEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Clone
helpviewer_keywords:
- Clone method, ICorDebugEnum interface [.NET Framework debugging]
- ICorDebugEnum::Clone method [.NET Framework debugging]
ms.assetid: 57eefaf3-75cf-4496-bc94-88c0706861b7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5ddd7d82b6eb2944b1d2a5d7a83f0ccc9f255e45
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="bb2cc-102">ICorDebugEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="bb2cc-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="bb2cc-103">建立這個 ICorDebugEnum 物件的複本。</span><span class="sxs-lookup"><span data-stu-id="bb2cc-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb2cc-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb2cc-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb2cc-105">參數</span><span class="sxs-lookup"><span data-stu-id="bb2cc-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="bb2cc-106">[out]位址指標`ICorDebugEnum`物件之這個複本`ICorDebugEnum`物件。</span><span class="sxs-lookup"><span data-stu-id="bb2cc-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb2cc-107">需求</span><span class="sxs-lookup"><span data-stu-id="bb2cc-107">Requirements</span></span>  
 <span data-ttu-id="bb2cc-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb2cc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb2cc-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb2cc-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb2cc-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb2cc-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb2cc-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb2cc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
