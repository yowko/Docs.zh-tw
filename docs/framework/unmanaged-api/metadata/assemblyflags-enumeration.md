---
title: AssemblyFlags 列舉
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
ms.openlocfilehash: 561b4d68a574a2859286fb5f2e2d950518a9d29d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732771"
---
# <a name="assemblyflags-enumeration"></a>AssemblyFlags 列舉

包含值，這些值會描述元件的執行時間功能。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`afImplicitExportedTypes`|指定匯出的型別定義在組成元件的檔案內是隱含的。 在 .NET Framework 1.0 和1.1 版中，一律會假設設定這個值。|  
|`afImplicitResources`|指定資源定義在組成元件的檔案內是隱含的。 在 .NET Framework 1.0 和1.1 中，一律會假設設定這個值。|  
|`afNonSideBySideAppDomain`|指定元件在相同的應用程式域中執行時，無法與其他版本一起執行。|  
|`afNonSideBySideProcess`|指定當元件在相同的進程中執行時，無法與其他版本一起執行。|  
|`afNonSideBySideMachine`|指定元件在同一部電腦上執行時，無法與其他版本一起執行。|  
  
## <a name="remarks"></a>備註  

 0x0010 和0x0070 （含）之間的值是用來描述參考元件的並存相容性功能。 如果未設定這些值，則會假設元件並存相容。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
- [IMetaDataAssemblyEmit 介面](imetadataassemblyemit-interface.md)
