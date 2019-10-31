---
title: ICorDebugVariableHome：： GetRegister 方法
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
ms.openlocfilehash: 4c9932c3eeebd0101ee364c9b4d0b0a26862c4b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125065"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="69c67-102">ICorDebugVariableHome：： GetRegister 方法</span><span class="sxs-lookup"><span data-stu-id="69c67-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="69c67-103">取得包含 `VLT_REGISTER`之位置類型之變數的暫存器，以及具有 `VLT_REGISTER_RELATIVE`位置類型之變數的基底暫存器。</span><span class="sxs-lookup"><span data-stu-id="69c67-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69c67-104">語法</span><span class="sxs-lookup"><span data-stu-id="69c67-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69c67-105">參數</span><span class="sxs-lookup"><span data-stu-id="69c67-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="69c67-106">脫銷CorDebugRegister 列舉值，指出位置類型為 `VLT_REGISTER`之變數的暫存器，以及位置類型為 `VLT_REGISTER_RELATIVE`之變數的基底暫存器。</span><span class="sxs-lookup"><span data-stu-id="69c67-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69c67-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="69c67-107">Return Value</span></span>  
 <span data-ttu-id="69c67-108">方法會傳回下列值：</span><span class="sxs-lookup"><span data-stu-id="69c67-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="69c67-109">值</span><span class="sxs-lookup"><span data-stu-id="69c67-109">Value</span></span>|<span data-ttu-id="69c67-110">描述</span><span class="sxs-lookup"><span data-stu-id="69c67-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="69c67-111">變數位於 `pRegister` 引數所指示的暫存器中。</span><span class="sxs-lookup"><span data-stu-id="69c67-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="69c67-112">變數不在暫存器或暫存器相對位置。</span><span class="sxs-lookup"><span data-stu-id="69c67-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="69c67-113">需求</span><span class="sxs-lookup"><span data-stu-id="69c67-113">Requirements</span></span>  
 <span data-ttu-id="69c67-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="69c67-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69c67-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69c67-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69c67-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69c67-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69c67-117">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69c67-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69c67-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="69c67-118">See also</span></span>

- [<span data-ttu-id="69c67-119">VariableLocationType 列舉</span><span class="sxs-lookup"><span data-stu-id="69c67-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
- [<span data-ttu-id="69c67-120">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="69c67-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
