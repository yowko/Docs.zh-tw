---
title: CoreResponseData。 m_ResponseHeaders] 欄位
description: 瞭解 .NET 中的 m_ResponseHeaders CoreResponseData 欄位。 此欄位是 WebHeaderCollection 類型，具有與伺服器回應相關聯的標頭。
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
ms.openlocfilehash: 7c7b896193cb81e9fc9e3ec28110359003a36728
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989793"
---
# <a name="coreresponsedatam_responseheaders-field"></a><span data-ttu-id="02a87-104">CoreResponseData. m \_ ResponseHeaders 欄位</span><span class="sxs-lookup"><span data-stu-id="02a87-104">CoreResponseData.m\_ResponseHeaders Field</span></span>

<span data-ttu-id="02a87-105">`CoreResponseData.m_ResponseHeaders`這是 <xref:System.Net.WebHeaderCollection> 與伺服器回應相關聯的標頭。</span><span class="sxs-lookup"><span data-stu-id="02a87-105">`CoreResponseData.m_ResponseHeaders` is a <xref:System.Net.WebHeaderCollection> of headers associated with the server response.</span></span>

## <a name="syntax"></a><span data-ttu-id="02a87-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="02a87-106">Syntax</span></span>
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> <span data-ttu-id="02a87-107">此 API 不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="02a87-107">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="02a87-108">相反地，您應該使用 <xref:System.Diagnostics.DiagnosticSource> 來攔截網路程式碼。</span><span class="sxs-lookup"><span data-stu-id="02a87-108">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="02a87-109">請參閱[DiagnosticSource 使用者手冊](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。</span><span class="sxs-lookup"><span data-stu-id="02a87-109">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="02a87-110">在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="02a87-110">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="02a87-111">需求</span><span class="sxs-lookup"><span data-stu-id="02a87-111">Requirements</span></span>

<span data-ttu-id="02a87-112">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="02a87-112">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="02a87-113">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="02a87-113">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="02a87-114">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="02a87-114">**.NET Framework versions:** Available since 2.0.</span></span>
