---
title: MailBnfHelper 類別（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mime.MailBnfHelper
- System.Net.Mime.MailBnfHelper.Ascii7bitMaxValue
- System.Net.Mime.MailBnfHelper.Atext
- System.Net.Mime.MailBnfHelper.CR
- System.Net.Mime.MailBnfHelper.Ctext
- System.Net.Mime.MailBnfHelper.Dot
- System.Net.Mime.MailBnfHelper.EndComment
- System.Net.Mime.MailBnfHelper.LF
- System.Net.Mime.MailBnfHelper.Space
- System.Net.Mime.MailBnfHelper.StartComment
- System.Net.Mime.MailBnfHelper.Tab
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 86c98726a7886285917b6be8c7631ca1e9e425e6
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990310"
---
# <a name="mailbnfhelper-class"></a><span data-ttu-id="a439c-102">MailBnfHelper 類別</span><span class="sxs-lookup"><span data-stu-id="a439c-102">MailBnfHelper class</span></span>

<span data-ttu-id="a439c-103">包含用來剖析網際網路訊息格式字串的公用程式方法。</span><span class="sxs-lookup"><span data-stu-id="a439c-103">Contains utility methods for parsing internet message-formatted strings.</span></span> <span data-ttu-id="a439c-104">這個類別無法被繼承。</span><span class="sxs-lookup"><span data-stu-id="a439c-104">This class cannot be inherited.</span></span>

```csharp
internal static class MailBnfHelper
```

> [!WARNING]
> <span data-ttu-id="a439c-105">這個類別是內部的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="a439c-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="a439c-106">在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="a439c-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="ascii7bitmaxvalue-field"></a><span data-ttu-id="a439c-107">Ascii7bitMaxValue 欄位</span><span class="sxs-lookup"><span data-stu-id="a439c-107">Ascii7bitMaxValue field</span></span>

<span data-ttu-id="a439c-108">表示最大的7位 Ascii 值。</span><span class="sxs-lookup"><span data-stu-id="a439c-108">Represents the maximum 7-bit Ascii value.</span></span>

```csharp
internal static readonly int Ascii7bitMaxValue
```

## <a name="atext-field"></a><span data-ttu-id="a439c-109">文字欄位</span><span class="sxs-lookup"><span data-stu-id="a439c-109">Atext field</span></span>

<span data-ttu-id="a439c-110">表示原子中允許的字元。</span><span class="sxs-lookup"><span data-stu-id="a439c-110">Represents the characters allowed in atoms.</span></span>

```csharp
internal static bool[] Atext
```

## <a name="cr-field"></a><span data-ttu-id="a439c-111">CR 欄位</span><span class="sxs-lookup"><span data-stu-id="a439c-111">CR field</span></span>

<span data-ttu-id="a439c-112">表示回車符。</span><span class="sxs-lookup"><span data-stu-id="a439c-112">Represents the carriage-return character.</span></span>

```csharp
internal static readonly char CR
```

## <a name="ctext-field"></a><span data-ttu-id="a439c-113">Ctext 欄位</span><span class="sxs-lookup"><span data-stu-id="a439c-113">Ctext field</span></span>

<span data-ttu-id="a439c-114">表示批註內允許的字元。</span><span class="sxs-lookup"><span data-stu-id="a439c-114">Represents the characters allowed inside of comments.</span></span>

```csharp
internal static bool[] Ctext
```

## <a name="dot-field"></a><span data-ttu-id="a439c-115">點欄位</span><span class="sxs-lookup"><span data-stu-id="a439c-115">Dot field</span></span>

<span data-ttu-id="a439c-116">表示全停用字元（ `.` ）。</span><span class="sxs-lookup"><span data-stu-id="a439c-116">Represents the full-stop character (`.`).</span></span>

```csharp
internal static readonly char Dot
```

## <a name="endcomment-field"></a><span data-ttu-id="a439c-117">EndComment 欄位</span><span class="sxs-lookup"><span data-stu-id="a439c-117">EndComment field</span></span>

<span data-ttu-id="a439c-118">表示指定批註結尾的字元。</span><span class="sxs-lookup"><span data-stu-id="a439c-118">Represents the character that specifies the end of a comment.</span></span>

```csharp
internal static readonly char EndComment
```

## <a name="lf-field"></a><span data-ttu-id="a439c-119">LF 欄位</span><span class="sxs-lookup"><span data-stu-id="a439c-119">LF field</span></span>

<span data-ttu-id="a439c-120">表示換行字元。</span><span class="sxs-lookup"><span data-stu-id="a439c-120">Represents the line-feed character.</span></span>

```csharp
internal static readonly char LF
```

## <a name="space-field"></a><span data-ttu-id="a439c-121">空間欄位</span><span class="sxs-lookup"><span data-stu-id="a439c-121">Space field</span></span>

<span data-ttu-id="a439c-122">代表空白字元。</span><span class="sxs-lookup"><span data-stu-id="a439c-122">Represents the space character.</span></span>

```csharp
internal static readonly char Space
```

## <a name="startcomment-field"></a><span data-ttu-id="a439c-123">StartComment 欄位</span><span class="sxs-lookup"><span data-stu-id="a439c-123">StartComment field</span></span>

<span data-ttu-id="a439c-124">表示指定批註開頭的字元。</span><span class="sxs-lookup"><span data-stu-id="a439c-124">Represents the character that specifies the start of a comment.</span></span>

```csharp
internal static readonly char StartComment
```

## <a name="tab-field"></a><span data-ttu-id="a439c-125">Tab 欄位</span><span class="sxs-lookup"><span data-stu-id="a439c-125">Tab field</span></span>

<span data-ttu-id="a439c-126">表示定位字元。</span><span class="sxs-lookup"><span data-stu-id="a439c-126">Represents the tab character.</span></span>

```csharp
internal static readonly char Tab
```

## <a name="requirements"></a><span data-ttu-id="a439c-127">需求</span><span class="sxs-lookup"><span data-stu-id="a439c-127">Requirements</span></span>

<span data-ttu-id="a439c-128">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="a439c-128">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="a439c-129">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="a439c-129">**Assembly:** System (in System.dll)</span></span>
