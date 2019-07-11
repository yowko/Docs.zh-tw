---
title: ICorDebugVariableHome::GetRegister 方法
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4b3b80546095b79dc5b551a9c5e92ec15c0dddb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771796"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="c70da-102">ICorDebugVariableHome::GetRegister 方法</span><span class="sxs-lookup"><span data-stu-id="c70da-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="c70da-103">取得包含位置類型的變數的暫存`VLT_REGISTER`，及基底的位置類型的變數報名`VLT_REGISTER_RELATIVE`。</span><span class="sxs-lookup"><span data-stu-id="c70da-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c70da-104">語法</span><span class="sxs-lookup"><span data-stu-id="c70da-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c70da-105">參數</span><span class="sxs-lookup"><span data-stu-id="c70da-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="c70da-106">[out]CorDebugRegister 列舉值，指出的位置類型的變數報名`VLT_REGISTER`，及基底的位置類型的變數報名`VLT_REGISTER_RELATIVE`。</span><span class="sxs-lookup"><span data-stu-id="c70da-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c70da-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="c70da-107">Return Value</span></span>  
 <span data-ttu-id="c70da-108">方法會傳回下列值：</span><span class="sxs-lookup"><span data-stu-id="c70da-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="c70da-109">值</span><span class="sxs-lookup"><span data-stu-id="c70da-109">Value</span></span>|<span data-ttu-id="c70da-110">描述</span><span class="sxs-lookup"><span data-stu-id="c70da-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="c70da-111">變數是在暫存器中所指示`pRegister`引數。</span><span class="sxs-lookup"><span data-stu-id="c70da-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="c70da-112">變數不是在暫存器或暫存器的相對位置。</span><span class="sxs-lookup"><span data-stu-id="c70da-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c70da-113">需求</span><span class="sxs-lookup"><span data-stu-id="c70da-113">Requirements</span></span>  
 <span data-ttu-id="c70da-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c70da-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c70da-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c70da-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c70da-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c70da-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c70da-117">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c70da-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c70da-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c70da-118">See also</span></span>

- [<span data-ttu-id="c70da-119">VariableLocationType 列舉</span><span class="sxs-lookup"><span data-stu-id="c70da-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
- [<span data-ttu-id="c70da-120">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="c70da-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
