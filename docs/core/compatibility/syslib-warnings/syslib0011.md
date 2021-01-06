---
title: SYSLIB0011 警告
description: 瞭解產生編譯時期警告 SYSLIB0011 的 obsoletions。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 36292cc5314e2b7677d705780880b7e25ae0dfb6
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596473"
---
# <a name="syslib0011-binaryformatter-serialization-is-obsolete"></a><span data-ttu-id="6b4d7-103">SYSLIB0011： BinaryFormatter 序列化已淘汰</span><span class="sxs-lookup"><span data-stu-id="6b4d7-103">SYSLIB0011: BinaryFormatter serialization is obsolete</span></span>

<span data-ttu-id="6b4d7-104">由於中的 [安全性弱點](../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ，下列 api 會標示為已淘汰，從 .net 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="6b4d7-104">Due to [security vulnerabilities](../../../standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) in <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, the following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="6b4d7-105">在程式碼中使用它們會 `SYSLIB0011` 在編譯時期產生警告。</span><span class="sxs-lookup"><span data-stu-id="6b4d7-105">Using them in code generates warning `SYSLIB0011` at compile time.</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="6b4d7-106">因應措施</span><span class="sxs-lookup"><span data-stu-id="6b4d7-106">Workarounds</span></span>

<span data-ttu-id="6b4d7-107">請考慮使用 <xref:System.Text.Json.JsonSerializer> 或， <xref:System.Xml.Serialization.XmlSerializer> 而不是 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 。</span><span class="sxs-lookup"><span data-stu-id="6b4d7-107">Consider using <xref:System.Text.Json.JsonSerializer> or <xref:System.Xml.Serialization.XmlSerializer> instead of <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span>

<span data-ttu-id="6b4d7-108">如需建議動作的詳細資訊，請參閱 [解決 BinaryFormatter obsoletion 和停用錯誤](https://aka.ms/binaryformatter)。</span><span class="sxs-lookup"><span data-stu-id="6b4d7-108">For more information about recommended actions, see [Resolving BinaryFormatter obsoletion and disablement errors](https://aka.ms/binaryformatter).</span></span>

[!INCLUDE [suppress-syslib-warning](../../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="6b4d7-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b4d7-109">See also</span></span>

- [<span data-ttu-id="6b4d7-110">解決 BinaryFormatter obsoletion 和停用錯誤</span><span class="sxs-lookup"><span data-stu-id="6b4d7-110">Resolving BinaryFormatter obsoletion and disablement errors</span></span>](https://aka.ms/binaryformatter)
- [<span data-ttu-id="6b4d7-111">ASP.NET apps 已淘汰且禁止 BinaryFormatter 序列化方法</span><span class="sxs-lookup"><span data-stu-id="6b4d7-111">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](../core-libraries/5.0/binaryformatter-serialization-obsolete.md)