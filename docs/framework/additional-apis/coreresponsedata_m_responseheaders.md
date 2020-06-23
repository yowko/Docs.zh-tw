---
title: CoreResponseData。 m_ResponseHeaders] 欄位
description: 瞭解 .NET 中的 m_ResponseHeaders CoreResponseData 欄位。 此欄位是 WebHeaderCollection 類型，具有與伺服器回應相關聯的標頭。
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_ResponseHeaders
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 7c7b896193cb81e9fc9e3ec28110359003a36728
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989793"
---
# <a name="coreresponsedatam_responseheaders-field"></a>CoreResponseData. m \_ ResponseHeaders 欄位

`CoreResponseData.m_ResponseHeaders`這是 <xref:System.Net.WebHeaderCollection> 與伺服器回應相關聯的標頭。

## <a name="syntax"></a>Syntax
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> 此 API 不適合直接在您的程式碼中使用。 相反地，您應該使用 <xref:System.Diagnostics.DiagnosticSource> 來攔截網路程式碼。 請參閱[DiagnosticSource 使用者手冊](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Net>

**元件：** 系統（在 System.dll 中）

**.NET Framework 版本：** 自2.0 開始提供。
