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
ms.openlocfilehash: ca7c7570aff63aa328dddc0626648fa74397addc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448730"
---
# <a name="enumimporttypes-method"></a>EnumImportTypes 方法

列舉每個範圍中的每個類型。

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
列舉值的控制碼。

`dwMax`\
要取出的類型數目上限。

`aTypeDefs`\
接收類型標記，而不是超過 `dwMax`。

`pdwCount`\
在 `aTypeDefs`中，接收類型的實際數目。

## <a name="return-value"></a>傳回值

如果方法成功，則傳回 S_OK。

## <a name="requirements"></a>需求

需要 alink. h

## <a name="see-also"></a>另請參閱

- [IALink 介面](ialink-interface.md)
- [IALink2 介面](ialink2-interface.md)
- [ALink API](index.md)
