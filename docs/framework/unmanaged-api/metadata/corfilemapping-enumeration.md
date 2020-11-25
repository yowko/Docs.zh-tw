---
title: CorFileMapping 列舉
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
ms.openlocfilehash: 63e27a62e176a92b03c10b59a55d9da3192918f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726111"
---
# <a name="corfilemapping-enumeration"></a>CorFileMapping 列舉

包含值，這些值會描述從 [IMetaDataInfo：： GetFileMapping](imetadatainfo-getfilemapping-method.md) 方法的呼叫所傳回的檔案對應類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`fmFlat`|檔案會對應為資料檔案。 也就是說，旗標 `SEC_IMAGE` 未傳遞至 Microsoft Win32 `CreateFileMapping` 函數。|  
|`fmExecutableImage`|使用函式 `LoadLibrary` 或具有旗標的函式，以對應檔案來執行 `CreateFileMapping` `SEC_IMAGE` 。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
- [GetFileMapping 方法](imetadatainfo-getfilemapping-method.md)
