---
title: IAssemblyCacheItem::CreateStream 方法
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
ms.openlocfilehash: 0660621f465f2ba3610e06bd1df38baa1bc5c907
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134477"
---
# <a name="iassemblycacheitemcreatestream-method"></a>IAssemblyCacheItem::CreateStream 方法

建立具有指定之名稱和格式的資料流程。

## <a name="syntax"></a>語法

```cpp
HRESULT CreateStream (
    [in]  DWORD dwFlags,
    [in]  LPCWSTR pszStreamName,
    [in]  DWORD dwFormat,
    [in]  DWORD dwFormatFlags,
    [out] IStream **ppIStream,
    [in, optional] ULARGE_INTEGER *puliMaxSize
);
```

## <a name="parameters"></a>參數

`dwFlags`\
在在融合 .idl 中定義的旗標。

`pszStreamName`\
在要建立之資料流程的名稱。

`dwFormat`\
在要進行資料流程處理之檔案的格式。

`dwFormatFlags`\
在在融合 .idl 中定義的格式特定旗標。

`ppIStream`\
脫銷傳回之[IStream](/windows/desktop/api/objidl/nn-objidl-istream)實例位址的指標。

`puliMaxSize`\
[in，optional]`ppIStream`所參考的資料流程大小上限。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** 融合。h

**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>請參閱

- [IAssemblyCacheItem 介面](iassemblycacheitem-interface.md)
