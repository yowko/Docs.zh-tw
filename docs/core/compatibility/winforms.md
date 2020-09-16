---
title: Windows Forms 重大變更
description: 列出適用于 .NET Core 和 .NET 5 的 Windows Forms 中的重大變更。
ms.date: 09/08/2020
ms.openlocfilehash: 3e7d077d07203d9c231ae4a7805e593c5432c135
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678992"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="39070-103">Windows Forms 中的重大變更</span><span class="sxs-lookup"><span data-stu-id="39070-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="39070-104">版本3.0 中的 .NET Core 已新增 Windows Forms 支援。</span><span class="sxs-lookup"><span data-stu-id="39070-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="39070-105">本文列出所引進之 .NET 版本 Windows Forms 的重大變更。</span><span class="sxs-lookup"><span data-stu-id="39070-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="39070-106">如果您要從 .NET Framework 或舊版 .NET Core (3.0 或更新版本的) 升級 Windows Forms 應用程式，本文適用于您。</span><span class="sxs-lookup"><span data-stu-id="39070-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="39070-107">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="39070-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="39070-108">重大變更</span><span class="sxs-lookup"><span data-stu-id="39070-108">Breaking change</span></span> | <span data-ttu-id="39070-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="39070-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="39070-110">適用于 WPF 和 WinForms 應用程式的 OutputType 設定為 WinExe</span><span class="sxs-lookup"><span data-stu-id="39070-110">OutputType set to WinExe for WPF and WinForms apps</span></span>](#outputtype-set-to-winexe-for-wpf-and-winforms-apps) | <span data-ttu-id="39070-111">5.0</span><span class="sxs-lookup"><span data-stu-id="39070-111">5.0</span></span> |
| [<span data-ttu-id="39070-112">DataGridView 相關的 Api 現在會擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="39070-112">DataGridView-related APIs now throw InvalidOperationException</span></span>](#datagridview-related-apis-now-throw-invalidoperationexception) | <span data-ttu-id="39070-113">5.0</span><span class="sxs-lookup"><span data-stu-id="39070-113">5.0</span></span> |
| [<span data-ttu-id="39070-114">WinForms 和 WPF 應用程式使用 Microsoft .NET Sdk</span><span class="sxs-lookup"><span data-stu-id="39070-114">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>](#winforms-and-wpf-apps-use-microsoftnetsdk) | <span data-ttu-id="39070-115">5.0</span><span class="sxs-lookup"><span data-stu-id="39070-115">5.0</span></span> |
| [<span data-ttu-id="39070-116">已移除狀態列控制項</span><span class="sxs-lookup"><span data-stu-id="39070-116">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="39070-117">5.0</span><span class="sxs-lookup"><span data-stu-id="39070-117">5.0</span></span> |
| [<span data-ttu-id="39070-118">WinForms 方法現在會擲回 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="39070-118">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="39070-119">5.0</span><span class="sxs-lookup"><span data-stu-id="39070-119">5.0</span></span> |
| [<span data-ttu-id="39070-120">WinForms 方法現在會擲回 System.argumentnullexception</span><span class="sxs-lookup"><span data-stu-id="39070-120">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="39070-121">5.0</span><span class="sxs-lookup"><span data-stu-id="39070-121">5.0</span></span> |
| [<span data-ttu-id="39070-122">WinForms 屬性現在會擲回 ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="39070-122">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="39070-123">5.0</span><span class="sxs-lookup"><span data-stu-id="39070-123">5.0</span></span> |
| [<span data-ttu-id="39070-124">已移除控制項</span><span class="sxs-lookup"><span data-stu-id="39070-124">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="39070-125">3.1</span><span class="sxs-lookup"><span data-stu-id="39070-125">3.1</span></span> |
| [<span data-ttu-id="39070-126">如果顯示工具提示，則不會引發 CellFormatting 事件</span><span class="sxs-lookup"><span data-stu-id="39070-126">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="39070-127">3.1</span><span class="sxs-lookup"><span data-stu-id="39070-127">3.1</span></span> |
| [<span data-ttu-id="39070-128">DefaultFont 變更為 Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="39070-128">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="39070-129">3.0</span><span class="sxs-lookup"><span data-stu-id="39070-129">3.0</span></span> |
| [<span data-ttu-id="39070-130">FolderBrowserDialog 的現代化</span><span class="sxs-lookup"><span data-stu-id="39070-130">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="39070-131">3.0</span><span class="sxs-lookup"><span data-stu-id="39070-131">3.0</span></span> |
| [<span data-ttu-id="39070-132">SerializableAttribute 已從部分 Windows Forms 類型中移除</span><span class="sxs-lookup"><span data-stu-id="39070-132">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="39070-133">3.0</span><span class="sxs-lookup"><span data-stu-id="39070-133">3.0</span></span> |
| [<span data-ttu-id="39070-134">不支援 AllowUpdateChildControlIndexForTabControls 相容性參數</span><span class="sxs-lookup"><span data-stu-id="39070-134">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="39070-135">3.0</span><span class="sxs-lookup"><span data-stu-id="39070-135">3.0</span></span> |
| [<span data-ttu-id="39070-136">不支援 DomainUpDown UseLegacyScrolling 相容性參數</span><span class="sxs-lookup"><span data-stu-id="39070-136">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="39070-137">3.0</span><span class="sxs-lookup"><span data-stu-id="39070-137">3.0</span></span> |
| [<span data-ttu-id="39070-138">不支援 DoNotLoadLatestRichEditControl 相容性參數</span><span class="sxs-lookup"><span data-stu-id="39070-138">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="39070-139">3.0</span><span class="sxs-lookup"><span data-stu-id="39070-139">3.0</span></span> |
| [<span data-ttu-id="39070-140">不支援 DoNotSupportSelectAllShortcutInMultilineTextBox 相容性參數</span><span class="sxs-lookup"><span data-stu-id="39070-140">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="39070-141">3.0</span><span class="sxs-lookup"><span data-stu-id="39070-141">3.0</span></span> |
| [<span data-ttu-id="39070-142">不支援 >dontsupportreentrantfiltermessage 相容性參數</span><span class="sxs-lookup"><span data-stu-id="39070-142">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="39070-143">3.0</span><span class="sxs-lookup"><span data-stu-id="39070-143">3.0</span></span> |
| [<span data-ttu-id="39070-144">不支援 EnableVisualStyleValidation 相容性參數</span><span class="sxs-lookup"><span data-stu-id="39070-144">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="39070-145">3.0</span><span class="sxs-lookup"><span data-stu-id="39070-145">3.0</span></span> |
| [<span data-ttu-id="39070-146">不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性參數</span><span class="sxs-lookup"><span data-stu-id="39070-146">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="39070-147">3.0</span><span class="sxs-lookup"><span data-stu-id="39070-147">3.0</span></span> |
| [<span data-ttu-id="39070-148">不支援 UseLegacyImages 相容性參數</span><span class="sxs-lookup"><span data-stu-id="39070-148">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="39070-149">3.0</span><span class="sxs-lookup"><span data-stu-id="39070-149">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="39070-150">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="39070-150">.NET 5.0</span></span>

[!INCLUDE [automatically-infer-winexe-output-type](../../../includes/core-changes/windowsforms/5.0/automatically-infer-winexe-output-type.md)]

***

[!INCLUDE [null-owner-causes-invalidoperationexception](../../../includes/core-changes/windowsforms/5.0/null-owner-causes-invalidoperationexception.md)]

***

[!INCLUDE [sdk-and-target-framework-change](../../../includes/core-changes/windowsforms/5.0/sdk-and-target-framework-change.md)]

***

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

***

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

***

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

[!INCLUDE [invalid-args-cause-argumentoutofrangeexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentoutofrangeexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="39070-151">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="39070-151">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="39070-152">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="39070-152">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

## <a name="see-also"></a><span data-ttu-id="39070-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39070-153">See also</span></span>

- [<span data-ttu-id="39070-154">將 Windows Forms 應用程式移植到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="39070-154">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
