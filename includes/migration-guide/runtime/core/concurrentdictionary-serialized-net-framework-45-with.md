---
ms.openlocfilehash: f9d7b8d22818245b96cafffe3732bdfe82ff69d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803529"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a>在 .NET Framework 4.5 中利用 NetDataContractSerializer 序列化過的 ConcurrentDictionary，無法由 .NET Framework 4.5.1 或 4.5.2 還原序列化

|   |   |
|---|---|
|詳細資料|由於此類型的內部變更，使用 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> 以 .NET Framework 4.5 序列化的 <xref:System.Collections.Concurrent.ConcurrentDictionary%602> 物件，無法在 .NET Framework 4.5.1 或 .NET Framework 4.5.2 中還原序列化。請注意，反向移動 (以 .NET Framework 4.5.x 序列化並以 .NET Framework 4.5 還原序列化) 則運作正常。 同樣地，所有 4.x 跨版本序列化在 .NET Framework 4.6 中都會正常運作。以單一 .NET Framework 版本進行序列化和還原序列化則不受影響。|
|建議|如果必須在 .NET Framework 4.5 和 .NET Framework 4.5.1/4.5.2 之間序列化和還原序列化 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name>，則應該使用替代的序列化程式 (例如 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> 或 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> 序列化程式) 來取代 <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name>。此外，由於此問題已在 .NET Framework 4.6 中解決，因此可藉由升級至該版 .NET Framework 來解決。|
|範圍|次要|
|版本|4.5.1|
|類型|執行階段|
