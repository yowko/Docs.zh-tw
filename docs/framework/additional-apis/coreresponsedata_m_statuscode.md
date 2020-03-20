---
title: 核心回應資料.m_StatusCode欄位
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_StatusCode
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: dfed9a748e959f0f751408566c7cbb4d2fa13e3c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79156069"
---
# <a name="coreresponsedatam_statuscode-field"></a>核心回應資料.m\_狀態碼欄位

`CoreResponseData.m_StatusCode`包含<xref:System.Net.HttpStatusCode>回應的狀態。

## <a name="syntax"></a>語法
  
```csharp
public HttpStatusCode m_StatusCode
```

> [!WARNING]
> 此 API 不應直接用於代碼。 相反，您應該使用 掛鉤<xref:System.Diagnostics.DiagnosticSource>網路代碼。 請參閱[診斷源使用者指南](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。
>
> 在任何情況下，Microsoft 都不支援在生產應用程式中使用此類。

## <a name="requirements"></a>需求

**命名空間：**<xref:System.Net>

**裝配：** 系統（系統中）

**.NET 框架版本：** 自 2.0 起可用。
