---
title: HttpWebRequest._CoreResponse 欄位
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
ms.openlocfilehash: 3627c9bf0d72ccec3a0d6d9c7c89b62f83dcd4b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356195"
---
# <a name="httpwebrequestcoreresponse-field"></a><span data-ttu-id="e358d-102">HttpWebRequest。\_CoreResponse 欄位</span><span class="sxs-lookup"><span data-stu-id="e358d-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="e358d-103">`HttpWebRequest._CoreResponse` 是一個物件 (任一[CoreResponseData](coreresponsedata.md)或<xref:System.Exception>) 包含 HTTP 回應剖析的結果。</span><span class="sxs-lookup"><span data-stu-id="e358d-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="e358d-104">語法</span><span class="sxs-lookup"><span data-stu-id="e358d-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="e358d-105">這個 API 不是直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="e358d-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="e358d-106">相反地，您應該使用<xref:System.Diagnostics.DiagnosticSource>連結網路的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e358d-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="e358d-107">請參閱[DiagnosticSource 使用者手冊 》](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。</span><span class="sxs-lookup"><span data-stu-id="e358d-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="e358d-108">Microsoft 不支援在實際執行應用程式在任何情況下使用這個類別。</span><span class="sxs-lookup"><span data-stu-id="e358d-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="e358d-109">需求</span><span class="sxs-lookup"><span data-stu-id="e358d-109">Requirements</span></span>

<span data-ttu-id="e358d-110">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="e358d-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="e358d-111">**組件：** 系統 （在 System.dll)</span><span class="sxs-lookup"><span data-stu-id="e358d-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="e358d-112">**.NET framework 版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="e358d-112">**.NET Framework versions:** Available since 2.0.</span></span>
