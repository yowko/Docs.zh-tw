---
title: HttpWebRequest。 _CoreResponse] 欄位
description: 閱讀 .NET 中 _CoreResponse HttpWebRequest 欄位的相關資訊。 此欄位是 CoreResponseData 或 Exception 物件，其中包含 HTTP 回應剖析的結果。
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
ms.openlocfilehash: 5093ec7ed2c3b94931dcd622ae9ccdb42feffa18
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989745"
---
# <a name="httpwebrequest_coreresponse-field"></a>HttpWebRequest。 \_CoreResponse 欄位

`HttpWebRequest._CoreResponse`是[CoreResponseData](coreresponsedata.md) <xref:System.Exception> 包含 HTTP 回應剖析結果的物件（CoreResponseData 或）。

## <a name="syntax"></a>Syntax
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> 此 API 不適合直接在您的程式碼中使用。 相反地，您應該使用 <xref:System.Diagnostics.DiagnosticSource> 來攔截網路程式碼。 請參閱[DiagnosticSource 使用者手冊](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。
>
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Net>

**元件：** 系統（在 System.dll 中）

**.NET Framework 版本：** 自2.0 開始提供。
