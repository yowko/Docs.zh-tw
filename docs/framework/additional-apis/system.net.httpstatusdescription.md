---
title: HttpStatusDescription 類別（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.HttpStatusDescription
- System.Net.HttpStatusDescription.Get
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 0214d8259c735de11abe204680d619a7298466de
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990336"
---
# <a name="httpstatusdescription-class"></a><span data-ttu-id="d9813-102">HttpStatusDescription 類別</span><span class="sxs-lookup"><span data-stu-id="d9813-102">HttpStatusDescription class</span></span>

<span data-ttu-id="d9813-103">提供標準 HTTP 狀態原因。</span><span class="sxs-lookup"><span data-stu-id="d9813-103">Provides standard HTTP status descriptions.</span></span> <span data-ttu-id="d9813-104">這個類別無法被繼承。</span><span class="sxs-lookup"><span data-stu-id="d9813-104">This class cannot be inherited.</span></span>

```csharp
internal static class HttpStatusDescription
```

> [!WARNING]
> <span data-ttu-id="d9813-105">這個類別是內部的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="d9813-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="d9813-106">在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="d9813-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="get-method"></a><span data-ttu-id="d9813-107">Get 方法</span><span class="sxs-lookup"><span data-stu-id="d9813-107">Get method</span></span>

<span data-ttu-id="d9813-108">傳回與指定的 HTTP 狀態碼相關聯的描述。</span><span class="sxs-lookup"><span data-stu-id="d9813-108">Returns the description associated with the specified HTTP status code.</span></span>

```csharp
internal static string Get(int code)
```

### <a name="parameters"></a><span data-ttu-id="d9813-109">參數</span><span class="sxs-lookup"><span data-stu-id="d9813-109">Parameters</span></span>

<span data-ttu-id="d9813-110">`code` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="d9813-110">`code` <xref:System.Int32></span></span>

<span data-ttu-id="d9813-111">HTTP 狀態碼，例如 `404` 。</span><span class="sxs-lookup"><span data-stu-id="d9813-111">The HTTP status code, for example, `404`.</span></span>

### <a name="return-value"></a><span data-ttu-id="d9813-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="d9813-112">Return value</span></span>

<xref:System.String?displayProperty=nameWithType>

<span data-ttu-id="d9813-113">HTTP 狀態原因。</span><span class="sxs-lookup"><span data-stu-id="d9813-113">The HTTP status description.</span></span>

## <a name="requirements"></a><span data-ttu-id="d9813-114">需求</span><span class="sxs-lookup"><span data-stu-id="d9813-114">Requirements</span></span>

<span data-ttu-id="d9813-115">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="d9813-115">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="d9813-116">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="d9813-116">**Assembly:** System (in System.dll)</span></span>
