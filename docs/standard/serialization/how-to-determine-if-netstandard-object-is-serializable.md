---
title: 如何判斷是否可序列化的.NET Standard 物件
description: 示範如何判斷在執行階段是否可序列化的.NET Standard 的類型。
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 196e99ab1f1a0baae53c6a1dc295b135e36fbfe0
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580456"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a>如何判斷是否可序列化的.NET Standard 物件

.NET Standard 是定義的類型和成員必須要有特定的.NET 實作符合標準的該版本上的規格。 不過，.NET Standard 並未定義是否可序列化類型。 .NET Standard 程式庫中定義的類型未標示有<xref:System.SerializableAttribute>屬性。 相反地，.NET 特定的實作，例如.NET Framework 和.NET Core，可用來判斷特定的型別是否可序列化。  

如果您已開發目標的.NET Standard 程式庫，您的程式庫可供任何支援.NET Standard 的.NET 實作。 這表示，您無法事先知道特定的型別是否可序列化;您只可以判斷它是否可序列化在執行階段。

您可以判斷物件是否在執行階段可序列化所擷取的值<xref:System.Type.IsSerializable>屬性<xref:System.Type>物件，表示該物件的型別。 下列範例提供一個實作。 它會定義`IsSerializable(Object)`擴充方法，指出是否有任何<xref:System.Object>可以序列化執行個體。

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

然後，您就可以傳遞任何物件至方法，以判斷它是否可以序列化和還原序列化目前的.NET 實作，如下列範例所示：

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a>另請參閱

- [二進位序列化](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
