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
ms.openlocfilehash: 2ec769c343ad055132c6d84e64600fc459357a85
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124712"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="42350-102">ICorDebugEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="42350-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="42350-103">建立這個 ICorDebugEnum 物件的複本。</span><span class="sxs-lookup"><span data-stu-id="42350-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42350-104">語法</span><span class="sxs-lookup"><span data-stu-id="42350-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42350-105">參數</span><span class="sxs-lookup"><span data-stu-id="42350-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="42350-106">脫銷這個 `ICorDebugEnum` 物件之複本的 `ICorDebugEnum` 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="42350-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42350-107">需求</span><span class="sxs-lookup"><span data-stu-id="42350-107">Requirements</span></span>  
 <span data-ttu-id="42350-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="42350-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42350-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42350-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42350-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42350-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42350-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42350-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
