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
ms.openlocfilehash: 965ce04b02a0eb1ca30aba065b3e372332e08b55
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752286"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="6ae3a-102">ICorDebugEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="6ae3a-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="6ae3a-103">建立這個 ICorDebugEnum 物件的複本。</span><span class="sxs-lookup"><span data-stu-id="6ae3a-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ae3a-104">語法</span><span class="sxs-lookup"><span data-stu-id="6ae3a-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ae3a-105">參數</span><span class="sxs-lookup"><span data-stu-id="6ae3a-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="6ae3a-106">[out]位址指標`ICorDebugEnum`物件，這個複本`ICorDebugEnum`物件。</span><span class="sxs-lookup"><span data-stu-id="6ae3a-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ae3a-107">需求</span><span class="sxs-lookup"><span data-stu-id="6ae3a-107">Requirements</span></span>  
 <span data-ttu-id="6ae3a-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6ae3a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ae3a-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ae3a-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ae3a-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ae3a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ae3a-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ae3a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
