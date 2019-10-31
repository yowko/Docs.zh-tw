---
title: HttpWebRequest. _HttpResponse 欄位
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d993021ccb87ccafb5f6f2fc4c6c7c288288adae
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120084"
---
# <a name="httpwebrequest_httpresponse-field"></a><span data-ttu-id="15741-102">HttpWebRequest.\_HttpResponse 欄位</span><span class="sxs-lookup"><span data-stu-id="15741-102">HttpWebRequest.\_HttpResponse Field</span></span>

<span data-ttu-id="15741-103">`HttpWebRequest._HttpResponse` 是一個 <xref:System.Net.HttpWebResponse>，其中包含來自 HTTP 要求的 HTTP 回應詳細資料。</span><span class="sxs-lookup"><span data-stu-id="15741-103">`HttpWebRequest._HttpResponse` is an <xref:System.Net.HttpWebResponse> containing HTTP response details from an HTTP request.</span></span> <span data-ttu-id="15741-104">在收到 HTTP 回應之前，它可以 `null`。</span><span class="sxs-lookup"><span data-stu-id="15741-104">It can be `null` until an HTTP response is received.</span></span>

## <a name="syntax"></a><span data-ttu-id="15741-105">語法</span><span class="sxs-lookup"><span data-stu-id="15741-105">Syntax</span></span>
  
```csharp  
internal HttpWebResponse _HttpResponse
```

> [!WARNING]
> <span data-ttu-id="15741-106">[`HttpWebRequest._HttpResponse`] 欄位是內部的，而不是直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="15741-106">The `HttpWebRequest._HttpResponse` field is internal and not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="15741-107">在任何情況下，Microsoft 不支援在生產應用程式中使用此欄位。</span><span class="sxs-lookup"><span data-stu-id="15741-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="15741-108">需求</span><span class="sxs-lookup"><span data-stu-id="15741-108">Requirements</span></span>

<span data-ttu-id="15741-109">**命名空間︰** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="15741-109">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="15741-110">**元件：** 系統（在 System .dll 中）</span><span class="sxs-lookup"><span data-stu-id="15741-110">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="15741-111">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="15741-111">**.NET Framework versions:** Available since 2.0.</span></span>
