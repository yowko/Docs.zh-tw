---
title: MailAddressParser 類別（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.MailAddressParser
- System.Net.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 2c17970614ff9b6f1e6793a064a956da7248d693
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990315"
---
# <a name="mailaddressparser-class"></a><span data-ttu-id="483a6-102">MailAddressParser 類別</span><span class="sxs-lookup"><span data-stu-id="483a6-102">MailAddressParser class</span></span>

<span data-ttu-id="483a6-103">剖析 RFC 2822 中所述的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="483a6-103">Parses email addresses as described in RFC 2822.</span></span> <span data-ttu-id="483a6-104">這個類別無法被繼承。</span><span class="sxs-lookup"><span data-stu-id="483a6-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> <span data-ttu-id="483a6-105">這個類別是內部的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="483a6-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="483a6-106">在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="483a6-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="parseaddress-method"></a><span data-ttu-id="483a6-107">ParseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="483a6-107">ParseAddress method</span></span>

<span data-ttu-id="483a6-108">剖析指定之字串中的單一電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="483a6-108">Parses a single email address from the specified string.</span></span>

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a><span data-ttu-id="483a6-109">參數</span><span class="sxs-lookup"><span data-stu-id="483a6-109">Parameters</span></span>

<span data-ttu-id="483a6-110">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="483a6-110">`data` <xref:System.String></span></span>

<span data-ttu-id="483a6-111">包含要剖析之電子郵件地址的字串。</span><span class="sxs-lookup"><span data-stu-id="483a6-111">The string that contains an email address to be parsed.</span></span>

### <a name="return-value"></a><span data-ttu-id="483a6-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="483a6-112">Return value</span></span>

<xref:System.Net.Mail.MailAddress>

<span data-ttu-id="483a6-113">有效的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="483a6-113">A valid email address.</span></span>

### <a name="exceptions"></a><span data-ttu-id="483a6-114">例外狀況</span><span class="sxs-lookup"><span data-stu-id="483a6-114">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="483a6-115">電子郵件地址無效。</span><span class="sxs-lookup"><span data-stu-id="483a6-115">The email address is invalid.</span></span>

## <a name="requirements"></a><span data-ttu-id="483a6-116">需求</span><span class="sxs-lookup"><span data-stu-id="483a6-116">Requirements</span></span>

<span data-ttu-id="483a6-117">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="483a6-117">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="483a6-118">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="483a6-118">**Assembly:** System (in System.dll)</span></span>
