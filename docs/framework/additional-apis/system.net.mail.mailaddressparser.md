---
title: MailAddressParser 類別（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.MailAddressParser
- System.Net.Mail.MailAddressParser.ParseAddress
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ff83f6946539fa262ccde980052627f98c75601d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051346"
---
# <a name="mailaddressparser-class"></a><span data-ttu-id="98e5b-102">MailAddressParser 類別</span><span class="sxs-lookup"><span data-stu-id="98e5b-102">MailAddressParser class</span></span>

<span data-ttu-id="98e5b-103">剖析 RFC 2822 中所述的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="98e5b-103">Parses email addresses as described in RFC 2822.</span></span> <span data-ttu-id="98e5b-104">這個類別無法被繼承。</span><span class="sxs-lookup"><span data-stu-id="98e5b-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailAddressParser
```

> [!WARNING]
> <span data-ttu-id="98e5b-105">這個類別是內部的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="98e5b-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="98e5b-106">在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="98e5b-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="parseaddress-method"></a><span data-ttu-id="98e5b-107">ParseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="98e5b-107">ParseAddress method</span></span>

<span data-ttu-id="98e5b-108">剖析指定之字串中的單一電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="98e5b-108">Parses a single email address from the specified string.</span></span>

```csharp
internal static MailAddress ParseAddress(string data)
```

### <a name="parameters"></a><span data-ttu-id="98e5b-109">參數</span><span class="sxs-lookup"><span data-stu-id="98e5b-109">Parameters</span></span>

<span data-ttu-id="98e5b-110">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="98e5b-110">`data` <xref:System.String></span></span>

<span data-ttu-id="98e5b-111">包含要剖析之電子郵件地址的字串。</span><span class="sxs-lookup"><span data-stu-id="98e5b-111">The string that contains an email address to be parsed.</span></span>

### <a name="return-value"></a><span data-ttu-id="98e5b-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="98e5b-112">Return value</span></span>

<xref:System.Net.Mail.MailAddress>

<span data-ttu-id="98e5b-113">有效的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="98e5b-113">A valid email address.</span></span>

### <a name="exceptions"></a><span data-ttu-id="98e5b-114">例外狀況</span><span class="sxs-lookup"><span data-stu-id="98e5b-114">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="98e5b-115">電子郵件地址無效。</span><span class="sxs-lookup"><span data-stu-id="98e5b-115">The email address is invalid.</span></span>

## <a name="requirements"></a><span data-ttu-id="98e5b-116">需求</span><span class="sxs-lookup"><span data-stu-id="98e5b-116">Requirements</span></span>

<span data-ttu-id="98e5b-117">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="98e5b-117">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="98e5b-118">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="98e5b-118">**Assembly:** System (in System.dll)</span></span>
