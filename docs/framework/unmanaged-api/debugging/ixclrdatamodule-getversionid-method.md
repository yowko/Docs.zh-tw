---
title: IXCLRDataModule::GetVersionId 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e863f14676acc84f4d9f59d0898dee5b291bd30f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775436"
---
# <a name="ixclrdatamodulegetversionid-method"></a>IXCLRDataModule::GetVersionId 方法

取得模組的版本識別碼。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a>參數

`vid`\
[out]模組的版本識別碼。

## <a name="remarks"></a>備註

提供的方法是一部分`IXCLRDataModule`介面，並對應至的虛擬方法表 40 的位置。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** None  
**LIBRARY:** None  
**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [IXCLRDataModule 介面](ixclrdatamodule-interface.md)