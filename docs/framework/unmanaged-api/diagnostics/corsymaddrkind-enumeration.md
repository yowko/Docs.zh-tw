---
title: CorSymAddrKind 列舉
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
ms.openlocfilehash: 5991b0abaedabe2337cd754c7bd19f96c5e9b685
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420613"
---
# <a name="corsymaddrkind-enumeration"></a>CorSymAddrKind 列舉
表示記憶體位址的類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|表示 Microsoft 中繼語言（MSIL）本機變數或參數索引。|  
|`ADDR_NATIVE_RVA`|表示模組中的相對虛擬位址。|  
|`ADDR_NATIVE_REGISTER`|表示 CPU 暫存器。|  
|`ADDR_NATIVE_REGREL`|表示第一個位址是暫存器，而第二個位址是位移。|  
|`ADDR_NATIVE_OFFSET`|表示基底位址的位移。|  
|`ADDR_NATIVE_REGREG`|表示第一個位址是暫存器的低部分，而第二個位址是最高的部分。|  
|`ADDR_NATIVE_REGSTK`|表示第一個位址是暫存器的低部分，第二個是高部分，而第三個是位移。|  
|`ADDR_NATIVE_STKREG`|表示第一個位址是暫存器，第二個是位移，而第三個是註冊的最高部分。|  
|`ADDR_BITFIELD`|表示第一個位址是欄位的開頭，而第二個位址是欄位長度。|  
|`ADDR_NATIVE_ISECTOFFSET`|表示第一個位址是區段，而第二個位址是位移。|  
  
## <a name="requirements"></a>需求  
 **標頭：** CorSym .idl，CorSym。h  
  
## <a name="see-also"></a>另請參閱

- [診斷符號存放區列舉](diagnostics-symbol-store-enumerations.md)
