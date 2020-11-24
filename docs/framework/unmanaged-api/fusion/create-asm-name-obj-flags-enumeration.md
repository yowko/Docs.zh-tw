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
# <a name="create_asm_name_obj_flags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS 列舉

指定 [IAssemblyName 介面](iassemblyname-interface.md) 物件在由 [CreateAssemblyNameObject](createassemblynameobject-function.md) 函數所建立時的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|指出傳遞的參數是文字身分識別。|  
|`CANOF_SET_DEFAULT_VALUES`|設定一些預設值。|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|驗證 friend 元件規則只 (名稱和公開金鑰) 。 此成員僅供內部使用。|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|`CANOF_PARSE_DISPLAY_NAME`和旗標的組合 `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` 。 此成員僅供內部使用。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IAssemblyName 介面](iassemblyname-interface.md)
- [CreateAssemblyNameObject 函式](createassemblynameobject-function.md)
- [融合列舉](fusion-enumerations.md)
