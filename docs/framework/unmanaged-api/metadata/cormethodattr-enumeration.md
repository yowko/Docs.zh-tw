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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f144426996583d5058f70daed99d8a37cfb6bfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cormethodattr-enumeration"></a>CorMethodAttr 列舉
包含值描述方法的功能。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
|成員|描述|  
|------------|-----------------|  
|`mdMemberAccessMask`|指定成員存取。|  
|`mdPrivateScope`|指定成員不能參考。|  
|`mdPrivate`|指定成員可存取只能由父型別。|  
|`mdFamANDAssem`|指定成員可存取由子型別只能在這個組件中。|  
|`mdAssem`|指定組件中的任何人都可以存取此成員。|  
|`mdFamily`|指定成員可存取只要類型與子類型。|  
|`mdFamORAssem`|指定成員可存取衍生的類別和其組件中的其他型別。|  
|`mdPublic`|指定成員可存取的所有型別存取範圍。|  
|`mdStatic`|指定此成員定義為之型別的一部分，而不是執行個體的成員。|  
|`mdFinal`|指定無法覆寫此方法。|  
|`mdVirtual`|指定可以覆寫此方法。|  
|`mdHideBySig`|指定的方法會隱藏由名稱和簽章，而不是只根據名稱。|  
|`mdVtableLayoutMask`|指定虛擬資料表配置。|  
|`mdReuseSlot`|指定用於虛擬資料表中，這個方法的位置可重複使用。 這是預設值。|  
|`mdNewSlot`|指定方法一律會取得虛擬資料表中的新位置。|  
|`mdCheckAccessOnOverride`|指定可以在相同的類型，它會顯示所覆寫方法。|  
|`mdAbstract`|指定方法未實作。|  
|`mdSpecialName`|指定的方法是特殊的且其名稱描述如何。|  
|`mdPinvokeImpl`|指定使用 PInvoke 轉送方法實作。|  
|`mdUnmanagedExport`|指定的方法是匯出至 unmanaged 程式碼的 managed 的方法。|  
|`mdReservedMask`|保留供內部使用的 common language runtime。|  
|`mdRTSpecialName`|指定通用語言執行平台應該檢查方法名稱的編碼方式。|  
|`mdHasSecurity`|指定的方法有與其相關聯的安全性。|  
|`mdRequireSecObject`|指定此方法會呼叫包含安全性驗證碼的另一個方法。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
