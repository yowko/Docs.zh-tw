---
title: 重大變更-.NET Framework 至 .NET Core
description: 列出從 .NET Framework 到 .NET Core 的重大變更。
ms.date: 12/18/2019
ms.openlocfilehash: 5c29636664632e80e4235e922a3296c34fdbef36
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900128"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="13637-103">從 .NET Framework 遷移至 .NET Core 的突破性變更</span><span class="sxs-lookup"><span data-stu-id="13637-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="13637-104">如果您要將應用程式從 .NET Framework 遷移至 .NET Core，本文中所列的重大變更可能會對您造成影響。</span><span class="sxs-lookup"><span data-stu-id="13637-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="13637-105">重大變更會依類別目錄分組。</span><span class="sxs-lookup"><span data-stu-id="13637-105">Breaking changes are grouped by category.</span></span>

> [!NOTE]
> <span data-ttu-id="13637-106">本文不是 .NET Framework 和 .NET Core 之間的重大變更完整清單。</span><span class="sxs-lookup"><span data-stu-id="13637-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="13637-107">最重要的重大變更會在這裡新增，因為我們會注意到它們。</span><span class="sxs-lookup"><span data-stu-id="13637-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="corefx"></a><span data-ttu-id="13637-108">CoreFx</span><span class="sxs-lookup"><span data-stu-id="13637-108">CoreFx</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

## <a name="windows-forms"></a><span data-ttu-id="13637-109">Windows 表單</span><span class="sxs-lookup"><span data-stu-id="13637-109">Windows Forms</span></span>

<span data-ttu-id="13637-110">如需將 Windows Forms 應用程式從 .NET Framework 遷移至 .NET Core 3.0 或更新版本時的重大變更相關資訊，請參閱[Windows Forms （.NET Framework 至 .Net core）中的重大變更](../porting/winforms-breaking-changes.md)。</span><span class="sxs-lookup"><span data-stu-id="13637-110">For information about breaking changes when you migrate a Windows Forms app from .NET Framework to .NET Core 3.0 or later, see [Breaking changes in Windows Forms (.NET Framework to .NET Core)](../porting/winforms-breaking-changes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="13637-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="13637-111">See also</span></span>

- [<span data-ttu-id="13637-112">在 .NET Core 上一律會擲回例外狀況的 Api</span><span class="sxs-lookup"><span data-stu-id="13637-112">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="13637-113">.NET Core 上無法使用的 .NET Framework 技術</span><span class="sxs-lookup"><span data-stu-id="13637-113">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
