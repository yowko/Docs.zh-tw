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
# <a name="httpwebrequest_coreresponse-field"></a><span data-ttu-id="f10f6-102">HttpWebRequest.\_CoreResponse 欄位</span><span class="sxs-lookup"><span data-stu-id="f10f6-102">HttpWebRequest.\_CoreResponse Field</span></span>

<span data-ttu-id="f10f6-103">`HttpWebRequest._CoreResponse` 是包含 HTTP 回應剖析結果的物件（ [CoreResponseData](coreresponsedata.md)或 <xref:System.Exception>）。</span><span class="sxs-lookup"><span data-stu-id="f10f6-103">`HttpWebRequest._CoreResponse` is an object (either a [CoreResponseData](coreresponsedata.md) or an <xref:System.Exception>) containing the result of HTTP response parsing.</span></span>

## <a name="syntax"></a><span data-ttu-id="f10f6-104">語法</span><span class="sxs-lookup"><span data-stu-id="f10f6-104">Syntax</span></span>
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> <span data-ttu-id="f10f6-105">此 API 不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="f10f6-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="f10f6-106">相反地，您應該使用 <xref:System.Diagnostics.DiagnosticSource> 來攔截網路程式碼。</span><span class="sxs-lookup"><span data-stu-id="f10f6-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="f10f6-107">請參閱[DiagnosticSource 使用者手冊](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。</span><span class="sxs-lookup"><span data-stu-id="f10f6-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="f10f6-108">在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="f10f6-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f10f6-109">需求</span><span class="sxs-lookup"><span data-stu-id="f10f6-109">Requirements</span></span>

<span data-ttu-id="f10f6-110">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="f10f6-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="f10f6-111">**元件：** 系統（在 System .dll 中）</span><span class="sxs-lookup"><span data-stu-id="f10f6-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="f10f6-112">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="f10f6-112">**.NET Framework versions:** Available since 2.0.</span></span>
