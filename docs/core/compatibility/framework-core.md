---
title: 重大變更，.NET Framework 至 .NET Core 3.0-.NET Core
description: 列出 Windows Forms 和 Windows Presentation Foundation .NET Framework 到 .NET Core 3.0 的重大變更。
ms.date: 09/10/2019
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c658c5bce7a2554bba83f2779a73d9d6af01a342
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "71151538"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core-30"></a><span data-ttu-id="21818-103">從 .NET Framework 遷移至 .NET Core 3.0 的突破性變更</span><span class="sxs-lookup"><span data-stu-id="21818-103">Breaking changes for migration from .NET Framework to .NET Core 3.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="21818-104">本文的結構如下。</span><span class="sxs-lookup"><span data-stu-id="21818-104">This article is under construction.</span></span> <span data-ttu-id="21818-105">這不是 .NET Core 重大變更的完整清單。</span><span class="sxs-lookup"><span data-stu-id="21818-105">This is not a complete list of .NET Core breaking changes.</span></span> <span data-ttu-id="21818-106">如需 .NET Core 重大變更的詳細資訊，您可以在 GitHub 上的 dotnet/檔存放庫中檢查個別的[重大變更問題](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change)。</span><span class="sxs-lookup"><span data-stu-id="21818-106">For more information on .NET Core breaking changes, you can examine individual [breaking changes issues](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) in the dotnet/docs repository on GitHub.</span></span> 

<span data-ttu-id="21818-107">如果您要將 Windows Forms 或 Windows Presentation Foundation 應用程式從 .NET Framework 遷移至 .NET Core 3.0，請參閱下列主題，以取得可能影響您應用程式的重大變更：</span><span class="sxs-lookup"><span data-stu-id="21818-107">If you are migrating a Windows Forms or Windows Presentation Foundation application from .NET Framework to .NET Core 3.0, review the following topics for breaking changes that may affect your app:</span></span>

## <a name="windows-forms"></a><span data-ttu-id="21818-108">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="21818-108">Windows Forms</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacyimages.md)]
