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
# <a name="create_asm_name_obj_flags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS 列舉
指定[IAssemblyName 介面](iassemblyname-interface.md)物件的屬性（當[CreateAssemblyNameObject](createassemblynameobject-function.md)函數所建立時）。  
  
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
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|指出傳遞的參數是文字識別。|  
|`CANOF_SET_DEFAULT_VALUES`|設定幾個預設值。|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|驗證 friend 元件規則（僅限名稱和公開金鑰）。 這個成員僅供內部使用。|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|`CANOF_PARSE_DISPLAY_NAME` 和 `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` 旗標的組合。 這個成員僅供內部使用。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [IAssemblyName 介面](iassemblyname-interface.md)
- [CreateAssemblyNameObject 函式](createassemblynameobject-function.md)
- [融合列舉](fusion-enumerations.md)
