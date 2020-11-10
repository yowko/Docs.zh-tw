---
title: SYSLIB0009 警告
description: 瞭解產生編譯時期警告 SYSLIB0009 的 obsoletions。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 47b4f595a54800370da90f61d838c665df8b6091
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439972"
---
# <a name="syslib0009-the-authenticationmanager-authenticate-and-preauthenticate-methods-are-not-supported"></a><span data-ttu-id="0cab0-103">SYSLIB0009：不支援 AuthenticationManager 驗證和預先驗證方法</span><span class="sxs-lookup"><span data-stu-id="0cab0-103">SYSLIB0009: The AuthenticationManager Authenticate and PreAuthenticate methods are not supported</span></span>

<span data-ttu-id="0cab0-104">下列 Api 會標示為已淘汰，從 .NET 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="0cab0-104">The following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="0cab0-105">使用這些 Api `SYSLIB0009` 時，會在編譯時期產生警告。</span><span class="sxs-lookup"><span data-stu-id="0cab0-105">Use of these APIs generates warning `SYSLIB0009` at compile time.</span></span>

- <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType>
- <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType>

## <a name="suppress-the-warning"></a><span data-ttu-id="0cab0-106">隱藏警告</span><span class="sxs-lookup"><span data-stu-id="0cab0-106">Suppress the warning</span></span>

<span data-ttu-id="0cab0-107">如果您無法變更程式碼，您可以透過指示詞 `#pragma` 或專案設定來隱藏警告 `<NoWarn>` 。</span><span class="sxs-lookup"><span data-stu-id="0cab0-107">If you cannot change your code, you can suppress the warning through a `#pragma` directive or a `<NoWarn>` project setting.</span></span> <span data-ttu-id="0cab0-108">如需範例，請參閱 [隱藏警告](syslib-obsoletions.md#suppress-warnings)。</span><span class="sxs-lookup"><span data-stu-id="0cab0-108">For examples, see [Suppress warnings](syslib-obsoletions.md#suppress-warnings).</span></span>
