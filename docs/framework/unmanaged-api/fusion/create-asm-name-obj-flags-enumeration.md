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
ms.openlocfilehash: aebc6dfe4830e6477cda8fd279b8ef2a8040895c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149665"
---
# <a name="createasmnameobjflags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS 列舉
指定的屬性[IAssemblyName 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)物件會藉由在建構時[CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)函式。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|表示傳遞的參數是文字的身分識別。|  
|`CANOF_SET_DEFAULT_VALUES`|設定一些預設值。|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|確認 friend 組件規則 （僅名稱和公開金鑰）。 這個成員是僅供內部使用。|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|組合`CANOF_PARSE_DISPLAY_NAME`和`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`旗標。 這個成員是僅供內部使用。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Fusion.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IAssemblyName 介面](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [CreateAssemblyNameObject 函式](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)
- [融合列舉](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
