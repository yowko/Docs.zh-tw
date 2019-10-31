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
ms.openlocfilehash: aff8fb0a2316817e413f10e82215556f1f54fbc4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109630"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="3dfcb-102">ICorDebugModule::GetBaseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="3dfcb-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="3dfcb-103">取得模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="3dfcb-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dfcb-104">語法</span><span class="sxs-lookup"><span data-stu-id="3dfcb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dfcb-105">參數</span><span class="sxs-lookup"><span data-stu-id="3dfcb-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="3dfcb-106">脫銷指定模組基底位址的 `CORDB_ADDRESS`。</span><span class="sxs-lookup"><span data-stu-id="3dfcb-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dfcb-107">備註</span><span class="sxs-lookup"><span data-stu-id="3dfcb-107">Remarks</span></span>  
 <span data-ttu-id="3dfcb-108">如果模組是原生映射（也就是，如果模組是由原生映射產生器（Ngen.exe）所產生），其基底位址會是零。</span><span class="sxs-lookup"><span data-stu-id="3dfcb-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dfcb-109">需求</span><span class="sxs-lookup"><span data-stu-id="3dfcb-109">Requirements</span></span>  
 <span data-ttu-id="3dfcb-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3dfcb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dfcb-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3dfcb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dfcb-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dfcb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3dfcb-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dfcb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dfcb-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="3dfcb-114">See also</span></span>
