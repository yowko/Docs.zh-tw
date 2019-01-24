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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4da0e064f507e2330aac27fc5c8bcd56b9d3c1b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716228"
---
# <a name="createasmnameobjflags-enumeration"></a><span data-ttu-id="c1feb-102">CREATE_ASM_NAME_OBJ_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="c1feb-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="c1feb-103">指定的屬性[IAssemblyName 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件會藉由在建構時[CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="c1feb-103">Specifies the attributes of an [IAssemblyName Interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1feb-104">語法</span><span class="sxs-lookup"><span data-stu-id="c1feb-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="c1feb-105">成員</span><span class="sxs-lookup"><span data-stu-id="c1feb-105">Members</span></span>  
  
|<span data-ttu-id="c1feb-106">成員</span><span class="sxs-lookup"><span data-stu-id="c1feb-106">Member</span></span>|<span data-ttu-id="c1feb-107">描述</span><span class="sxs-lookup"><span data-stu-id="c1feb-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="c1feb-108">表示傳遞的參數是文字的身分識別。</span><span class="sxs-lookup"><span data-stu-id="c1feb-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="c1feb-109">設定一些預設值。</span><span class="sxs-lookup"><span data-stu-id="c1feb-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="c1feb-110">確認 friend 組件規則 （僅名稱和公開金鑰）。</span><span class="sxs-lookup"><span data-stu-id="c1feb-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="c1feb-111">這個成員是僅供內部使用。</span><span class="sxs-lookup"><span data-stu-id="c1feb-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="c1feb-112">組合`CANOF_PARSE_DISPLAY_NAME`和`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`旗標。</span><span class="sxs-lookup"><span data-stu-id="c1feb-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="c1feb-113">這個成員是僅供內部使用。</span><span class="sxs-lookup"><span data-stu-id="c1feb-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c1feb-114">需求</span><span class="sxs-lookup"><span data-stu-id="c1feb-114">Requirements</span></span>  
 <span data-ttu-id="c1feb-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c1feb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1feb-116">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="c1feb-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c1feb-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1feb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1feb-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1feb-118">See also</span></span>
- [<span data-ttu-id="c1feb-119">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="c1feb-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="c1feb-120">CreateAssemblyNameObject 函式</span><span class="sxs-lookup"><span data-stu-id="c1feb-120">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)
- [<span data-ttu-id="c1feb-121">融合列舉</span><span class="sxs-lookup"><span data-stu-id="c1feb-121">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
