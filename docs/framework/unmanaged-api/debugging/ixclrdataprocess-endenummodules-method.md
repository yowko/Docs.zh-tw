---
title: IXCLRDataProcess::EndEnumModules 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: de30384b4c12c4fcac3eafe580484685f8a43fa4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775423"
---
# <a name="ixclrdataprocessendenummodules-method"></a>IXCLRDataProcess::EndEnumModules 方法

釋出內部模組列舉期間使用的迭代器所使用的資源。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a>參數

`handle`\
[out]列舉模組控制代碼。

## <a name="remarks"></a>備註

提供的方法是一部分`IXCLRDataProcess`介面，並對應至的虛擬方法表 26 的位置。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。
**標頭：** 無**程式庫：** 無 **.NET Framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [IXCLRDataProcess 介面](ixclrdataprocess-interface.md)
