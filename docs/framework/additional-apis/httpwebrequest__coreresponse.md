---
title: HttpWebRequest。 _CoreResponse 欄位
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
ms.openlocfilehash: d16936f6984e73a886f5f48e05b53501ced63c1b
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740454"
---
# <a name="httpwebrequest_coreresponse-field"></a>HttpWebRequest.\_CoreResponse 欄位

`HttpWebRequest._CoreResponse` 是包含 HTTP 回應剖析結果的物件（ [CoreResponseData](coreresponsedata.md)或 <xref:System.Exception>）。

## <a name="syntax"></a>語法
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> 此 API 不適合直接在您的程式碼中使用。 相反地，您應該使用 <xref:System.Diagnostics.DiagnosticSource> 來攔截網路程式碼。 請參閱[DiagnosticSource 使用者手冊](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。
> 
> 在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。

## <a name="requirements"></a>需求

**命名空間：** <xref:System.Net>

**元件：** 系統（在 System .dll 中）

**.NET Framework 版本：** 自2.0 開始提供。
