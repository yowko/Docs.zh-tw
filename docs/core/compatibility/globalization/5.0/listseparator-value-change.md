---
title: 重大變更： TextInfo. ListSeparator 值變更
description: 瞭解 .NET 5.0 的重大變更，其中 TextInfo 的預設值是在5.0 和5.0.1 版之間變更。
ms.date: 12/10/2020
ms.openlocfilehash: 720d46c1908bcd70812f575a90f580470dbc7f32
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596484"
---
# <a name="textinfolistseparator-values-changed"></a><span data-ttu-id="9946a-103">TextInfo. ListSeparator 值已變更</span><span class="sxs-lookup"><span data-stu-id="9946a-103">TextInfo.ListSeparator values changed</span></span>

<span data-ttu-id="9946a-104">不同文化特性的預設 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 值已在所有作業系統上變更。</span><span class="sxs-lookup"><span data-stu-id="9946a-104">The default <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values for different cultures have changed on all operating systems.</span></span>

## <a name="change-description"></a><span data-ttu-id="9946a-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="9946a-105">Change description</span></span>

<span data-ttu-id="9946a-106">在 .NET 5.0.0 中，做為 [從 NLS 切換至 ICU 程式庫](icu-globalization-api.md)的一部分，在 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> Windows 上變更不同文化特性的預設值。</span><span class="sxs-lookup"><span data-stu-id="9946a-106">In .NET 5.0.0, as part of the [switch from NLS to ICU libraries](icu-globalization-api.md), the default <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values for different cultures changed on Windows.</span></span> <span data-ttu-id="9946a-107">從 Unicode (ICU) 的國際元件取得的十進位分隔符號值，是用來做為 <xref:System.Globalization.TextInfo.ListSeparator> 值。</span><span class="sxs-lookup"><span data-stu-id="9946a-107">Decimal separator values, obtained from International Components for Unicode (ICU), were used as the <xref:System.Globalization.TextInfo.ListSeparator> values.</span></span> <span data-ttu-id="9946a-108">在 Linux 和 macOS 上，值沒有變更， <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 也就是說，它們會繼續使用小數分隔符號值。</span><span class="sxs-lookup"><span data-stu-id="9946a-108">On Linux and macOS, there was no change in <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values; that is, they continued to use decimal separator values.</span></span>

<span data-ttu-id="9946a-109">針對 .NET 5.0.1 和更新版本中的所有作業系統，的值 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 相當於從 NLS 取得的值。</span><span class="sxs-lookup"><span data-stu-id="9946a-109">For all operating systems in .NET 5.0.1 and later versions, the values for <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> are equivalent to the values that would be obtained from NLS.</span></span> <span data-ttu-id="9946a-110">若為 Windows，這表示值相當於它們在 .NET Framework 和 .NET Core 1.0-3.1 中的值。</span><span class="sxs-lookup"><span data-stu-id="9946a-110">For Windows, this means the values are equivalent to what they were in .NET Framework and .NET Core 1.0 - 3.1.</span></span> <span data-ttu-id="9946a-111">若為 Linux 和 macOS，這些 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 值現在會與 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> Windows 的值相符。</span><span class="sxs-lookup"><span data-stu-id="9946a-111">For Linux and macOS, the <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values now match the <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values for Windows.</span></span>

<span data-ttu-id="9946a-112">下表摘要說明值的變更 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="9946a-112">The following table summarizes the changes for <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values.</span></span>

| | <span data-ttu-id="9946a-113">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="9946a-113">.NET Framework</span></span><br/><span data-ttu-id="9946a-114">.NET Core 1.0-3。1</span><span class="sxs-lookup"><span data-stu-id="9946a-114">.NET Core 1.0 - 3.1</span></span> | <span data-ttu-id="9946a-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="9946a-115">.NET 5.0</span></span> | <span data-ttu-id="9946a-116">.NET 5.0。1</span><span class="sxs-lookup"><span data-stu-id="9946a-116">.NET 5.0.1</span></span> |
-|-|-|-
| <span data-ttu-id="9946a-117">**Windows**</span><span class="sxs-lookup"><span data-stu-id="9946a-117">**Windows**</span></span> | <span data-ttu-id="9946a-118">從 NLS 取得</span><span class="sxs-lookup"><span data-stu-id="9946a-118">Obtain from NLS</span></span> | <span data-ttu-id="9946a-119">來自 ICU 的小數分隔符號。</span><span class="sxs-lookup"><span data-stu-id="9946a-119">Decimal separator from ICU.</span></span><br/><span data-ttu-id="9946a-120">可以切換回 NLS。</span><span class="sxs-lookup"><span data-stu-id="9946a-120">Can switch back to NLS.</span></span> | <span data-ttu-id="9946a-121">相當於 NLS</span><span class="sxs-lookup"><span data-stu-id="9946a-121">Equivalent to NLS</span></span> |
| <span data-ttu-id="9946a-122">**Linux 與 macOS**</span><span class="sxs-lookup"><span data-stu-id="9946a-122">**Linux and macOS**</span></span> | <span data-ttu-id="9946a-123">來自 ICU 的小數分隔符號</span><span class="sxs-lookup"><span data-stu-id="9946a-123">Decimal separator from ICU</span></span> | <span data-ttu-id="9946a-124">來自 ICU 的小數分隔符號</span><span class="sxs-lookup"><span data-stu-id="9946a-124">Decimal separator from ICU</span></span> | <span data-ttu-id="9946a-125">相當於 NLS</span><span class="sxs-lookup"><span data-stu-id="9946a-125">Equivalent to NLS</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="9946a-126">引進的版本</span><span class="sxs-lookup"><span data-stu-id="9946a-126">Version introduced</span></span>

<span data-ttu-id="9946a-127">5.0.1</span><span class="sxs-lookup"><span data-stu-id="9946a-127">5.0.1</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="9946a-128">變更的原因</span><span class="sxs-lookup"><span data-stu-id="9946a-128">Reason for change</span></span>

<span data-ttu-id="9946a-129">開發人員回報在 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 剖析逗點分隔值 (CSV) 檔案時，他們使用屬性，而新的 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 值會中斷該剖析。</span><span class="sxs-lookup"><span data-stu-id="9946a-129">Developers reported that they use the <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> property when parsing comma-separated value (CSV) files, and the new <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values broke that parsing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="9946a-130">建議的動作</span><span class="sxs-lookup"><span data-stu-id="9946a-130">Recommended action</span></span>

<span data-ttu-id="9946a-131">如果您的程式碼依賴先前的十進位分隔符號值，您可以將所需的值硬式編碼 <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="9946a-131">If your code relies on the previous decimal separator values, you can hardcode the desired <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="9946a-132">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="9946a-132">Affected APIs</span></span>

- <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=fullName>

<!--

#### Category

- Globalization

### Affected APIs

- `P:System.Globalization.TextInfo.ListSeparator`

-->
