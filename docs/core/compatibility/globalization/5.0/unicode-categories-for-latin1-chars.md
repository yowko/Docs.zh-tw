---
title: 重大變更：某些拉丁-1 字元的 Unicode 類別目錄已變更
description: 瞭解 .NET 5.0 中的全球化重大變更，其中 Char 方法現在會針對拉丁-1 範圍中的字元傳回正確的 Unicode 類別。
ms.date: 04/07/2020
ms.openlocfilehash: 8bd093a89857c83921fc0bf987348b529f74ce68
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760794"
---
# <a name="unicode-category-changed-for-some-latin-1-characters"></a><span data-ttu-id="ce3b1-103">某些拉丁字元的 Unicode 類別已變更</span><span class="sxs-lookup"><span data-stu-id="ce3b1-103">Unicode category changed for some Latin-1 characters</span></span>

<span data-ttu-id="ce3b1-104"><xref:System.Char> 方法現在會針對拉丁-1 範圍中的字元傳回正確的 Unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="ce3b1-104"><xref:System.Char> methods now return the correct Unicode category for characters in the Latin-1 range.</span></span> <span data-ttu-id="ce3b1-105">類別符合 Unicode 標準的類別。</span><span class="sxs-lookup"><span data-stu-id="ce3b1-105">The category matches that of the Unicode standard.</span></span>

## <a name="change-description"></a><span data-ttu-id="ce3b1-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="ce3b1-106">Change description</span></span>

<span data-ttu-id="ce3b1-107">在舊版的 .NET 中， <xref:System.Char> 方法會使用 Unicode 分類的固定清單來代表拉丁-1 範圍中的字元。</span><span class="sxs-lookup"><span data-stu-id="ce3b1-107">In previous .NET versions, <xref:System.Char> methods used a fixed list of Unicode categories for characters in the Latin-1 range.</span></span> <span data-ttu-id="ce3b1-108">不過，Unicode 標準已經變更這些字元的類別，因為這些是這些字元都已實作為這些字元，所以會產生差異。</span><span class="sxs-lookup"><span data-stu-id="ce3b1-108">However, the Unicode standard has changed the categories of some of these characters since those APIs were implemented, creating a discrepancy.</span></span> <span data-ttu-id="ce3b1-109">此外，與 api 之間的差異也會 <xref:System.Char> <xref:System.Globalization.CharUnicodeInfo> 遵循 Unicode 標準。</span><span class="sxs-lookup"><span data-stu-id="ce3b1-109">In addition, there was also a discrepancy between <xref:System.Char> and <xref:System.Globalization.CharUnicodeInfo> APIs, which follow the Unicode standard.</span></span> <span data-ttu-id="ce3b1-110">在 .NET 5.0 和更新版本中， <xref:System.Char> 方法會使用並傳回符合所有字元 unicode 標準的 unicode 分類。</span><span class="sxs-lookup"><span data-stu-id="ce3b1-110">In .NET 5.0 and later versions, <xref:System.Char> methods use and return the Unicode category that matches the Unicode standard for all characters.</span></span>

<span data-ttu-id="ce3b1-111">下表顯示其 Unicode 類別在 .NET 5.0 中已變更的字元：</span><span class="sxs-lookup"><span data-stu-id="ce3b1-111">The following table shows the characters whose Unicode categories have changed in .NET 5.0:</span></span>

| <span data-ttu-id="ce3b1-112">字元</span><span class="sxs-lookup"><span data-stu-id="ce3b1-112">Character</span></span>    | <span data-ttu-id="ce3b1-113">Unicode 類別</span><span class="sxs-lookup"><span data-stu-id="ce3b1-113">Unicode category</span></span><br><span data-ttu-id="ce3b1-114">在先前的 .NET 版本中</span><span class="sxs-lookup"><span data-stu-id="ce3b1-114">in previous .NET versions</span></span> | <span data-ttu-id="ce3b1-115">Unicode 類別</span><span class="sxs-lookup"><span data-stu-id="ce3b1-115">Unicode category</span></span><br><span data-ttu-id="ce3b1-116">.NET 5.0 和更新版本中的</span><span class="sxs-lookup"><span data-stu-id="ce3b1-116">in .NET 5.0 and later versions</span></span> |
|:------------:|:---------------------------------------------:|:--------------------------------------------------:|
| <span data-ttu-id="ce3b1-117">§ ( \u00a7) </span><span class="sxs-lookup"><span data-stu-id="ce3b1-117">§ (\u00a7)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="ce3b1-118"> ( 的 \u00aa) </span><span class="sxs-lookup"><span data-stu-id="ce3b1-118">ª (\u00aa)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |
| <span data-ttu-id="ce3b1-119">SHY ( \u00ad) </span><span class="sxs-lookup"><span data-stu-id="ce3b1-119">SHY (\u00ad)</span></span> | `DashPunctuation`                             | `Format`                                           |
| <span data-ttu-id="ce3b1-120">¶ ( \u00b6) </span><span class="sxs-lookup"><span data-stu-id="ce3b1-120">¶ (\u00b6)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="ce3b1-121"> ( \u00ba) </span><span class="sxs-lookup"><span data-stu-id="ce3b1-121">º (\u00ba)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |

## <a name="version-introduced"></a><span data-ttu-id="ce3b1-122">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ce3b1-122">Version introduced</span></span>

<span data-ttu-id="ce3b1-123">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="ce3b1-123">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ce3b1-124">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ce3b1-124">Recommended action</span></span>

<span data-ttu-id="ce3b1-125">如果您有任何程式碼使用類別取得 Unicode 字元類別， <xref:System.Char> 並假設類別永遠不會變更，您可能需要更新它。</span><span class="sxs-lookup"><span data-stu-id="ce3b1-125">If you have any code that gets the Unicode character category by using the <xref:System.Char> class and assumes the category will never change, you may need to update it.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="ce3b1-126">變更的原因</span><span class="sxs-lookup"><span data-stu-id="ce3b1-126">Reason for change</span></span>

<span data-ttu-id="ce3b1-127">這項變更是為了讓類型所傳回的類別 <xref:System.Char> 與 Unicode 標準和 <xref:System.Globalization.CharUnicodeInfo> 類型一致。</span><span class="sxs-lookup"><span data-stu-id="ce3b1-127">This change was made so that the categories returned by the <xref:System.Char> type are consistent with both the Unicode standard and the <xref:System.Globalization.CharUnicodeInfo> type.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="ce3b1-128">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ce3b1-128">Affected APIs</span></span>

- <xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName>
- <xref:System.Char.IsLetter%2A?displayProperty=fullName>
- <xref:System.Char.IsPunctuation%2A?displayProperty=fullName>
- <xref:System.Char.IsSymbol%2A?displayProperty=fullName>
- <xref:System.Char.IsLower%2A?displayProperty=fullName>

<span data-ttu-id="ce3b1-129">此外，任何依賴 <xref:System.Char> 來取得 Unicode 字元類別目錄的類別（例如） <xref:System.Text.RegularExpressions.Regex> 都會受到這項變更的影響。</span><span class="sxs-lookup"><span data-stu-id="ce3b1-129">Additionally, any class that depends on <xref:System.Char> to obtain the Unicode character category, for example, <xref:System.Text.RegularExpressions.Regex>, is affected by this change.</span></span>

<!--

### Affected APIs

- `Overload:System.Char.GetUnicodeCategory`
- `Overload:System.Char.IsLetter`
- `Overload:System.Char.IsPunctuation`
- `Overload:System.Char.IsSymbol`
- `Overload:System.Char.IsLower`

### Category

- Core .NET libraries
- Globalization
-
-->
