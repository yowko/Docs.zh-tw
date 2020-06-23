---
title: HttpWebRequest。 _HttpResponse] 欄位
description: 瞭解 .NET 中的 _HttpResponse HttpWebRequest 欄位。 此欄位是 HttpWebResponse 類型，其中包含來自 HTTP 要求的 HTTP 回應詳細資料。
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._HttpResponse
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: eab9b789-beb4-4c28-b2d8-78debc7ba129
ms.openlocfilehash: 70058e1183abf5b6bfd172497f65a3ceb2344060
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989953"
---
# <a name="httpwebrequest_httpresponse-field"></a><span data-ttu-id="e79bf-104">HttpWebRequest。 \_HttpResponse 欄位</span><span class="sxs-lookup"><span data-stu-id="e79bf-104">HttpWebRequest.\_HttpResponse Field</span></span>

<span data-ttu-id="e79bf-105">`HttpWebRequest._HttpResponse`是， <xref:System.Net.HttpWebResponse> 其中包含來自 HTTP 要求的 HTTP 回應詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e79bf-105">`HttpWebRequest._HttpResponse` is an <xref:System.Net.HttpWebResponse> containing HTTP response details from an HTTP request.</span></span> <span data-ttu-id="e79bf-106">這可能是在 `null` 收到 HTTP 回應之前。</span><span class="sxs-lookup"><span data-stu-id="e79bf-106">It can be `null` until an HTTP response is received.</span></span>

## <a name="syntax"></a><span data-ttu-id="e79bf-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="e79bf-107">Syntax</span></span>
  
```csharp  
internal HttpWebResponse _HttpResponse
```

> [!WARNING]
> <span data-ttu-id="e79bf-108">`HttpWebRequest._HttpResponse`欄位是內部的，而不是直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="e79bf-108">The `HttpWebRequest._HttpResponse` field is internal and not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="e79bf-109">在任何情況下，Microsoft 不支援在生產應用程式中使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="e79bf-109">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e79bf-110">需求</span><span class="sxs-lookup"><span data-stu-id="e79bf-110">Requirements</span></span>

<span data-ttu-id="e79bf-111">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="e79bf-111">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="e79bf-112">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="e79bf-112">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="e79bf-113">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="e79bf-113">**.NET Framework versions:** Available since 2.0.</span></span>
