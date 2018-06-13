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
ms.openlocfilehash: da16a22c71c1fac1932f74a9af18fbc30eb326f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410828"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="83e70-102">ICorDebugEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="83e70-102">ICorDebugEnum::Clone Method</span></span>
<span data-ttu-id="83e70-103">建立這個 ICorDebugEnum 物件的複本。</span><span class="sxs-lookup"><span data-stu-id="83e70-103">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83e70-104">語法</span><span class="sxs-lookup"><span data-stu-id="83e70-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83e70-105">參數</span><span class="sxs-lookup"><span data-stu-id="83e70-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="83e70-106">[out]位址指標`ICorDebugEnum`物件之這個複本`ICorDebugEnum`物件。</span><span class="sxs-lookup"><span data-stu-id="83e70-106">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83e70-107">需求</span><span class="sxs-lookup"><span data-stu-id="83e70-107">Requirements</span></span>  
 <span data-ttu-id="83e70-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83e70-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83e70-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83e70-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83e70-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83e70-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83e70-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83e70-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
