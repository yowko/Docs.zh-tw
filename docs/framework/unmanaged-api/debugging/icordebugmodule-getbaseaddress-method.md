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
ms.openlocfilehash: 9270afa1d8c8ddd74cfe6dd05e39c1480f5767e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206940"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="96612-102">ICorDebugModule::GetBaseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="96612-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="96612-103">取得模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="96612-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96612-104">語法</span><span class="sxs-lookup"><span data-stu-id="96612-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96612-105">參數</span><span class="sxs-lookup"><span data-stu-id="96612-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="96612-106">脫銷`CORDB_ADDRESS`指定模組基底位址的。</span><span class="sxs-lookup"><span data-stu-id="96612-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96612-107">備註</span><span class="sxs-lookup"><span data-stu-id="96612-107">Remarks</span></span>  
 <span data-ttu-id="96612-108">如果模組是原生映射（也就是，如果模組是由原生映射產生器（Ngen.exe）所產生），其基底位址會是零。</span><span class="sxs-lookup"><span data-stu-id="96612-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96612-109">需求</span><span class="sxs-lookup"><span data-stu-id="96612-109">Requirements</span></span>  
 <span data-ttu-id="96612-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="96612-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96612-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96612-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96612-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96612-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96612-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96612-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96612-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96612-114">See also</span></span>
