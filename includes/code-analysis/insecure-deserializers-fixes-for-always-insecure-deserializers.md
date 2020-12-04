---
author: dotpaul
ms.author: paulming
ms.date: 05/01/2019
ms.topic: include
ms.openlocfilehash: cf944ae9ca200d34a1f0f32e68bf3aee73a9500a
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2020
ms.locfileid: "96585147"
---
- 可能的話，請改用安全的序列化程式，而且 **不允許攻擊者指定任意類型來** 還原序列化。 有些安全的序列化套裝程式括：

  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -永遠不使用 <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType> 。 如果您必須使用類型解析程式，請將已還原序列化的類型限制為預期的清單。
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET-使用 Typenamehandling.none。無。 如果您必須針對 Typenamehandling.none 使用另一個值，請使用自訂 ISerializationBinder 將已還原序列化的類型限制為預期的清單。
  - 通訊協定緩衝區

- 使序列化的資料無法進行篡改。 在序列化之後，以密碼編譯方式簽署序列化的資料。 在還原序列化之前，請先驗證密碼編譯簽章。 保護密碼編譯金鑰免于洩漏和設計金鑰輪替。
