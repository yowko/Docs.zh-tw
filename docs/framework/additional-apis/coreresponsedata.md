---
title: CoreResponseData 類別
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: fd0ffb982c22b0a8b6cb5dd677faafb9921bf5d9
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741028"
---
# <a name="coreresponsedata-class"></a><span data-ttu-id="b15e3-102">CoreResponseData 類別</span><span class="sxs-lookup"><span data-stu-id="b15e3-102">CoreResponseData Class</span></span>

<span data-ttu-id="b15e3-103">`CoreResponseData` 類別代表 HTTP 標頭和回應主體的剖析。</span><span class="sxs-lookup"><span data-stu-id="b15e3-103">The `CoreResponseData` class represents the parsing of the HTTP headers and the response body.</span></span>

## <a name="syntax"></a><span data-ttu-id="b15e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="b15e3-104">Syntax</span></span>
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> <span data-ttu-id="b15e3-105">這個 API 是內部的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="b15e3-105">This API is internal, and it is not meant to be used directly in your code.</span></span> <span data-ttu-id="b15e3-106">相反地，您應該使用 <xref:System.Diagnostics.DiagnosticSource> 來攔截網路程式碼。</span><span class="sxs-lookup"><span data-stu-id="b15e3-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="b15e3-107">請參閱[DiagnosticSource 使用者手冊](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。</span><span class="sxs-lookup"><span data-stu-id="b15e3-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="b15e3-108">在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="b15e3-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="b15e3-109">需求</span><span class="sxs-lookup"><span data-stu-id="b15e3-109">Requirements</span></span>

<span data-ttu-id="b15e3-110">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="b15e3-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="b15e3-111">**元件：** 系統（在 System .dll 中）</span><span class="sxs-lookup"><span data-stu-id="b15e3-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="b15e3-112">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="b15e3-112">**.NET Framework versions:** Available since 2.0.</span></span>
