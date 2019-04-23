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
ms.openlocfilehash: 249de91483117db6b497fa8eae6f97c3eb0a0587
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176991"
---
# <a name="cormethodattr-enumeration"></a>CorMethodAttr 列舉
包含描述方法的功能值。  
  
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
|`mdPrivate`|指定成員只能由父型別存取。|  
|`mdFamANDAssem`|指定成員可存取由子型別只能在這個組件中。|  
|`mdAssem`|指定組件中的任何人都可以存取此成員。|  
|`mdFamily`|指定成員只能由型別和子型別存取。|  
|`mdFamORAssem`|指定成員可存取由衍生的類別和其組件中的其他型別。|  
|`mdPublic`|指定成員為可存取的所有型別存取範圍。|  
|`mdStatic`|指定此成員定義為類型的一部分，而不是執行個體的成員。|  
|`mdFinal`|指定無法覆寫此方法。|  
|`mdVirtual`|指定可以覆寫此方法。|  
|`mdHideBySig`|指定的方法會在依名稱和簽章，而不是只依名稱隱藏。|  
|`mdVtableLayoutMask`|指定虛擬資料表配置。|  
|`mdReuseSlot`|指定用於虛擬資料表中，這個方法的位置可重複使用。 這是預設值。|  
|`mdNewSlot`|指定此方法一律會取得虛擬資料表中的新位置。|  
|`mdCheckAccessOnOverride`|指定可以在相同的型別，它會顯示所覆寫此方法。|  
|`mdAbstract`|指定的方法尚未實作。|  
|`mdSpecialName`|指定的方法是特殊的且其名稱描述方式。|  
|`mdPinvokeImpl`|指定方法實作會轉送使用 PInvoke。|  
|`mdUnmanagedExport`|指定的方法是匯出至 unmanaged 程式碼的 managed 的方法。|  
|`mdReservedMask`|保留供內部使用的 common language runtime。|  
|`mdRTSpecialName`|指定 common language runtime 應該檢查方法名稱的編碼方式。|  
|`mdHasSecurity`|指定的方法具有與它相關聯的安全性。|  
|`mdRequireSecObject`|指定此方法會呼叫含有安全程式碼的另一種方法。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorHdr.h  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
