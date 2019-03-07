---
title: ICorDebugVariableHome::GetOffset 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6880584fe407d651010fad885c2dd5983ad4dfcf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492461"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="44f4c-102">ICorDebugVariableHome::GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="44f4c-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="44f4c-103">取得從基底的暫存器變數的位移。</span><span class="sxs-lookup"><span data-stu-id="44f4c-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44f4c-104">語法</span><span class="sxs-lookup"><span data-stu-id="44f4c-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44f4c-105">參數</span><span class="sxs-lookup"><span data-stu-id="44f4c-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="44f4c-106">[out]從 基底的暫存器的位移。</span><span class="sxs-lookup"><span data-stu-id="44f4c-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44f4c-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="44f4c-107">Return Value</span></span>  
 <span data-ttu-id="44f4c-108">方法會傳回下列值：</span><span class="sxs-lookup"><span data-stu-id="44f4c-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="44f4c-109">值</span><span class="sxs-lookup"><span data-stu-id="44f4c-109">Value</span></span>|<span data-ttu-id="44f4c-110">描述</span><span class="sxs-lookup"><span data-stu-id="44f4c-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="44f4c-111">變數是在暫存器的相對記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="44f4c-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="44f4c-112">變數不是位在暫存器的相對記憶體位置中。</span><span class="sxs-lookup"><span data-stu-id="44f4c-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44f4c-113">需求</span><span class="sxs-lookup"><span data-stu-id="44f4c-113">Requirements</span></span>  
 <span data-ttu-id="44f4c-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="44f4c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44f4c-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="44f4c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="44f4c-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44f4c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44f4c-117">**.NET framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44f4c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44f4c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44f4c-118">See also</span></span>
- [<span data-ttu-id="44f4c-119">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="44f4c-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
