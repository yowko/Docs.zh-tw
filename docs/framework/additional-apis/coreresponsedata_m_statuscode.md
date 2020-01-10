---
title: CoreResponseData。 m_StatusCode 欄位
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
ms.openlocfilehash: 8abe619a57cc61fc3502807f60deccbbd578f382
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740998"
---
# <a name="coreresponsedatam_statuscode-field"></a><span data-ttu-id="5b41d-102">CoreResponseData\_StatusCode 欄位</span><span class="sxs-lookup"><span data-stu-id="5b41d-102">CoreResponseData.m\_StatusCode Field</span></span>

<span data-ttu-id="5b41d-103">`CoreResponseData.m_StatusCode` 是包含回應狀態的 <xref:System.Net.HttpStatusCode>。</span><span class="sxs-lookup"><span data-stu-id="5b41d-103">`CoreResponseData.m_StatusCode` is an <xref:System.Net.HttpStatusCode> containing the status of the response.</span></span>

## <a name="syntax"></a><span data-ttu-id="5b41d-104">語法</span><span class="sxs-lookup"><span data-stu-id="5b41d-104">Syntax</span></span>
  
```csharp
public HttpStatusCode m_StatusCode
```

> [!WARNING]
> <span data-ttu-id="5b41d-105">此 API 不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="5b41d-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="5b41d-106">相反地，您應該使用 <xref:System.Diagnostics.DiagnosticSource> 來攔截網路程式碼。</span><span class="sxs-lookup"><span data-stu-id="5b41d-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="5b41d-107">請參閱[DiagnosticSource 使用者手冊](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。</span><span class="sxs-lookup"><span data-stu-id="5b41d-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="5b41d-108">在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="5b41d-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="5b41d-109">需求</span><span class="sxs-lookup"><span data-stu-id="5b41d-109">Requirements</span></span>

<span data-ttu-id="5b41d-110">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="5b41d-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="5b41d-111">**元件：** 系統（在 System .dll 中）</span><span class="sxs-lookup"><span data-stu-id="5b41d-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="5b41d-112">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="5b41d-112">**.NET Framework versions:** Available since 2.0.</span></span>
