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
ms.openlocfilehash: 1c65efa006a8b2f4fb4db257b4ad2cde99c4e75e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725257"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="911fa-102">VariableLocationType 列舉</span><span class="sxs-lookup"><span data-stu-id="911fa-102">VariableLocationType Enumeration</span></span>

<span data-ttu-id="911fa-103">指出變數的原生位置型別。</span><span class="sxs-lookup"><span data-stu-id="911fa-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="911fa-104">語法</span><span class="sxs-lookup"><span data-stu-id="911fa-104">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="911fa-105">成員</span><span class="sxs-lookup"><span data-stu-id="911fa-105">Members</span></span>  
  
|<span data-ttu-id="911fa-106">member</span><span class="sxs-lookup"><span data-stu-id="911fa-106">Member</span></span>|<span data-ttu-id="911fa-107">描述</span><span class="sxs-lookup"><span data-stu-id="911fa-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="911fa-108">變數位於註冊中。</span><span class="sxs-lookup"><span data-stu-id="911fa-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="911fa-109">變數位於暫存器相對的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="911fa-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="911fa-110">變數不會儲存在暫存器或暫存器相對的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="911fa-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="911fa-111">備註</span><span class="sxs-lookup"><span data-stu-id="911fa-111">Remarks</span></span>  

 <span data-ttu-id="911fa-112">`VariableLocationType` [ICorDebugVariableHome：： GetLocationType](icordebugvariablehome-getlocationtype-method.md)方法會傳回列舉的成員。</span><span class="sxs-lookup"><span data-stu-id="911fa-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="911fa-113">需求</span><span class="sxs-lookup"><span data-stu-id="911fa-113">Requirements</span></span>  

 <span data-ttu-id="911fa-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="911fa-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="911fa-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="911fa-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="911fa-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="911fa-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="911fa-117">**.NET Framework 版本：**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="911fa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="911fa-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="911fa-118">See also</span></span>

- [<span data-ttu-id="911fa-119">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="911fa-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
