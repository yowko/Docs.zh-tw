---
title: CorMethodAttr 列舉
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
ms.openlocfilehash: 6c3e721c24da217eaf2e8857377359e1c51b7b59
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677007"
---
# <a name="cormethodattr-enumeration"></a>CorMethodAttr 列舉

包含描述方法功能的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`mdMemberAccessMask`|指定成員存取權。|  
|`mdPrivateScope`|指定無法參考成員。|  
|`mdPrivate`|指定成員只能由父類型存取。|  
|`mdFamANDAssem`|指定只有這個元件中的子類型可以存取該成員。|  
|`mdAssem`|指定由元件中的任何人存取然後順著成員。|  
|`mdFamily`|指定成員只能透過類型和子類型存取。|  
|`mdFamORAssem`|指定成員可由衍生類別以及其元件中的其他類型存取。|  
|`mdPublic`|指定成員可供具有範圍存取權的所有類型存取。|  
|`mdStatic`|指定將成員定義為類型的一部分，而不是實例的成員。|  
|`mdFinal`|指定無法覆寫方法。|  
|`mdVirtual`|指定可以覆寫方法。|  
|`mdHideBySig`|指定方法依名稱和簽章隱藏，而不只是依名稱。|  
|`mdVtableLayoutMask`|指定虛擬資料表版面配置。|  
|`mdReuseSlot`|指定要在虛擬資料表中重複使用這個方法所使用的位置。 此為預設值。|  
|`mdNewSlot`|指定方法一律取得虛擬資料表中的新位置。|  
|`mdCheckAccessOnOverride`|指定方法可由可見的相同類型覆寫。|  
|`mdAbstract`|指定不執行方法。|  
|`mdSpecialName`|指定方法為特殊方法，且其名稱會描述如何。|  
|`mdPinvokeImpl`|指定使用 PInvoke 轉送方法執行。|  
|`mdUnmanagedExport`|指定方法是匯出至非受控碼的 managed 方法。|  
|`mdReservedMask`|保留給 common language runtime 內部使用。|  
|`mdRTSpecialName`|指定 common language runtime 應該檢查方法名稱的編碼方式。|  
|`mdHasSecurity`|指定方法具有與其相關聯的安全性。|  
|`mdRequireSecObject`|指定方法呼叫另一個包含安全程式碼的方法。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
