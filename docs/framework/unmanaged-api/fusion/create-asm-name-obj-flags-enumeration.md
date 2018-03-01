---
title: "CREATE_ASM_NAME_OBJ_FLAGS 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 61e9bea623e38b1416721773d8739bc6e6748909
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="createasmnameobjflags-enumeration"></a><span data-ttu-id="0ad81-102">CREATE_ASM_NAME_OBJ_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="0ad81-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="0ad81-103">指定的屬性[IAssemblyName 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件來建構時[CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="0ad81-103">Specifies the attributes of an [IAssemblyName Interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ad81-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ad81-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="0ad81-105">成員</span><span class="sxs-lookup"><span data-stu-id="0ad81-105">Members</span></span>  
  
|<span data-ttu-id="0ad81-106">成員</span><span class="sxs-lookup"><span data-stu-id="0ad81-106">Member</span></span>|<span data-ttu-id="0ad81-107">描述</span><span class="sxs-lookup"><span data-stu-id="0ad81-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="0ad81-108">表示傳遞的參數為文字的識別。</span><span class="sxs-lookup"><span data-stu-id="0ad81-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="0ad81-109">設定一些預設值。</span><span class="sxs-lookup"><span data-stu-id="0ad81-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="0ad81-110">確認 friend 組件規則 （僅名稱和公開金鑰）。</span><span class="sxs-lookup"><span data-stu-id="0ad81-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="0ad81-111">這個成員是僅供內部使用。</span><span class="sxs-lookup"><span data-stu-id="0ad81-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="0ad81-112">組合`CANOF_PARSE_DISPLAY_NAME`和`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`旗標。</span><span class="sxs-lookup"><span data-stu-id="0ad81-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="0ad81-113">這個成員是僅供內部使用。</span><span class="sxs-lookup"><span data-stu-id="0ad81-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0ad81-114">需求</span><span class="sxs-lookup"><span data-stu-id="0ad81-114">Requirements</span></span>  
 <span data-ttu-id="0ad81-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ad81-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ad81-116">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="0ad81-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0ad81-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ad81-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ad81-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="0ad81-118">See Also</span></span>  
 [<span data-ttu-id="0ad81-119">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="0ad81-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="0ad81-120">CreateAssemblyNameObject 函式</span><span class="sxs-lookup"><span data-stu-id="0ad81-120">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 [<span data-ttu-id="0ad81-121">融合列舉</span><span class="sxs-lookup"><span data-stu-id="0ad81-121">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
