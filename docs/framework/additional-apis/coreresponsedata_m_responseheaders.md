---
title: 核心回應資料.m_ResponseHeaders欄位
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
ms.openlocfilehash: 723df6dc2de978695608d106e3a01bde286fc4fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79156099"
---
# <a name="coreresponsedatam_responseheaders-field"></a><span data-ttu-id="83807-102">核心回應資料.m\_回應標題欄位</span><span class="sxs-lookup"><span data-stu-id="83807-102">CoreResponseData.m\_ResponseHeaders Field</span></span>

<span data-ttu-id="83807-103">`CoreResponseData.m_ResponseHeaders`是與<xref:System.Net.WebHeaderCollection>伺服器回應關聯的標頭。</span><span class="sxs-lookup"><span data-stu-id="83807-103">`CoreResponseData.m_ResponseHeaders` is a <xref:System.Net.WebHeaderCollection> of headers associated with the server response.</span></span>

## <a name="syntax"></a><span data-ttu-id="83807-104">語法</span><span class="sxs-lookup"><span data-stu-id="83807-104">Syntax</span></span>
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> <span data-ttu-id="83807-105">此 API 不應直接用於代碼。</span><span class="sxs-lookup"><span data-stu-id="83807-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="83807-106">相反，您應該使用 掛鉤<xref:System.Diagnostics.DiagnosticSource>網路代碼。</span><span class="sxs-lookup"><span data-stu-id="83807-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="83807-107">請參閱[診斷源使用者指南](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。</span><span class="sxs-lookup"><span data-stu-id="83807-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
>
> <span data-ttu-id="83807-108">在任何情況下，Microsoft 都不支援在生產應用程式中使用此類。</span><span class="sxs-lookup"><span data-stu-id="83807-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="83807-109">需求</span><span class="sxs-lookup"><span data-stu-id="83807-109">Requirements</span></span>

<span data-ttu-id="83807-110">**命名空間：**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="83807-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="83807-111">**裝配：** 系統（系統中）</span><span class="sxs-lookup"><span data-stu-id="83807-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="83807-112">**.NET 框架版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="83807-112">**.NET Framework versions:** Available since 2.0.</span></span>
