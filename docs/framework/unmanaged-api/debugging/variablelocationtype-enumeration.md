---
title: VariableLocationType 列舉
ms.date: 03/30/2017
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
ms.openlocfilehash: e2fa5d5a998f51e0e90cfde22b40ec12f278307b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178354"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="b07d4-102">VariableLocationType 列舉</span><span class="sxs-lookup"><span data-stu-id="b07d4-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="b07d4-103">指示變數的本機位置類型。</span><span class="sxs-lookup"><span data-stu-id="b07d4-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b07d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="b07d4-104">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="b07d4-105">成員</span><span class="sxs-lookup"><span data-stu-id="b07d4-105">Members</span></span>  
  
|<span data-ttu-id="b07d4-106">member</span><span class="sxs-lookup"><span data-stu-id="b07d4-106">Member</span></span>|<span data-ttu-id="b07d4-107">描述</span><span class="sxs-lookup"><span data-stu-id="b07d4-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="b07d4-108">變數在寄存器中。</span><span class="sxs-lookup"><span data-stu-id="b07d4-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="b07d4-109">變數位於寄存器相對記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="b07d4-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="b07d4-110">變數不存儲在寄存器或寄存器相對記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="b07d4-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b07d4-111">備註</span><span class="sxs-lookup"><span data-stu-id="b07d4-111">Remarks</span></span>  
 <span data-ttu-id="b07d4-112">枚舉的成員`VariableLocationType`由[ICorDebugvariableHome：：獲取定位類型](icordebugvariablehome-getlocationtype-method.md)方法返回。</span><span class="sxs-lookup"><span data-stu-id="b07d4-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b07d4-113">需求</span><span class="sxs-lookup"><span data-stu-id="b07d4-113">Requirements</span></span>  
 <span data-ttu-id="b07d4-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b07d4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b07d4-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b07d4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b07d4-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b07d4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b07d4-117">**.NET 框架版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b07d4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b07d4-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b07d4-118">See also</span></span>

- [<span data-ttu-id="b07d4-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="b07d4-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
