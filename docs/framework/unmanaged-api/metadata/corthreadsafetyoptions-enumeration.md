---
title: CorThreadSafetyOptions 列舉
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
ms.openlocfilehash: 8c0527a7bc3cde7344bf809dc8e6f5a3fac04852
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007503"
---
# <a name="corthreadsafetyoptions-enumeration"></a>CorThreadSafetyOptions 列舉

指定旗標，以選取執行緒安全的選項。

## <a name="syntax"></a>語法

```cpp
typedef enum CorThreadSafetyOptions {
    MDThreadSafetyDefault       = 0x00000000,
    MDThreadSafetyOff           = 0x00000000,
    MDThreadSafetyOn            = 0x00000001,
} CorThreadSafetyOptions;
```

## <a name="members"></a>成員

|成員|描述|
|------------|-----------------|
|`MDThreadSafetyDefault`|預設值。 與 `MDThreadSafetyOff` 相同。|
|`MDThreadSafetyOff`|表示無法設定讀取器/寫入器鎖定。|
|`MDThreadSafetyOn`|表示可以設定讀取器/寫入器鎖定。|

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** Corhdr.h。h

**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>另請參閱

- [中繼資料列舉](metadata-enumerations.md)
