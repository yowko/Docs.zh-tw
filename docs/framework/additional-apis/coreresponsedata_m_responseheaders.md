---
title: CoreResponseData。 m_ResponseHeaders 欄位
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
ms.openlocfilehash: df0b592a5f85d4c99dee4ecb60963f4abb560a13
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741014"
---
# <a name="coreresponsedatam_responseheaders-field"></a>CoreResponseData\_ResponseHeaders 欄位

`CoreResponseData.m_ResponseHeaders` 是與伺服器回應相關聯的標頭 <xref:System.Net.WebHeaderCollection>。

## <a name="syntax"></a>語法
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> 此 API 不適合直接在您的程式碼中使用。 相反地，您應該使用 <xref:System.Diagnostics.DiagnosticSource> 來攔截網路程式碼。 請參閱[DiagnosticSource 使用者手冊](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。
> 
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Net>

**元件：** 系統（在 System .dll 中）

**.NET Framework 版本：** 自2.0 開始提供。
