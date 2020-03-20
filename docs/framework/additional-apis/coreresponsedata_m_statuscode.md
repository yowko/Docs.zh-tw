---
title: 核心回應資料.m_StatusCode欄位
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
ms.openlocfilehash: dfed9a748e959f0f751408566c7cbb4d2fa13e3c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79156069"
---
# <a name="coreresponsedatam_statuscode-field"></a><span data-ttu-id="eb7e4-102">核心回應資料.m\_狀態碼欄位</span><span class="sxs-lookup"><span data-stu-id="eb7e4-102">CoreResponseData.m\_StatusCode Field</span></span>

<span data-ttu-id="eb7e4-103">`CoreResponseData.m_StatusCode`包含<xref:System.Net.HttpStatusCode>回應的狀態。</span><span class="sxs-lookup"><span data-stu-id="eb7e4-103">`CoreResponseData.m_StatusCode` is an <xref:System.Net.HttpStatusCode> containing the status of the response.</span></span>

## <a name="syntax"></a><span data-ttu-id="eb7e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb7e4-104">Syntax</span></span>
  
```csharp
public HttpStatusCode m_StatusCode
```

> [!WARNING]
> <span data-ttu-id="eb7e4-105">此 API 不應直接用於代碼。</span><span class="sxs-lookup"><span data-stu-id="eb7e4-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="eb7e4-106">相反，您應該使用 掛鉤<xref:System.Diagnostics.DiagnosticSource>網路代碼。</span><span class="sxs-lookup"><span data-stu-id="eb7e4-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="eb7e4-107">請參閱[診斷源使用者指南](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。</span><span class="sxs-lookup"><span data-stu-id="eb7e4-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="eb7e4-108">在任何情況下，Microsoft 都不支援在生產應用程式中使用此類。</span><span class="sxs-lookup"><span data-stu-id="eb7e4-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="eb7e4-109">需求</span><span class="sxs-lookup"><span data-stu-id="eb7e4-109">Requirements</span></span>

<span data-ttu-id="eb7e4-110">**命名空間：**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="eb7e4-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="eb7e4-111">**裝配：** 系統（系統中）</span><span class="sxs-lookup"><span data-stu-id="eb7e4-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="eb7e4-112">**.NET 框架版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="eb7e4-112">**.NET Framework versions:** Available since 2.0.</span></span>
