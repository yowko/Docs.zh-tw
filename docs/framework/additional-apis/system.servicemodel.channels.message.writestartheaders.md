---
title: WriteStartHeaders 方法（System.servicemodel. 通道）
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.WriteStartHeaders
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: c826e6a3b976e5705e9815586441e8a25b64f76e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214870"
---
# <a name="messagewritestartheaders-method"></a>WriteStartHeaders 方法

藉由呼叫 <xref:System.ServiceModel.Channels.Message.OnWriteStartHeaders%2A?displayProperty=nameWithType> 方法，將開始標頭寫入至 XML 檔案。

```csharp
internal void WriteStartHeaders(XmlDictionaryWriter writer)
```

## <a name="parameters"></a>參數

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  用來將開始標頭寫入 XML 檔案的寫入器。

## <a name="remarks"></a>備註

> [!WARNING]
> `Message.WriteStartHeaders` 方法是內部的，而且不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.ServiceModel.Channels>

**元件：** System.servicemodel .dll

**.NET Framework 版本：** 自3.0 開始提供。
