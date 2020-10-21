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
# <a name="serialization-breaking-changes"></a>序列化的重大變更

此頁面記載了下列重大變更：

| 重大變更 | 引進的版本 |
| - | - |
| [ASP.NET Core apps 允許將引號數位還原序列化](#aspnet-core-apps-allow-deserializing-quoted-numbers) | 5.0 |
| [序列化和還原序列化機碼值組時，會接受 PropertyNamingPolicy、PropertyNameCaseInsensitive 和編碼器選項](#propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs) | 5.0 |
| [非公用、無參數的函式不會用於還原序列化](#non-public-parameterless-constructors-not-used-for-deserialization) | 5.0 |
| [JsonSerializer。當型別參數為 null 時，序列化會擲回 System.argumentnullexception](#jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null) | 5.0 |
| [JsonSerializer。還原序列化需要單一字元字串](#jsonserializerdeserialize-requires-single-character-string) | 5.0 |
| [BinaryFormatter。還原序列化 rewraps SerializationException 中的一些例外狀況](#binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception) | 5.0 |

## <a name="net-50"></a>.NET 5。0

[!INCLUDE [jsonserializer-allows-reading-numbers-as-strings](../../../includes/core-changes/serialization/5.0/jsonserializer-allows-reading-numbers-as-strings.md)]

***

[!INCLUDE [options-honored-when-serializing-key-value-pairs](../../../includes/core-changes/serialization/5.0/options-honored-when-serializing-key-value-pairs.md)]

**_

[!INCLUDE [non-public-parameterless-constructors-not-used-for-deserialization](../../../includes/core-changes/serialization/5.0/non-public-parameterless-constructors-not-used-for-deserialization.md)]

_*_

[!INCLUDE [jsonserializer-serialize-throws-argumentnullexception-for-null-type](../../../includes/core-changes/serialization/5.0/jsonserializer-serialize-throws-argumentnullexception-for-null-type.md)]

_*_

[!INCLUDE [deserializing-json-into-char-requires-single-character](../../../includes/core-changes/serialization/5.0/deserializing-json-into-char-requires-single-character.md)]

_*_

[!INCLUDE [binaryformatter-deserialize-rewraps-exceptions](../../../includes/core-changes/serialization/5.0/binaryformatter-deserialize-rewraps-exceptions.md)]

_**
