---
title: ComNetOS 類別（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ComNetOS
- System.Net.ComNetOS.IsWin7orLater
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ed2b970d07df2c338870b386e75c1688703f1d68
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990343"
---
# <a name="comnetos-class"></a>ComNetOS 類別

提供目前作業系統的相關資訊，例如其版本和安裝類型（用戶端或伺服器）。 這個類別無法被繼承。
  
```csharp  
internal static class ComNetOS
```

> [!WARNING]
> 這個類別是內部的，不適合直接在程式碼中使用。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。

## <a name="iswin7orlater-field"></a>IsWin7orLater 欄位

指定作業系統版本是否為 Windows 7 或更新版本。

```csharp
internal static readonly bool IsWin7orLater
```

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Net>

**元件：** 系統（在 System.dll 中）
