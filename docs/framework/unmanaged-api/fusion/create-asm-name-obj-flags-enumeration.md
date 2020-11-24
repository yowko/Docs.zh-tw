---
title: CREATE_ASM_NAME_OBJ_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- CREATE_ASM_NAME_OBJ_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type:
- apiref
ms.openlocfilehash: 52d5ad3a18c102422e90621c7d1e23b2692c0000
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683224"
---
# <a name="create_asm_name_obj_flags-enumeration"></a><span data-ttu-id="02eee-102">CREATE_ASM_NAME_OBJ_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="02eee-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>

<span data-ttu-id="02eee-103">指定 [IAssemblyName 介面](iassemblyname-interface.md) 物件在由 [CreateAssemblyNameObject](createassemblynameobject-function.md) 函數所建立時的屬性。</span><span class="sxs-lookup"><span data-stu-id="02eee-103">Specifies the attributes of an [IAssemblyName Interface](iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02eee-104">語法</span><span class="sxs-lookup"><span data-stu-id="02eee-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="02eee-105">成員</span><span class="sxs-lookup"><span data-stu-id="02eee-105">Members</span></span>  
  
|<span data-ttu-id="02eee-106">member</span><span class="sxs-lookup"><span data-stu-id="02eee-106">Member</span></span>|<span data-ttu-id="02eee-107">描述</span><span class="sxs-lookup"><span data-stu-id="02eee-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="02eee-108">指出傳遞的參數是文字身分識別。</span><span class="sxs-lookup"><span data-stu-id="02eee-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="02eee-109">設定一些預設值。</span><span class="sxs-lookup"><span data-stu-id="02eee-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="02eee-110">驗證 friend 元件規則只 (名稱和公開金鑰) 。</span><span class="sxs-lookup"><span data-stu-id="02eee-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="02eee-111">此成員僅供內部使用。</span><span class="sxs-lookup"><span data-stu-id="02eee-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="02eee-112">`CANOF_PARSE_DISPLAY_NAME`和旗標的組合 `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` 。</span><span class="sxs-lookup"><span data-stu-id="02eee-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="02eee-113">此成員僅供內部使用。</span><span class="sxs-lookup"><span data-stu-id="02eee-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="02eee-114">需求</span><span class="sxs-lookup"><span data-stu-id="02eee-114">Requirements</span></span>  

 <span data-ttu-id="02eee-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02eee-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02eee-116">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="02eee-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="02eee-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02eee-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02eee-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02eee-118">See also</span></span>

- [<span data-ttu-id="02eee-119">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="02eee-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="02eee-120">CreateAssemblyNameObject 函式</span><span class="sxs-lookup"><span data-stu-id="02eee-120">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)
- [<span data-ttu-id="02eee-121">融合列舉</span><span class="sxs-lookup"><span data-stu-id="02eee-121">Fusion Enumerations</span></span>](fusion-enumerations.md)
