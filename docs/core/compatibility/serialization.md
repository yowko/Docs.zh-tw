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
# <a name="serialization-breaking-changes"></a>序列化的重大變更

此頁面記載了下列重大變更：

| 重大變更 | 引進的版本 |
| - | - |
| [JsonSerializer。還原序列化需要單一字元字串](#jsonserializerdeserialize-requires-single-character-string) | 5.0 |
| [BinaryFormatter。還原序列化 rewraps SerializationException 中的一些例外狀況](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | 5.0 |

## <a name="net-50"></a>.NET 5。0

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

***

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

***
