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
ms.openlocfilehash: 396dd9c017fca6dc7037b43355ba7f726d7390ea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790981"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="abaf4-102">ICorDebugVariableHome：： GetRegister 方法</span><span class="sxs-lookup"><span data-stu-id="abaf4-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="abaf4-103">取得包含 `VLT_REGISTER`之位置類型之變數的暫存器，以及具有 `VLT_REGISTER_RELATIVE`位置類型之變數的基底暫存器。</span><span class="sxs-lookup"><span data-stu-id="abaf4-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abaf4-104">語法</span><span class="sxs-lookup"><span data-stu-id="abaf4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abaf4-105">參數</span><span class="sxs-lookup"><span data-stu-id="abaf4-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="abaf4-106">脫銷CorDebugRegister 列舉值，指出位置類型為 `VLT_REGISTER`之變數的暫存器，以及位置類型為 `VLT_REGISTER_RELATIVE`之變數的基底暫存器。</span><span class="sxs-lookup"><span data-stu-id="abaf4-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abaf4-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="abaf4-107">Return Value</span></span>  
 <span data-ttu-id="abaf4-108">方法會傳回下列值：</span><span class="sxs-lookup"><span data-stu-id="abaf4-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="abaf4-109">{2&gt;值&lt;2}</span><span class="sxs-lookup"><span data-stu-id="abaf4-109">Value</span></span>|<span data-ttu-id="abaf4-110">描述</span><span class="sxs-lookup"><span data-stu-id="abaf4-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="abaf4-111">變數位於 `pRegister` 引數所指示的暫存器中。</span><span class="sxs-lookup"><span data-stu-id="abaf4-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="abaf4-112">變數不在暫存器或暫存器相對位置。</span><span class="sxs-lookup"><span data-stu-id="abaf4-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="abaf4-113">需求</span><span class="sxs-lookup"><span data-stu-id="abaf4-113">Requirements</span></span>  
 <span data-ttu-id="abaf4-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abaf4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abaf4-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abaf4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abaf4-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abaf4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abaf4-117">**.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abaf4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abaf4-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="abaf4-118">See also</span></span>

- [<span data-ttu-id="abaf4-119">VariableLocationType 列舉</span><span class="sxs-lookup"><span data-stu-id="abaf4-119">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
- [<span data-ttu-id="abaf4-120">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="abaf4-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
