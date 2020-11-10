---
title: SYSLIB0010 警告
description: 瞭解產生編譯時期警告 SYSLIB0010 的 obsoletions。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 824423d58802d4a286bfed98422341097985990f
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440604"
---
# <a name="syslib0010-unsupported-remoting-apis"></a><span data-ttu-id="0ec6a-103">SYSLIB0010：不支援的遠端 Api</span><span class="sxs-lookup"><span data-stu-id="0ec6a-103">SYSLIB0010: Unsupported remoting APIs</span></span>

<span data-ttu-id="0ec6a-104">[.Net 遠端處理](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) 是一種舊版技術，基礎結構只存在於 .NET Framework 中。</span><span class="sxs-lookup"><span data-stu-id="0ec6a-104">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) is a legacy technology, and the infrastructure exists only in .NET Framework.</span></span> <span data-ttu-id="0ec6a-105">從 .NET 5.0 開始，下列遠端相關的 Api 會標示為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="0ec6a-105">The following remoting-related APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="0ec6a-106">在程式碼中使用它們會 `SYSLIB0010` 在編譯時期產生警告。</span><span class="sxs-lookup"><span data-stu-id="0ec6a-106">Using them in code generates warning `SYSLIB0010` at compile time.</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="0ec6a-107">因應措施</span><span class="sxs-lookup"><span data-stu-id="0ec6a-107">Workarounds</span></span>

<span data-ttu-id="0ec6a-108">請考慮使用以 WCF 或 HTTP 為基礎的 REST 服務，與其他應用程式或電腦之間的物件進行通訊。</span><span class="sxs-lookup"><span data-stu-id="0ec6a-108">Consider using WCF or HTTP-based REST services to communicate with objects in other applications or across machines.</span></span> <span data-ttu-id="0ec6a-109">如需詳細資訊，請參閱 [.NET FRAMEWORK .Net Core 上無法使用的技術](../porting/net-framework-tech-unavailable.md)。</span><span class="sxs-lookup"><span data-stu-id="0ec6a-109">For more information, see [.NET Framework technologies unavailable on .NET Core](../porting/net-framework-tech-unavailable.md).</span></span>

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]

## <a name="see-also"></a><span data-ttu-id="0ec6a-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="0ec6a-110">See also</span></span>

- <span data-ttu-id="0ec6a-111">[.NET 遠端處理](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))</span><span class="sxs-lookup"><span data-stu-id="0ec6a-111">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))</span></span>
