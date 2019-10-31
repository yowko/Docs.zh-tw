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
ms.openlocfilehash: f6abb59c3aaec40a4e7b228b8c69147a2d454431
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108874"
---
# <a name="create_asm_name_obj_flags-enumeration"></a><span data-ttu-id="2ebf3-102">CREATE_ASM_NAME_OBJ_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="2ebf3-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="2ebf3-103">指定[IAssemblyName 介面](iassemblyname-interface.md)物件的屬性（當[CreateAssemblyNameObject](createassemblynameobject-function.md)函數所建立時）。</span><span class="sxs-lookup"><span data-stu-id="2ebf3-103">Specifies the attributes of an [IAssemblyName Interface](iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ebf3-104">語法</span><span class="sxs-lookup"><span data-stu-id="2ebf3-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="2ebf3-105">Members</span><span class="sxs-lookup"><span data-stu-id="2ebf3-105">Members</span></span>  
  
|<span data-ttu-id="2ebf3-106">成員</span><span class="sxs-lookup"><span data-stu-id="2ebf3-106">Member</span></span>|<span data-ttu-id="2ebf3-107">描述</span><span class="sxs-lookup"><span data-stu-id="2ebf3-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="2ebf3-108">指出傳遞的參數是文字識別。</span><span class="sxs-lookup"><span data-stu-id="2ebf3-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="2ebf3-109">設定幾個預設值。</span><span class="sxs-lookup"><span data-stu-id="2ebf3-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="2ebf3-110">驗證 friend 元件規則（僅限名稱和公開金鑰）。</span><span class="sxs-lookup"><span data-stu-id="2ebf3-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="2ebf3-111">這個成員僅供內部使用。</span><span class="sxs-lookup"><span data-stu-id="2ebf3-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="2ebf3-112">`CANOF_PARSE_DISPLAY_NAME` 和 `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` 旗標的組合。</span><span class="sxs-lookup"><span data-stu-id="2ebf3-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="2ebf3-113">這個成員僅供內部使用。</span><span class="sxs-lookup"><span data-stu-id="2ebf3-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2ebf3-114">需求</span><span class="sxs-lookup"><span data-stu-id="2ebf3-114">Requirements</span></span>  
 <span data-ttu-id="2ebf3-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2ebf3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ebf3-116">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="2ebf3-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2ebf3-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ebf3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ebf3-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="2ebf3-118">See also</span></span>

- [<span data-ttu-id="2ebf3-119">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="2ebf3-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="2ebf3-120">CreateAssemblyNameObject 函式</span><span class="sxs-lookup"><span data-stu-id="2ebf3-120">CreateAssemblyNameObject Function</span></span>](createassemblynameobject-function.md)
- [<span data-ttu-id="2ebf3-121">融合列舉</span><span class="sxs-lookup"><span data-stu-id="2ebf3-121">Fusion Enumerations</span></span>](fusion-enumerations.md)
