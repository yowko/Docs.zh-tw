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
- <span data-ttu-id="9f334-101">可能的話，請改用安全的序列化程式，而且 **不允許攻擊者指定任意類型來** 還原序列化。</span><span class="sxs-lookup"><span data-stu-id="9f334-101">If possible, use a secure serializer instead, and **don't allow an attacker to specify an arbitrary type to deserialize**.</span></span> <span data-ttu-id="9f334-102">有些安全的序列化套裝程式括：</span><span class="sxs-lookup"><span data-stu-id="9f334-102">Some safer serializers include:</span></span>

  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <span data-ttu-id="9f334-103"><xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> -永遠不使用 <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="9f334-103"><xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType> - Never use <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9f334-104">如果您必須使用類型解析程式，請將已還原序列化的類型限制為預期的清單。</span><span class="sxs-lookup"><span data-stu-id="9f334-104">If you must use a type resolver, restrict deserialized types to an expected list.</span></span>
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - <span data-ttu-id="9f334-105">Newtonsoft Json.NET-使用 Typenamehandling.none。無。</span><span class="sxs-lookup"><span data-stu-id="9f334-105">Newtonsoft Json.NET - Use TypeNameHandling.None.</span></span> <span data-ttu-id="9f334-106">如果您必須針對 Typenamehandling.none 使用另一個值，請使用自訂 ISerializationBinder 將已還原序列化的類型限制為預期的清單。</span><span class="sxs-lookup"><span data-stu-id="9f334-106">If you must use another value for TypeNameHandling, restrict deserialized types to an expected list with a custom ISerializationBinder.</span></span>
  - <span data-ttu-id="9f334-107">通訊協定緩衝區</span><span class="sxs-lookup"><span data-stu-id="9f334-107">Protocol Buffers</span></span>

- <span data-ttu-id="9f334-108">使序列化的資料無法進行篡改。</span><span class="sxs-lookup"><span data-stu-id="9f334-108">Make the serialized data tamper-proof.</span></span> <span data-ttu-id="9f334-109">在序列化之後，以密碼編譯方式簽署序列化的資料。</span><span class="sxs-lookup"><span data-stu-id="9f334-109">After serialization, cryptographically sign the serialized data.</span></span> <span data-ttu-id="9f334-110">在還原序列化之前，請先驗證密碼編譯簽章。</span><span class="sxs-lookup"><span data-stu-id="9f334-110">Before deserialization, validate the cryptographic signature.</span></span> <span data-ttu-id="9f334-111">保護密碼編譯金鑰免于洩漏和設計金鑰輪替。</span><span class="sxs-lookup"><span data-stu-id="9f334-111">Protect the cryptographic key from being disclosed and design for key rotations.</span></span>
