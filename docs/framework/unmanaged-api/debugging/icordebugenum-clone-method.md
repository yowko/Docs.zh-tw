---
title: ICorDebugEnum::Clone 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d1226f64df379b5c40304221e9e66eebcdb17b4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479229"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="d6ce4-102">ICorDebugEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="d6ce4-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="d6ce4-103">建立這個 ICorDebugEnum 物件的複本。</span><span class="sxs-lookup"><span data-stu-id="d6ce4-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6ce4-104">語法</span><span class="sxs-lookup"><span data-stu-id="d6ce4-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6ce4-105">參數</span><span class="sxs-lookup"><span data-stu-id="d6ce4-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="d6ce4-106">[out]位址指標`ICorDebugEnum`物件，這個複本`ICorDebugEnum`物件。</span><span class="sxs-lookup"><span data-stu-id="d6ce4-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6ce4-107">需求</span><span class="sxs-lookup"><span data-stu-id="d6ce4-107">Requirements</span></span>  
 <span data-ttu-id="d6ce4-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6ce4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6ce4-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6ce4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6ce4-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6ce4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6ce4-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6ce4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
