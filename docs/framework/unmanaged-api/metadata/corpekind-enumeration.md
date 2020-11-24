---
title: CorPEKind 列舉
ms.date: 03/30/2017
api_name:
- CorPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPEKind
helpviewer_keywords:
- CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type:
- apiref
ms.openlocfilehash: 001be0c5e8897bacf76d2a044fb9400768473052
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673523"
---
# <a name="corpekind-enumeration"></a>CorPEKind 列舉

包含值，這些值描述從 [IMetaDataImport2：： GetPEKind](imetadataimport2-getpekind-method.md)呼叫傳回的可攜式可執行檔 (PE) 檔。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`peNot`|指出這不是 PE 檔。|  
|`peILOnly`|指出此 PE 檔案僅包含 managed 程式碼。|  
|`pe32BitRequired`|指出此 PE 檔案會進行 Win32 呼叫。|  
|`pe32Plus`|指出此 PE 檔會在64位平臺上執行。|  
|`pe32Unmanaged`|指出此 PE 檔案為機器碼。|  
|pe32BitPreferred|指出此 PE 檔案是平臺中立的，且偏好在32位環境中載入。|  
  
## <a name="remarks"></a>備註  

 這些值可用於位組合。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Corhdr.h。h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
