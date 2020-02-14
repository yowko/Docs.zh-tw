---
title: BodyToString 方法（System.servicemodel. 通道）
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 9f1f852c0bd82299fd40afe66a5f90cd7c0335cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215498"
---
# <a name="messagebodytostring-method"></a>BodyToString 方法

藉由呼叫 <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> 方法，將訊息本文轉換成字串。

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a>參數

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  用來將訊息主體轉換成字串的寫入器。

## <a name="remarks"></a>備註

> [!WARNING]
> `Message.BodyToString` 方法是內部的，而且不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.ServiceModel.Channels>

**元件：** System.servicemodel .dll

**.NET Framework 版本：** 自3.0 開始提供。
