---
title: NETSDK1079：以 .NET Core 3.0 或更高版本為目標時，不支援 AspNetCore. 所有套件。
description: 如何解決 AspNetCore 應用程式的遷移
author: dsplaisted
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1079
ms.openlocfilehash: e0b7aba909dbd2931f755238a2de2418d294751d
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445749"
---
# <a name="netsdk1079-the-microsoftaspnetcoreall-package-is-not-supported-when-targeting-net-core-30-or-higher"></a><span data-ttu-id="7b0f6-103">NETSDK1079：以 .NET Core 3.0 或更高版本為目標時，不支援 AspNetCore. 所有套件。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-103">NETSDK1079: The Microsoft.AspNetCore.All package is not supported when targeting .NET Core 3.0 or higher.</span></span>

<span data-ttu-id="7b0f6-104">本文 **適用于：** ✔️ .NET Core SDK 3.1.100 和更新版本</span><span class="sxs-lookup"><span data-stu-id="7b0f6-104">**This article applies to:** ✔️ .NET Core SDK 3.1.100 and later versions</span></span>

<span data-ttu-id="7b0f6-105">當下列情況時，您可能會收到此錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="7b0f6-105">You may receive this error message when:</span></span>

- <span data-ttu-id="7b0f6-106">您將 ASP.NET Core 專案從 .NET Core 2.2 或更舊版本重定為 .NET Core 3.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-106">You retarget an ASP.NET Core project from .NET Core 2.2 or earlier to .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="7b0f6-107">專案會使用 AspNetCore. All 套件。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-107">The project uses the Microsoft.AspNetCore.All package.</span></span>

<span data-ttu-id="7b0f6-108">移除 AspNetCore 的。 `PackageReference`</span><span class="sxs-lookup"><span data-stu-id="7b0f6-108">Remove the `PackageReference` for Microsoft.AspNetCore.All.</span></span>  <span data-ttu-id="7b0f6-109">您也可能需要為 AspNetCore 所參考的封裝新增套件參考，但不包含在 ASP.NET Core 的共用架構中。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-109">You may also need to add package references for packages that were referenced from Microsoft.AspNetCore.All but are not included in the ASP.NET Core shared framework.</span></span>  <span data-ttu-id="7b0f6-110">這些套件列在這裡：[從 AspNetCore 遷移至 AspNetCore。](/aspnet/core/fundamentals/metapackage#migrating-from-microsoftaspnetcoreall-to-microsoftaspnetcoreapp)</span><span class="sxs-lookup"><span data-stu-id="7b0f6-110">These packages are listed here: [Migrating from Microsoft.AspNetCore.All to Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage#migrating-from-microsoftaspnetcoreall-to-microsoftaspnetcoreapp).</span></span>

<span data-ttu-id="7b0f6-111">另請參閱 [從 ASP.NET Core 2.2 遷移至 3.0](/aspnet/core/migration/22-to-30)</span><span class="sxs-lookup"><span data-stu-id="7b0f6-111">See also [Migrate from ASP.NET Core 2.2 to 3.0](/aspnet/core/migration/22-to-30)</span></span>
