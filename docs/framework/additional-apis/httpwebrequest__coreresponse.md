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
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="a495d-104">HttpWebRequest。 \_CoreResponse 欄位</span><span class="sxs-lookup"><span data-stu-id="a495d-104">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="a495d-105">`HttpWebRequest._CoreResponse`是[CoreResponseData](coreresponsedata.md) <xref:System.Exception> 包含 HTTP 回應剖析結果的物件（CoreResponseData 或）。</span><span class="sxs-lookup"><span data-stu-id="a495d-105">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="a495d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a495d-106">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="a495d-107">此 API 不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="a495d-107">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="a495d-108">相反地，您應該使用 <xref:System.Diagnostics.DiagnosticSource> 來攔截網路程式碼。</span><span class="sxs-lookup"><span data-stu-id="a495d-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="a495d-109">請參閱[DiagnosticSource 使用者手冊](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。</span><span class="sxs-lookup"><span data-stu-id="a495d-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="a495d-110">在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="a495d-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="a495d-111">需求</span><span class="sxs-lookup"><span data-stu-id="a495d-111">Requirements</span></span>

<span data-ttu-id="a495d-112">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="a495d-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="a495d-113">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="a495d-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="a495d-114">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="a495d-114">**.NET Framework versions:** Available since 2.0.</span></span>
