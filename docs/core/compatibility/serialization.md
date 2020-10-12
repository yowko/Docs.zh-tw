---
title: 序列化的重大變更
description: 列出 .NET Core 和 .NET 5.0 和更新版本中序列化類別的重大變更。
ms.date: 07/30/2020
ms.openlocfilehash: 65006e6fb45ed2d54699c9972e0489e3ac5ac8bc
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955328"
---
# <a name="serialization-breaking-changes"></a><span data-ttu-id="44350-103">序列化的重大變更</span><span class="sxs-lookup"><span data-stu-id="44350-103">Serialization breaking changes</span></span>

<span data-ttu-id="44350-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="44350-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="44350-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="44350-105">Breaking change</span></span> | <span data-ttu-id="44350-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="44350-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="44350-107">JsonSerializer。當型別參數為 null 時，序列化會擲回 System.argumentnullexception</span><span class="sxs-lookup"><span data-stu-id="44350-107">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | <span data-ttu-id="44350-108">5.0</span><span class="sxs-lookup"><span data-stu-id="44350-108">5.0</span></span> |
| [<span data-ttu-id="44350-109">JsonSerializer。還原序列化需要單一字元字串</span><span class="sxs-lookup"><span data-stu-id="44350-109">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="44350-110">5.0</span><span class="sxs-lookup"><span data-stu-id="44350-110">5.0</span></span> |
| [<span data-ttu-id="44350-111">BinaryFormatter。還原序列化 rewraps SerializationException 中的一些例外狀況</span><span class="sxs-lookup"><span data-stu-id="44350-111">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="44350-112">5.0</span><span class="sxs-lookup"><span data-stu-id="44350-112">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="44350-113">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="44350-113">.NET 5.0</span></span>

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

***

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
