---
title: 序列化的重大變更
description: 列出 .NET Core 和 .NET 5.0 和更新版本中序列化類別的重大變更。
ms.date: 07/30/2020
ms.openlocfilehash: d68bb95f4ee2b21a5a5bf002a46a3904543cd4a7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844497"
---
# <a name="serialization-breaking-changes"></a><span data-ttu-id="436f7-103">序列化的重大變更</span><span class="sxs-lookup"><span data-stu-id="436f7-103">Serialization breaking changes</span></span>

<span data-ttu-id="436f7-104">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="436f7-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="436f7-105">重大變更</span><span class="sxs-lookup"><span data-stu-id="436f7-105">Breaking change</span></span> | <span data-ttu-id="436f7-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="436f7-106">Introduced version</span></span> |
| - | - |
| [<span data-ttu-id="436f7-107">JsonSerializer。還原序列化需要單一字元字串</span><span class="sxs-lookup"><span data-stu-id="436f7-107">JsonSerializer.Deserialize requires single-character string</span></span>](#jsonserializerdeserialize-requires-single-character-string) | <span data-ttu-id="436f7-108">5.0</span><span class="sxs-lookup"><span data-stu-id="436f7-108">5.0</span></span> |
| [<span data-ttu-id="436f7-109">BinaryFormatter。還原序列化 rewraps SerializationException 中的一些例外狀況</span><span class="sxs-lookup"><span data-stu-id="436f7-109">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | <span data-ttu-id="436f7-110">5.0</span><span class="sxs-lookup"><span data-stu-id="436f7-110">5.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="436f7-111">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="436f7-111">.NET 5.0</span></span>

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
