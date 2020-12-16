---
title: SYSLIB0008 警告
description: 瞭解產生編譯時期警告 SYSLIB0008 的 obsoletion。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 2b573f4b28cdf79107395f5cb38a4226d0ccc11e
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596441"
---
# <a name="syslib0008-createpdbgenerator-is-not-supported"></a><span data-ttu-id="18992-103">SYSLIB0008：不支援 CreatePdbGenerator</span><span class="sxs-lookup"><span data-stu-id="18992-103">SYSLIB0008: CreatePdbGenerator is not supported</span></span>

<span data-ttu-id="18992-104"><xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType>API 已標示為過時，從 .net 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="18992-104">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> API is marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="18992-105">使用這個 API 會 `SYSLIB0008` 在編譯時期產生警告。</span><span class="sxs-lookup"><span data-stu-id="18992-105">Using this API generates warning `SYSLIB0008` at compile time.</span></span>

## <a name="suppress-the-warning"></a><span data-ttu-id="18992-106">隱藏警告</span><span class="sxs-lookup"><span data-stu-id="18992-106">Suppress the warning</span></span>

<span data-ttu-id="18992-107">如果您無法變更程式碼，您可以透過指示詞 `#pragma` 或專案設定來隱藏警告 `<NoWarn>` 。</span><span class="sxs-lookup"><span data-stu-id="18992-107">If you cannot change your code, you can suppress the warning through a `#pragma` directive or a `<NoWarn>` project setting.</span></span> <span data-ttu-id="18992-108">如需範例，請參閱 [隱藏警告](../syslib-obsoletions.md#suppress-warnings)。</span><span class="sxs-lookup"><span data-stu-id="18992-108">For examples, see [Suppress warnings](../syslib-obsoletions.md#suppress-warnings).</span></span>
