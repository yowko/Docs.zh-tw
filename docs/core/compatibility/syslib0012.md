---
title: SYSLIB0012 警告
description: 瞭解產生編譯時期警告 SYSLIB0012 的 obsoletions。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: dc139d5c5cb6d6a34d161147b350b3324d15117e
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440578"
---
# <a name="syslib0012-assemblycodebase-and-assemblyescapedcodebase-are-obsolete"></a><span data-ttu-id="ab231-103">SYSLIB0012： Assembly。程式碼基底和 Assembly. EscapedCodeBase 已淘汰</span><span class="sxs-lookup"><span data-stu-id="ab231-103">SYSLIB0012: Assembly.CodeBase and Assembly.EscapedCodeBase are obsolete</span></span>

<span data-ttu-id="ab231-104">下列 Api 會標示為已淘汰，從 .NET 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="ab231-104">The following APIs are marked as obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="ab231-105">在程式碼中使用它們會 `SYSLIB0012` 在編譯時期產生警告。</span><span class="sxs-lookup"><span data-stu-id="ab231-105">Using them in code generates warning `SYSLIB0012` at compile time.</span></span>

- <xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType>
- <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType>

## <a name="workarounds"></a><span data-ttu-id="ab231-106">因應措施</span><span class="sxs-lookup"><span data-stu-id="ab231-106">Workarounds</span></span>

<span data-ttu-id="ab231-107">請改用 <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="ab231-107">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span>

[!INCLUDE [suppress-syslib-warning](../../../includes/suppress-syslib-warning.md)]
