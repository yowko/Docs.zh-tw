---
title: CoreResponseData.m_ResponseHeaders 欄位
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
ms.openlocfilehash: ea93b70ae8e1a710b4208050d7ec823a28b218b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705970"
---
# <a name="coreresponsedatamresponseheaders-field"></a><span data-ttu-id="dbd5e-102">CoreResponseData.m\_ResponseHeaders 欄位</span><span class="sxs-lookup"><span data-stu-id="dbd5e-102">CoreResponseData.m\_ResponseHeaders Field</span></span>

<span data-ttu-id="dbd5e-103">`CoreResponseData.m_ResponseHeaders` 是<xref:System.Net.WebHeaderCollection>伺服器回應相關聯的標頭。</span><span class="sxs-lookup"><span data-stu-id="dbd5e-103">`CoreResponseData.m_ResponseHeaders` is a <xref:System.Net.WebHeaderCollection> of headers associated with the server response.</span></span>

## <a name="syntax"></a><span data-ttu-id="dbd5e-104">語法</span><span class="sxs-lookup"><span data-stu-id="dbd5e-104">Syntax</span></span>
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> <span data-ttu-id="dbd5e-105">此 API 不適合直接在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="dbd5e-105">This API is not meant to be used directly in your code.</span></span> <span data-ttu-id="dbd5e-106">因此，您應該改用<xref:System.Diagnostics.DiagnosticSource>連結網路的程式碼。</span><span class="sxs-lookup"><span data-stu-id="dbd5e-106">Instead, you should use a <xref:System.Diagnostics.DiagnosticSource> to hook networking code.</span></span> <span data-ttu-id="dbd5e-107">請參閱[DiagnosticSource 使用者指南](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)。</span><span class="sxs-lookup"><span data-stu-id="dbd5e-107">See [DiagnosticSource User's Guide](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md).</span></span>
> 
> <span data-ttu-id="dbd5e-108">Microsoft 不支援在生產環境應用程式中任何情況下使用這個類別。</span><span class="sxs-lookup"><span data-stu-id="dbd5e-108">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="dbd5e-109">需求</span><span class="sxs-lookup"><span data-stu-id="dbd5e-109">Requirements</span></span>

<span data-ttu-id="dbd5e-110">**命名空間︰** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="dbd5e-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="dbd5e-111">**組件：**（在 System.dll) 的系統</span><span class="sxs-lookup"><span data-stu-id="dbd5e-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="dbd5e-112">**.NET framework 版本：** 自 2.0 起可用。</span><span class="sxs-lookup"><span data-stu-id="dbd5e-112">**.NET Framework versions:** Available since 2.0.</span></span>
