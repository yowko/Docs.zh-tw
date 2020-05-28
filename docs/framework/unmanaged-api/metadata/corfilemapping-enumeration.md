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
ms.openlocfilehash: 0ed1579886f1682348a136be3391f6bdc2543d26
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007386"
---
# <a name="corfilemapping-enumeration"></a>CorFileMapping 列舉
包含值，描述從[IMetaDataInfo：： GetFileMapping](imetadatainfo-getfilemapping-method.md)方法的呼叫所傳回的檔對應類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`fmFlat`|檔案會對應為資料檔案。 也就是說，旗標 `SEC_IMAGE` 不會傳遞至 Microsoft Win32 `CreateFileMapping` 函數。|  
|`fmExecutableImage`|檔案會對應執行，方法是使用函式 `LoadLibrary` 或 `CreateFileMapping` 函數搭配旗標 `SEC_IMAGE` 。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
- [GetFileMapping 方法](imetadatainfo-getfilemapping-method.md)
