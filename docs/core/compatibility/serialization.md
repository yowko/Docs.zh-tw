---
title: 序列化的重大變更
description: 列出 .NET Core 和 .NET 5.0 和更新版本中序列化類別的重大變更。
ms.date: 07/30/2020
ms.openlocfilehash: 67608c8e7a9745c060b7eb179fe5a956ede9f80f
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332872"
---
# <a name="serialization-breaking-changes"></a><span data-ttu-id="6696a-103">序列化的重大變更</span><span class="sxs-lookup"><span data-stu-id="6696a-103">Serialization breaking changes</span></span>

<span data-ttu-id="6696a-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="6696a-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="6696a-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="6696a-105">Breaking change</span></span> | <span data-ttu-id="6696a-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="6696a-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="6696a-107">ASP.NET Core apps 允許將引號數位還原序列化</span><span class="sxs-lookup"><span data-stu-id="6696a-107">ASP.NET Core apps allow deserializing quoted numbers</span></span>](#aspnet-core-apps-allow-deserializing-quoted-numbers) | <span data-ttu-id="6696a-108">5.0</span><span class="sxs-lookup"><span data-stu-id="6696a-108">5.0</span></span> |
| [<span data-ttu-id="6696a-109">序列化和還原序列化機碼值組時，會接受 PropertyNamingPolicy、PropertyNameCaseInsensitive 和編碼器選項</span><span class="sxs-lookup"><span data-stu-id="6696a-109">PropertyNamingPolicy, PropertyNameCaseInsensitive, and Encoder options are honored when serializing and deserializing key-value pairs</span></span>](#propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs) | <span data-ttu-id="6696a-110">5.0</span><span class="sxs-lookup"><span data-stu-id="6696a-110">5.0</span></span> |
| [<span data-ttu-id="6696a-111">非公用、無參數的函式不會用於還原序列化</span><span class="sxs-lookup"><span data-stu-id="6696a-111">Non-public, parameterless constructors not used for deserialization</span></span>](#non-public-parameterless-constructors-not-used-for-deserialization) | <span data-ttu-id="6696a-112">5.0</span><span class="sxs-lookup"><span data-stu-id="6696a-112">5.0</span></span> |
| [<span data-ttu-id="6696a-113">JsonSerializer。當型別參數為 null 時，序列化會擲回 System.argumentnullexception</span><span class="sxs-lookup"><span data-stu-id="6696a-113">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="6696a-114">5.0</span><span class="sxs-lookup"><span data-stu-id="6696a-114">5.0</span></span> |
| [<span data-ttu-id="6696a-115">JsonSerializer。還原序列化需要單一字元字串</span><span class="sxs-lookup"><span data-stu-id="6696a-115">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="6696a-116">5.0</span><span class="sxs-lookup"><span data-stu-id="6696a-116">5.0</span></span> |
| [<span data-ttu-id="6696a-117">BinaryFormatter。還原序列化 rewraps SerializationException 中的一些例外狀況</span><span class="sxs-lookup"><span data-stu-id="6696a-117">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="6696a-118">5.0</span><span class="sxs-lookup"><span data-stu-id="6696a-118">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="6696a-119">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="6696a-119">.NET 5.0</span></span>

[!INCLUDE [jsonserializer-allows-reading-numbers-as-strings](../../../includes/core-changes/serialization/5.0/jsonserializer-allows-reading-numbers-as-strings.md)]

***

[!INCLUDE [options-honored-when-serializing-key-value-pairs](../../../includes/core-changes/serialization/5.0/options-honored-when-serializing-key-value-pairs.md)]

<span data-ttu-id="6696a-120">\*\*_</span><span class="sxs-lookup"><span data-stu-id="6696a-120">\*\*_</span></span>

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

_*_

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

_*_

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

_*_

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

<span data-ttu-id="6696a-121">_\*\*</span><span class="sxs-lookup"><span data-stu-id="6696a-121">_\*\*</span></span>
