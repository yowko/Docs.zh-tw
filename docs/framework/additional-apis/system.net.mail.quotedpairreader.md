---
title: QuotedPairReader 類別（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Mail.QuotedPairReader
- System.Net.Mail.QuotedPairReader.CountQuotedChars
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 898c6e9d2d5dd02f3d5f9c096ad470b5dd445d1d
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: zh-TW
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051307"
---
# <a name="quotedpairreader-class"></a><span data-ttu-id="4816d-102">QuotedPairReader 類別</span><span class="sxs-lookup"><span data-stu-id="4816d-102">QuotedPairReader class</span></span>

<span data-ttu-id="4816d-103">決定以引號括住的字串括住的字元（已轉義）。</span><span class="sxs-lookup"><span data-stu-id="4816d-103">Determines which characters are quoted (escaped) in a quoted string.</span></span> <span data-ttu-id="4816d-104">這個類別無法被繼承。</span><span class="sxs-lookup"><span data-stu-id="4816d-104">This class cannot be inherited.</span></span>

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> <span data-ttu-id="4816d-105">這個類別是內部的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="4816d-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="4816d-106">在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="4816d-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="countquotedchars-method"></a><span data-ttu-id="4816d-107">CountQuotedChars 方法</span><span class="sxs-lookup"><span data-stu-id="4816d-107">CountQuotedChars method</span></span>

<span data-ttu-id="4816d-108">在指定的字串中計算連續加上引號的字元數，包括多個前面加上引號的反斜線。</span><span class="sxs-lookup"><span data-stu-id="4816d-108">Counts the number of consecutive quoted characters, including multiple preceding quoted backslashes, in the specified string.</span></span> <span data-ttu-id="4816d-109">例如，假設字串和的 `a\\\b` 索引 `4` ，方法 `4` 會傳回，因為 `b` 會加上引號，因此是前面三個反斜線。</span><span class="sxs-lookup"><span data-stu-id="4816d-109">For example, given the string `a\\\b` and an index of `4`, the method returns `4`, because `b` is quoted and so are the three preceding backslashes.</span></span>

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a><span data-ttu-id="4816d-110">參數</span><span class="sxs-lookup"><span data-stu-id="4816d-110">Parameters</span></span>

- <span data-ttu-id="4816d-111">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="4816d-111">`data` <xref:System.String></span></span>

  <span data-ttu-id="4816d-112">要在其中計算連續引號字元的資料字串。</span><span class="sxs-lookup"><span data-stu-id="4816d-112">The data string in which to count consecutive quoted characters.</span></span>

- <span data-ttu-id="4816d-113">`index` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="4816d-113">`index` <xref:System.Int32></span></span>

  <span data-ttu-id="4816d-114">指定字串中的位置，最高到，包括應計算的連續引號字元。</span><span class="sxs-lookup"><span data-stu-id="4816d-114">The position in the specified string up to and including which consecutive quoted characters should be counted.</span></span>

- <span data-ttu-id="4816d-115">`permitUnicodeEscaping` <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="4816d-115">`permitUnicodeEscaping` <xref:System.Boolean></span></span>

  <span data-ttu-id="4816d-116">`true`表示允許轉義 Unicode 字元;否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="4816d-116">`true` to permit Unicode characters to be escaped; otherwise, `false`.</span></span>

### <a name="return-value"></a><span data-ttu-id="4816d-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="4816d-117">Return value</span></span>

<xref:System.Int32?displayProperty=nameWithType>

<span data-ttu-id="4816d-118">`0`如果指定索引處的字元未進行轉義，則為，否則，就是在中最多加上引號字元數，並在其中包含字元 `index` 。</span><span class="sxs-lookup"><span data-stu-id="4816d-118">`0` if the character at the specified index is not escaped; otherwise, the number of consecutive quoted characters up to and including the character at `index`.</span></span>

### <a name="exceptions"></a><span data-ttu-id="4816d-119">例外狀況</span><span class="sxs-lookup"><span data-stu-id="4816d-119">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="4816d-120">找到了已轉義的 Unicode 字元，但不允許這樣做。</span><span class="sxs-lookup"><span data-stu-id="4816d-120">An escaped Unicode character was found but is not permitted.</span></span>

## <a name="requirements"></a><span data-ttu-id="4816d-121">需求</span><span class="sxs-lookup"><span data-stu-id="4816d-121">Requirements</span></span>

<span data-ttu-id="4816d-122">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="4816d-122">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="4816d-123">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="4816d-123">**Assembly:** System (in System.dll)</span></span>
