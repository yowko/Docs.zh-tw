---
title: 重大變更：還原序列化 char 需要單一字元字串
description: 瞭解 .NET 5.0 中的重大變更，在此情況下，System.Text.Json 在還原序列化至 char 目標時需要 JSON 中的單一字元字串。
ms.date: 12/15/2020
ms.openlocfilehash: 39a2d25b00bf8855cfbf46a4d78b8545052703e5
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633867"
---
# <a name="systemtextjson-requires-single-char-string-to-deserialize-a-char"></a><span data-ttu-id="1a4d5-103">System.Text.Json 需要單一字元字串才能還原序列化字元</span><span class="sxs-lookup"><span data-stu-id="1a4d5-103">System.Text.Json requires single-char string to deserialize a char</span></span>

<span data-ttu-id="1a4d5-104">若要使用成功還原序列化 <xref:System.Char> <xref:System.Text.Json> ，JSON 字串必須包含單一字元。</span><span class="sxs-lookup"><span data-stu-id="1a4d5-104">To successfully deserialize a <xref:System.Char> using <xref:System.Text.Json>, the JSON string must contain a single character.</span></span>

## <a name="change-description"></a><span data-ttu-id="1a4d5-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="1a4d5-105">Change description</span></span>

<span data-ttu-id="1a4d5-106">在先前的 .NET 版本中，JSON 中的多字串已成功還原序列化 `char` 為 `char` 屬性或欄位。</span><span class="sxs-lookup"><span data-stu-id="1a4d5-106">In previous .NET versions, a multi-`char` string in the JSON is successfully deserialized to a `char` property or field.</span></span> <span data-ttu-id="1a4d5-107">只 `char` 會使用第一個字串，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1a4d5-107">Only the first `char` of the string is used, as in the following example:</span></span>

```csharp
// .NET Core 3.0 and 3.1: Returns the first char 'a'.
// .NET 5.0 and later: Throws JsonException because payload has more than one char.
char deserializedChar = JsonSerializer.Deserialize<char>("\"abc\"");
```

<span data-ttu-id="1a4d5-108">在 .NET 5.0 和更新版本中，單一字串以外的任何其他作業都會導致在還原序列化 `char` <xref:System.Text.Json.JsonException> 目標為時擲回 `char` 。</span><span class="sxs-lookup"><span data-stu-id="1a4d5-108">In .NET 5.0 and later, anything other than a single-`char` string causes a <xref:System.Text.Json.JsonException> to be thrown when the deserialization target is a `char`.</span></span> <span data-ttu-id="1a4d5-109">下列範例字串已在所有 .NET 版本中成功還原序列化：</span><span class="sxs-lookup"><span data-stu-id="1a4d5-109">The following example string is successfully deserialized in all .NET versions:</span></span>

```csharp
// Correct usage.
char deserializedChar = JsonSerializer.Deserialize<char>("\"a\"");
```

## <a name="version-introduced"></a><span data-ttu-id="1a4d5-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="1a4d5-110">Version introduced</span></span>

<span data-ttu-id="1a4d5-111">5.0</span><span class="sxs-lookup"><span data-stu-id="1a4d5-111">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="1a4d5-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="1a4d5-112">Reason for change</span></span>

<span data-ttu-id="1a4d5-113">只有當提供的裝載對目標型別有效時，才應該成功剖析還原序列化。</span><span class="sxs-lookup"><span data-stu-id="1a4d5-113">Parsing for deserialization should only succeed when the provided payload is valid for the target type.</span></span> <span data-ttu-id="1a4d5-114">針對 `char` 類型，唯一有效的承載是單一 `char` 字串。</span><span class="sxs-lookup"><span data-stu-id="1a4d5-114">For a `char` type, the only valid payload is a single-`char` string.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="1a4d5-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="1a4d5-115">Recommended action</span></span>

<span data-ttu-id="1a4d5-116">當您將 JSON 還原序列化為 `char` 目標時，請確定該字串包含單一 `char` 。</span><span class="sxs-lookup"><span data-stu-id="1a4d5-116">When you deserialize JSON into a `char` target, make sure the string consists of a single `char`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="1a4d5-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1a4d5-117">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`

### Category

Serialization

-->
