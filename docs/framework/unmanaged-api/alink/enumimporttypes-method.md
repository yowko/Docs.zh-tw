---
title: EnumImportTypes 方法
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d0aefea7345bc3bf37bdb8d13cb2cda19cfe527
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789951"
---
# <a name="enumimporttypes-method"></a>EnumImportTypes 方法

列舉每個範圍中的每個型別。

## <a name="syntax"></a>語法

```cpp
HRESULT EnumImportTypes(
    HALINKENUM   hEnum,
    DWORD        dwMax,
    mdTypeDef    aTypeDefs[],
    DWORD*       pdwCount
) PURE;
```

## <a name="parameters"></a>參數

`hEnum`\
列舉值的控制代碼。

`dwMax`\
擷取類型的最大數目。

`aTypeDefs`\
接收類型的語彙基元，不能超過`dwMax`。

`pdwCount`\
接收輸入的實際數目`aTypeDefs`。

## <a name="return-value"></a>傳回值

如果方法成功，則會傳回 S_OK。

## <a name="requirements"></a>需求

需要 alink.h

## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)