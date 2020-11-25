---
title: Windows Forms 重大變更
description: 列出 .NET Core 3.0 和 3.1 Windows Forms 的重大變更。
ms.date: 09/08/2020
ms.openlocfilehash: b944f7eea89b61f41feb8eef99e949c2d6017960
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726427"
---
# <a name="breaking-changes-in-windows-forms-for-net-core-30-and-31"></a><span data-ttu-id="dbf29-103">.NET Core 3.0 和 3.1 Windows Forms 的重大變更</span><span class="sxs-lookup"><span data-stu-id="dbf29-103">Breaking changes in Windows Forms for .NET Core 3.0 and 3.1</span></span>

<span data-ttu-id="dbf29-104">版本3.0 中的 .NET Core 已新增 Windows Forms 支援。</span><span class="sxs-lookup"><span data-stu-id="dbf29-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="dbf29-105">本文列出所引進之 .NET 版本 Windows Forms 的重大變更。</span><span class="sxs-lookup"><span data-stu-id="dbf29-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="dbf29-106">如果您要從 .NET Framework 或舊版 .NET Core (3.0 或更新版本的) 升級 Windows Forms 應用程式，本文適用于您。</span><span class="sxs-lookup"><span data-stu-id="dbf29-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="dbf29-107">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="dbf29-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="dbf29-108">重大變更</span><span class="sxs-lookup"><span data-stu-id="dbf29-108">Breaking change</span></span> | <span data-ttu-id="dbf29-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="dbf29-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="dbf29-110">已移除控制項</span><span class="sxs-lookup"><span data-stu-id="dbf29-110">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="dbf29-111">3.1</span><span class="sxs-lookup"><span data-stu-id="dbf29-111">3.1</span></span> |
| [<span data-ttu-id="dbf29-112">如果顯示工具提示，則不會引發 CellFormatting 事件</span><span class="sxs-lookup"><span data-stu-id="dbf29-112">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="dbf29-113">3.1</span><span class="sxs-lookup"><span data-stu-id="dbf29-113">3.1</span></span> |
| [<span data-ttu-id="dbf29-114">DefaultFont 變更為 Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="dbf29-114">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="dbf29-115">3.0</span><span class="sxs-lookup"><span data-stu-id="dbf29-115">3.0</span></span> |
| [<span data-ttu-id="dbf29-116">FolderBrowserDialog 的現代化</span><span class="sxs-lookup"><span data-stu-id="dbf29-116">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="dbf29-117">3.0</span><span class="sxs-lookup"><span data-stu-id="dbf29-117">3.0</span></span> |
| [<span data-ttu-id="dbf29-118">SerializableAttribute 已從部分 Windows Forms 類型中移除</span><span class="sxs-lookup"><span data-stu-id="dbf29-118">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="dbf29-119">3.0</span><span class="sxs-lookup"><span data-stu-id="dbf29-119">3.0</span></span> |
| [<span data-ttu-id="dbf29-120">不支援 AllowUpdateChildControlIndexForTabControls 相容性參數</span><span class="sxs-lookup"><span data-stu-id="dbf29-120">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="dbf29-121">3.0</span><span class="sxs-lookup"><span data-stu-id="dbf29-121">3.0</span></span> |
| [<span data-ttu-id="dbf29-122">不支援 DomainUpDown UseLegacyScrolling 相容性參數</span><span class="sxs-lookup"><span data-stu-id="dbf29-122">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="dbf29-123">3.0</span><span class="sxs-lookup"><span data-stu-id="dbf29-123">3.0</span></span> |
| [<span data-ttu-id="dbf29-124">不支援 DoNotLoadLatestRichEditControl 相容性參數</span><span class="sxs-lookup"><span data-stu-id="dbf29-124">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="dbf29-125">3.0</span><span class="sxs-lookup"><span data-stu-id="dbf29-125">3.0</span></span> |
| [<span data-ttu-id="dbf29-126">不支援 DoNotSupportSelectAllShortcutInMultilineTextBox 相容性參數</span><span class="sxs-lookup"><span data-stu-id="dbf29-126">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="dbf29-127">3.0</span><span class="sxs-lookup"><span data-stu-id="dbf29-127">3.0</span></span> |
| [<span data-ttu-id="dbf29-128">不支援 >dontsupportreentrantfiltermessage 相容性參數</span><span class="sxs-lookup"><span data-stu-id="dbf29-128">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="dbf29-129">3.0</span><span class="sxs-lookup"><span data-stu-id="dbf29-129">3.0</span></span> |
| [<span data-ttu-id="dbf29-130">不支援 EnableVisualStyleValidation 相容性參數</span><span class="sxs-lookup"><span data-stu-id="dbf29-130">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="dbf29-131">3.0</span><span class="sxs-lookup"><span data-stu-id="dbf29-131">3.0</span></span> |
| [<span data-ttu-id="dbf29-132">不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性參數</span><span class="sxs-lookup"><span data-stu-id="dbf29-132">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="dbf29-133">3.0</span><span class="sxs-lookup"><span data-stu-id="dbf29-133">3.0</span></span> |
| [<span data-ttu-id="dbf29-134">不支援 UseLegacyImages 相容性參數</span><span class="sxs-lookup"><span data-stu-id="dbf29-134">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="dbf29-135">3.0</span><span class="sxs-lookup"><span data-stu-id="dbf29-135">3.0</span></span> |

## <a name="net-core-31"></a><span data-ttu-id="dbf29-136">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="dbf29-136">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

<span data-ttu-id="dbf29-137">\*\*_</span><span class="sxs-lookup"><span data-stu-id="dbf29-137">\*\*_</span></span>

## <a name="net-core-30"></a><span data-ttu-id="dbf29-138">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="dbf29-138">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

_*_

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

_*_

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

_*_

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

<span data-ttu-id="dbf29-139">_\*\*</span><span class="sxs-lookup"><span data-stu-id="dbf29-139">_\*\*</span></span>

## <a name="see-also"></a><span data-ttu-id="dbf29-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbf29-140">See also</span></span>

- [<span data-ttu-id="dbf29-141">將 Windows Forms 應用程式移植到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="dbf29-141">Port a Windows Forms app to .NET Core</span></span>](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
