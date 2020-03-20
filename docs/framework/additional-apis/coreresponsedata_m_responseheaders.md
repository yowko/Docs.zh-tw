---
title: 核心回應資料.m_ResponseHeaders欄位
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
ms.openlocfilehash: 723df6dc2de978695608d106e3a01bde286fc4fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79156099"
---
# <a name="coreresponsedatam_responseheaders-field"></a>核心回應資料.m\_回應標題欄位

`CoreResponseData.m_ResponseHeaders`是與<xref:System.Net.WebHeaderCollection>伺服器回應關聯的標頭。

## <a name="syntax"></a>語法
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> 此 API 不應直接用於代碼。 相反，您應該使用 掛鉤<xref:System.Diagnostics.DiagnosticSource>網路代碼。 請參閱[診斷源使用者指南](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。
>
> 在任何情況下，Microsoft 都不支援在生產應用程式中使用此類。

## <a name="requirements"></a>需求

**命名空間：**<xref:System.Net>

**裝配：** 系統（系統中）

**.NET 框架版本：** 自 2.0 起可用。
