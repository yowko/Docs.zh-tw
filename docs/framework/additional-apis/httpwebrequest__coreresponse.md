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
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="de9c1-102">HttpWeb請求。\_核心回應欄位</span><span class="sxs-lookup"><span data-stu-id="de9c1-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="de9c1-103">`HttpWebRequest._CoreResponse`是包含 HTTP 回應分析結果的物件（[核心回應資料](coreresponsedata.md)或<xref:System.Exception>）。</span><span class="sxs-lookup"><span data-stu-id="de9c1-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="de9c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="de9c1-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="de9c1-105">此 API 不應直接用於代碼。</span><span class="sxs-lookup"><span data-stu-id="de9c1-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="de9c1-106">相反，您應該使用 掛鉤<xref:System.Diagnostics.DiagnosticSource>網路代碼。</span><span class="sxs-lookup"><span data-stu-id="de9c1-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="de9c1-107">請參閱[診斷源使用者指南](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。</span><span class="sxs-lookup"><span data-stu-id="de9c1-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="de9c1-108">在任何情況下，Microsoft 都不支援在生產應用程式中使用此類。</span><span class="sxs-lookup"><span data-stu-id="de9c1-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="de9c1-109">需求</span><span class="sxs-lookup"><span data-stu-id="de9c1-109">Requirements</span></span>

<span data-ttu-id="de9c1-110">**命名空間：**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="de9c1-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="de9c1-111">**裝配：** 系統（系統中）</span><span class="sxs-lookup"><span data-stu-id="de9c1-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="de9c1-112">**.NET 框架版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="de9c1-112">**.NET Framework versions:** Available since 2.0.</span></span>
