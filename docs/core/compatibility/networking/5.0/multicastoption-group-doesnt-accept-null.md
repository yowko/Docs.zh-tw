---
title: 中斷性變更： MulticastOption。群組不接受 null 值
description: 瞭解 .NET 5.0 中的重大變更，其中 MulticastOption 已不再接受 null 值。
ms.date: 08/18/2020
ms.openlocfilehash: 164ac8c2c8dd14f9e0758017e54eeb377f88a7e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760622"
---
# <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a><span data-ttu-id="7b809-103">MulticastOption。群組不接受 null 值</span><span class="sxs-lookup"><span data-stu-id="7b809-103">MulticastOption.Group doesn't accept a null value</span></span>

<span data-ttu-id="7b809-104"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> 不再接受的值 `null` 。</span><span class="sxs-lookup"><span data-stu-id="7b809-104"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> no longer accepts a value of `null`.</span></span> <span data-ttu-id="7b809-105">如果您將屬性設定為 `null` ， <xref:System.ArgumentNullException> 就會擲回。</span><span class="sxs-lookup"><span data-stu-id="7b809-105">If you set the property to `null`, an <xref:System.ArgumentNullException> is thrown.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="7b809-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="7b809-106">Version introduced</span></span>

<span data-ttu-id="7b809-107">5.0</span><span class="sxs-lookup"><span data-stu-id="7b809-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="7b809-108">變更描述</span><span class="sxs-lookup"><span data-stu-id="7b809-108">Change description</span></span>

<span data-ttu-id="7b809-109">在舊版的 .NET 中，您可以將 <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> 屬性設定為 `null` 。</span><span class="sxs-lookup"><span data-stu-id="7b809-109">In previous versions of .NET, you can set the <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> property to `null`.</span></span> <span data-ttu-id="7b809-110">如果 <xref:System.Net.Sockets.MulticastOption> 稍後傳遞至 <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> ，則執行時間會擲回 <xref:System.NullReferenceException> 。</span><span class="sxs-lookup"><span data-stu-id="7b809-110">If the <xref:System.Net.Sockets.MulticastOption> is later passed to <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType>, the runtime throws a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="7b809-111">在 .NET 5.0 和更新版本中， <xref:System.ArgumentNullException> 如果您將屬性設定為，就會擲回 `null` 。</span><span class="sxs-lookup"><span data-stu-id="7b809-111">In .NET 5.0 and later, an <xref:System.ArgumentNullException> is thrown if you set the property to `null`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="7b809-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="7b809-112">Reason for change</span></span>

<span data-ttu-id="7b809-113">為了與架構設計指導方針一致，屬性已更新為如果值為，則會擲回 <xref:System.ArgumentNullException> `null` 。</span><span class="sxs-lookup"><span data-stu-id="7b809-113">To be consistent with the Framework Design Guidelines, the property has been updated to throw an <xref:System.ArgumentNullException> if the value is `null`.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="7b809-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="7b809-114">Recommended action</span></span>

<span data-ttu-id="7b809-115">請確定您未將設定 <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> 為 `null` 。</span><span class="sxs-lookup"><span data-stu-id="7b809-115">Make sure that you don't set <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> to `null`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="7b809-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7b809-116">Affected APIs</span></span>

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

### Category

Networking

-->
