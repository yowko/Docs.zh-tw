---
title: ICorDebugModule::GetBaseAddress 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetBaseAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11685e8ceba1638ce99a8c4c47b66d0ae2e67714
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476161"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="b1d63-102">ICorDebugModule::GetBaseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="b1d63-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="b1d63-103">取得模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="b1d63-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1d63-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1d63-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1d63-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1d63-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="b1d63-106">[out]A`CORDB_ADDRESS`指定模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="b1d63-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1d63-107">備註</span><span class="sxs-lookup"><span data-stu-id="b1d63-107">Remarks</span></span>  
 <span data-ttu-id="b1d63-108">如果模組是原生映像 （亦即，如果模組由原生映像產生器 NGen.exe 產生），其基底的位址將會是零。</span><span class="sxs-lookup"><span data-stu-id="b1d63-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1d63-109">需求</span><span class="sxs-lookup"><span data-stu-id="b1d63-109">Requirements</span></span>  
 <span data-ttu-id="b1d63-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1d63-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1d63-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1d63-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1d63-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1d63-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1d63-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1d63-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1d63-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1d63-114">See also</span></span>


