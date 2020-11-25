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
ms.openlocfilehash: 7f912f4b13620b567f5aa097604e98112d85f02d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711750"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="69304-102">ICorDebugVariableHome：： GetRegister 方法</span><span class="sxs-lookup"><span data-stu-id="69304-102">ICorDebugVariableHome::GetRegister Method</span></span>

<span data-ttu-id="69304-103">取得暫存器，其中包含位置類型為的變數 `VLT_REGISTER` ，以及位置類型為之變數的基底暫存器 `VLT_REGISTER_RELATIVE` 。</span><span class="sxs-lookup"><span data-stu-id="69304-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69304-104">語法</span><span class="sxs-lookup"><span data-stu-id="69304-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69304-105">參數</span><span class="sxs-lookup"><span data-stu-id="69304-105">Parameters</span></span>  

 `pRegister`  
 <span data-ttu-id="69304-106">擴展CorDebugRegister 列舉值，這個值會指出的位置型別為之變數的註冊 `VLT_REGISTER` ，以及位置型別為之變數的基底暫存器 `VLT_REGISTER_RELATIVE` 。</span><span class="sxs-lookup"><span data-stu-id="69304-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69304-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="69304-107">Return Value</span></span>  

 <span data-ttu-id="69304-108">方法會傳回下列值：</span><span class="sxs-lookup"><span data-stu-id="69304-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="69304-109">值</span><span class="sxs-lookup"><span data-stu-id="69304-109">Value</span></span>|<span data-ttu-id="69304-110">描述</span><span class="sxs-lookup"><span data-stu-id="69304-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="69304-111">變數位於引數所指示的暫存器中 `pRegister` 。</span><span class="sxs-lookup"><span data-stu-id="69304-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="69304-112">變數不在暫存器或暫存器的相對位置。</span><span class="sxs-lookup"><span data-stu-id="69304-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="69304-113">需求</span><span class="sxs-lookup"><span data-stu-id="69304-113">Requirements</span></span>  

 <span data-ttu-id="69304-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="69304-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69304-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69304-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69304-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69304-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69304-117">**.NET Framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69304-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69304-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69304-118">See also</span></span>

- [<span data-ttu-id="69304-119">VariableLocationType 列舉</span><span class="sxs-lookup"><span data-stu-id="69304-119">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
- [<span data-ttu-id="69304-120">ICorDebugVariableHome 介面</span><span class="sxs-lookup"><span data-stu-id="69304-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
