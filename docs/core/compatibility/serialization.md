---
title: 序列化的重大變更
description: 列出 .NET Core 和 .NET 5.0 和更新版本中序列化類別的重大變更。
ms.date: 07/30/2020
ms.openlocfilehash: bb6bd650afeba426edc6e102076f05f97f8e0598
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050456"
---
# <a name="serialization-breaking-changes"></a><span data-ttu-id="fe582-103">序列化的重大變更</span><span class="sxs-lookup"><span data-stu-id="fe582-103">Serialization breaking changes</span></span>

<span data-ttu-id="fe582-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="fe582-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="fe582-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="fe582-105">Breaking change</span></span> | <span data-ttu-id="fe582-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="fe582-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="fe582-107">序列化和還原序列化機碼值組時，會接受 PropertyNamingPolicy、PropertyNameCaseInsensitive 和編碼器選項</span><span class="sxs-lookup"><span data-stu-id="fe582-107">PropertyNamingPolicy, PropertyNameCaseInsensitive, and Encoder options are honored when serializing and deserializing key-value pairs</span></span>](#propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs) | <span data-ttu-id="fe582-108">5.0</span><span class="sxs-lookup"><span data-stu-id="fe582-108">5.0</span></span> |
| [<span data-ttu-id="fe582-109">非公用、無參數的函式不會用於還原序列化</span><span class="sxs-lookup"><span data-stu-id="fe582-109">Non-public, parameterless constructors not used for deserialization</span></span>](#non-public-parameterless-constructors-not-used-for-deserialization) | <span data-ttu-id="fe582-110">5.0</span><span class="sxs-lookup"><span data-stu-id="fe582-110">5.0</span></span> |
| [<span data-ttu-id="fe582-111">JsonSerializer。當型別參數為 null 時，序列化會擲回 System.argumentnullexception</span><span class="sxs-lookup"><span data-stu-id="fe582-111">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="fe582-112">5.0</span><span class="sxs-lookup"><span data-stu-id="fe582-112">5.0</span></span> |
| [<span data-ttu-id="fe582-113">JsonSerializer。還原序列化需要單一字元字串</span><span class="sxs-lookup"><span data-stu-id="fe582-113">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="fe582-114">5.0</span><span class="sxs-lookup"><span data-stu-id="fe582-114">5.0</span></span> |
| [<span data-ttu-id="fe582-115">BinaryFormatter。還原序列化 rewraps SerializationException 中的一些例外狀況</span><span class="sxs-lookup"><span data-stu-id="fe582-115">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="fe582-116">5.0</span><span class="sxs-lookup"><span data-stu-id="fe582-116">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="fe582-117">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="fe582-117">.NET 5.0</span></span>

[!INCLUDE [options-honored-when-serializing-key-value-pairs](../../../includes/core-changes/serialization/5.0/options-honored-when-serializing-key-value-pairs.md)]

***

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

***

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

***

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
