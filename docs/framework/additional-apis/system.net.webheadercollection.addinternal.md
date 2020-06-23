---
title: WebHeaderCollection. AddInternal 方法（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.WebHeaderCollection.AddInternal
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fd7b13ccd1baad48ab99a85d80ccd6154651c608
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990306"
---
# <a name="webheadercollectionaddinternal-method"></a>WebHeaderCollection. AddInternal 方法

將具有指定之名稱和值的新標頭加入至集合，略過檢查。

```csharp
internal void AddInternal(string name, string value)
```

> [!WARNING]
> 這個方法是內部的，不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。

## <a name="parameters"></a>參數

- `name` <xref:System.String>

  標頭的名稱。

- `value` <xref:System.String>

  標頭的值。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Net>

**元件：** 系統（在 System.dll 中）
