---
title: 重大變更：加密功能僅限功能初始化
description: 瞭解 .NET 5.0 中的重大變更，在此情況下，如果您嘗試變更值，則在密碼編譯的屬性 setter 現在會擲回例外狀況。
ms.date: 08/16/2020
ms.openlocfilehash: a3b5a393e2a84f7c9a60c2a821ecfda9c6acd2e3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760462"
---
# <a name="systemsecuritycryptographyoid-is-functionally-init-only"></a><span data-ttu-id="bb8f5-103">在功能上，加密功能僅限初始化</span><span class="sxs-lookup"><span data-stu-id="bb8f5-103">System.Security.Cryptography.Oid is functionally init-only</span></span>

<span data-ttu-id="bb8f5-104"><xref:System.Security.Cryptography.Oid?displayProperty=fullName>用來代表 Asn.1 物件識別碼值和其「易記」名稱的類別，先前是完全可變動的。</span><span class="sxs-lookup"><span data-stu-id="bb8f5-104">The <xref:System.Security.Cryptography.Oid?displayProperty=fullName> class, which is used to represent ASN.1 Object Identifier values and their "friendly" names, was previously fully mutable.</span></span> <span data-ttu-id="bb8f5-105">這種可變動性經常被忽略，或令人驚訝。</span><span class="sxs-lookup"><span data-stu-id="bb8f5-105">This mutability was often overlooked or came as a surprise.</span></span> <span data-ttu-id="bb8f5-106"><xref:System.PlatformNotSupportedException>當您嘗試在已指派值之後變更該值時，屬性 setter 現在會擲回。</span><span class="sxs-lookup"><span data-stu-id="bb8f5-106">The property setters now throw a <xref:System.PlatformNotSupportedException> when you attempt to change the value after it's already been assigned.</span></span>

## <a name="change-description"></a><span data-ttu-id="bb8f5-107">變更描述</span><span class="sxs-lookup"><span data-stu-id="bb8f5-107">Change description</span></span>

<span data-ttu-id="bb8f5-108">在先前的版本中，屬性 setter <xref:System.Security.Cryptography.Oid> 可以用來變更 <xref:System.Security.Cryptography.Oid.FriendlyName> 和屬性的值 <xref:System.Security.Cryptography.Oid.Value> 。</span><span class="sxs-lookup"><span data-stu-id="bb8f5-108">In previous versions, the property setters on <xref:System.Security.Cryptography.Oid> can be used to change the value of the <xref:System.Security.Cryptography.Oid.FriendlyName> and <xref:System.Security.Cryptography.Oid.Value> properties.</span></span>

<span data-ttu-id="bb8f5-109">在 .NET 5.0 和更新版本中，屬性 setter 只能用來初始化值。</span><span class="sxs-lookup"><span data-stu-id="bb8f5-109">In .NET 5.0 and later versions, the property setters can only be used to initialize the value.</span></span> <span data-ttu-id="bb8f5-110">一旦屬性具有值（從函式或先前對屬性 setter 的呼叫），屬性 setter 一律會擲回 <xref:System.PlatformNotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="bb8f5-110">Once the property has a value, either from a constructor or a previous call to the property setter, the property setter always throws a <xref:System.PlatformNotSupportedException>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="bb8f5-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="bb8f5-111">Reason for change</span></span>

<span data-ttu-id="bb8f5-112">這項變更可讓您在 <xref:System.Security.Cryptography.Oid> 公用 api 中重複使用物件作為傳回值的一部分，以減少物件配置設定檔。</span><span class="sxs-lookup"><span data-stu-id="bb8f5-112">This change enables the reuse of <xref:System.Security.Cryptography.Oid> objects as part of return values in public APIs to reduce object allocation profiles.</span></span> <span data-ttu-id="bb8f5-113">它可避免在將值當做輸入使用時，建立暫時的「防禦」複本 <xref:System.Security.Cryptography.Oid> 。</span><span class="sxs-lookup"><span data-stu-id="bb8f5-113">It avoids the need to create temporary "defensive" copies when <xref:System.Security.Cryptography.Oid> values are used as inputs.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="bb8f5-114">引進的版本</span><span class="sxs-lookup"><span data-stu-id="bb8f5-114">Version introduced</span></span>

<span data-ttu-id="bb8f5-115">5.0</span><span class="sxs-lookup"><span data-stu-id="bb8f5-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="bb8f5-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="bb8f5-116">Recommended action</span></span>

<span data-ttu-id="bb8f5-117">避免使用 <xref:System.Security.Cryptography.Oid> 屬性 setter （用於物件初始化）。</span><span class="sxs-lookup"><span data-stu-id="bb8f5-117">Avoid using the <xref:System.Security.Cryptography.Oid> property setters other than for object initialization.</span></span> <span data-ttu-id="bb8f5-118">若要代表新的值，請使用新的實例，而不是變更現有物件的值。</span><span class="sxs-lookup"><span data-stu-id="bb8f5-118">To represent a new value, use a new instance instead of changing the value on an existing object.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="bb8f5-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="bb8f5-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Oid.FriendlyName?displayProperty=fullName>
- <xref:System.Security.Cryptography.Oid.Value?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Security.Cryptography.Oid.FriendlyName`
- `P:System.Security.Cryptography.Oid.Value`

### Category

Cryptography

-->
