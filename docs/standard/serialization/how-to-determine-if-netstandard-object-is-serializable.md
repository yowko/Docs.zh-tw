---
title: 如何判斷 .NET Standard 物件是否可序列化
description: 示範如何判斷是否可以在執行時間序列化 .NET Standard 型別。
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.openlocfilehash: a425d44ac3b58a568bd51e638f28a2b76ced9dec
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223986"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a>如何判斷 .NET Standard 物件是否可序列化

.NET Standard 是一種規格，可定義必須存在於符合該標準版本之特定 .NET 執行的類型和成員。 但是，.NET Standard 不會定義類型是否可序列化。 .NET Standard 程式庫中定義的類型不會以屬性標記 <xref:System.SerializableAttribute> 。 相反地，特定的 .NET 執行（例如 .NET Framework 和 .NET Core）可以用來判斷特定類型是否可序列化。

如果您已開發以 .NET Standard 為目標的程式庫，則任何支援 .NET Standard 的 .NET 執行都可使用您的程式庫。 這表示您無法事先知道特定類型是否可序列化;您只能判斷它是否可在執行時間進行序列化。

您可以藉由抓取物件 <xref:System.Type.IsSerializable> （代表物件的型別）的屬性值，判斷物件是否可在執行時間進行序列化 <xref:System.Type> 。 下列範例提供一個實作為。 它會定義 `IsSerializable(Object)` 擴充方法，以指出是否 <xref:System.Object> 可以序列化任何實例。

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

然後，您可以將任何物件傳遞至方法，以判斷是否可以在目前的 .NET 執行上序列化和還原序列化，如下列範例所示：

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a>另請參閱

- [二進位序列化](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
