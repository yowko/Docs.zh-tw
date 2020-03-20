---
title: HTTPWeb請求._CoreResponse欄位
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: b275f3eece96ac8a9ae3fb0ebd030c8d79e21fc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155917"
---
# <a name="httpwebrequest_coreresponse-field"></a>HttpWeb請求。\_核心回應欄位

`HttpWebRequest._CoreResponse`是包含 HTTP 回應分析結果的物件（[核心回應資料](coreresponsedata.md)或<xref:System.Exception>）。

## <a name="syntax"></a>語法
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> 此 API 不應直接用於代碼。 相反，您應該使用 掛鉤<xref:System.Diagnostics.DiagnosticSource>網路代碼。 請參閱[診斷源使用者指南](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。
>
> 在任何情況下，Microsoft 都不支援在生產應用程式中使用此類。

## <a name="requirements"></a>需求

**命名空間：**<xref:System.Net>

**裝配：** 系統（系統中）

**.NET 框架版本：** 自 2.0 起可用。
