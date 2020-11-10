---
title: SYSLIB0008 警告
description: 瞭解產生編譯時期警告 SYSLIB0008 的 obsoletion。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 22ac5b4c5f57ec3f92585ee8d1f8cf278a15dbb0
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440591"
---
# <a name="syslib0008-createpdbgenerator-is-not-supported"></a><span data-ttu-id="16e92-103">SYSLIB0008：不支援 CreatePdbGenerator</span><span class="sxs-lookup"><span data-stu-id="16e92-103">SYSLIB0008: CreatePdbGenerator is not supported</span></span>

<span data-ttu-id="16e92-104"><xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType>API 已標示為過時，從 .net 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="16e92-104">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> API is marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="16e92-105">使用這個 API 會 `SYSLIB0008` 在編譯時期產生警告。</span><span class="sxs-lookup"><span data-stu-id="16e92-105">Using this API generates warning `SYSLIB0008` at compile time.</span></span>

## <a name="suppress-the-warning"></a><span data-ttu-id="16e92-106">隱藏警告</span><span class="sxs-lookup"><span data-stu-id="16e92-106">Suppress the warning</span></span>

<span data-ttu-id="16e92-107">如果您無法變更程式碼，您可以透過指示詞 `#pragma` 或專案設定來隱藏警告 `<NoWarn>` 。</span><span class="sxs-lookup"><span data-stu-id="16e92-107">If you cannot change your code, you can suppress the warning through a `#pragma` directive or a `<NoWarn>` project setting.</span></span> <span data-ttu-id="16e92-108">如需範例，請參閱 [隱藏警告](syslib-obsoletions.md#suppress-warnings)。</span><span class="sxs-lookup"><span data-stu-id="16e92-108">For examples, see [Suppress warnings](syslib-obsoletions.md#suppress-warnings).</span></span>
