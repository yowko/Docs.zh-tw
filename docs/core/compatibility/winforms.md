---
title: Windows Forms 重大變更
description: 列出適用于 .NET Core 和 .NET 5 的 Windows Forms 中的重大變更。
ms.date: 09/08/2020
ms.openlocfilehash: c79fd28b5c3b81ae7ddf1ef3f470601108b87705
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440786"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="1eb3d-103">Windows Forms 中的重大變更</span><span class="sxs-lookup"><span data-stu-id="1eb3d-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="1eb3d-104">版本3.0 中的 .NET Core 已新增 Windows Forms 支援。</span><span class="sxs-lookup"><span data-stu-id="1eb3d-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="1eb3d-105">本文列出所引進之 .NET 版本 Windows Forms 的重大變更。</span><span class="sxs-lookup"><span data-stu-id="1eb3d-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="1eb3d-106">如果您要從 .NET Framework 或舊版 .NET Core (3.0 或更新版本的) 升級 Windows Forms 應用程式，本文適用于您。</span><span class="sxs-lookup"><span data-stu-id="1eb3d-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="1eb3d-107">此頁面記載了下列重大變更：</span><span class="sxs-lookup"><span data-stu-id="1eb3d-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="1eb3d-108">重大變更</span><span class="sxs-lookup"><span data-stu-id="1eb3d-108">Breaking change</span></span> | <span data-ttu-id="1eb3d-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="1eb3d-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="1eb3d-110">TextFormatFlags. ModifyString 已淘汰</span><span class="sxs-lookup"><span data-stu-id="1eb3d-110">TextFormatFlags.ModifyString is obsolete</span></span>](#textformatflagsmodifystring-is-obsolete) | <span data-ttu-id="1eb3d-111">5.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-111">5.0</span></span> |
| [<span data-ttu-id="1eb3d-112">DataGridView 不會再重設自訂儲存格樣式的字型</span><span class="sxs-lookup"><span data-stu-id="1eb3d-112">DataGridView no longer resets fonts for customized cell styles</span></span>](#datagridview-no-longer-resets-fonts-for-customized-cell-styles) | <span data-ttu-id="1eb3d-113">5.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-113">5.0</span></span> |
| [<span data-ttu-id="1eb3d-114">適用于 WPF 和 WinForms 應用程式的 OutputType 設定為 WinExe</span><span class="sxs-lookup"><span data-stu-id="1eb3d-114">OutputType set to WinExe for WPF and WinForms apps</span></span>](#outputtype-set-to-winexe-for-wpf-and-winforms-apps) | <span data-ttu-id="1eb3d-115">5.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-115">5.0</span></span> |
| [<span data-ttu-id="1eb3d-116">DataGridView 相關的 Api 現在會擲回 InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="1eb3d-116">DataGridView-related APIs now throw InvalidOperationException</span></span>](#datagridview-related-apis-now-throw-invalidoperationexception) | <span data-ttu-id="1eb3d-117">5.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-117">5.0</span></span> |
| [<span data-ttu-id="1eb3d-118">WinForms 和 WPF 應用程式使用 Microsoft .NET Sdk</span><span class="sxs-lookup"><span data-stu-id="1eb3d-118">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>](#winforms-and-wpf-apps-use-microsoftnetsdk) | <span data-ttu-id="1eb3d-119">5.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-119">5.0</span></span> |
| [<span data-ttu-id="1eb3d-120">已移除狀態列控制項</span><span class="sxs-lookup"><span data-stu-id="1eb3d-120">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="1eb3d-121">5.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-121">5.0</span></span> |
| [<span data-ttu-id="1eb3d-122">WinForms 方法現在會擲回 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="1eb3d-122">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="1eb3d-123">5.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-123">5.0</span></span> |
| [<span data-ttu-id="1eb3d-124">WinForms 方法現在會擲回 System.argumentnullexception</span><span class="sxs-lookup"><span data-stu-id="1eb3d-124">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="1eb3d-125">5.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-125">5.0</span></span> |
| [<span data-ttu-id="1eb3d-126">WinForms 屬性現在會擲回 ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="1eb3d-126">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="1eb3d-127">5.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-127">5.0</span></span> |
| [<span data-ttu-id="1eb3d-128">已移除控制項</span><span class="sxs-lookup"><span data-stu-id="1eb3d-128">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="1eb3d-129">3.1</span><span class="sxs-lookup"><span data-stu-id="1eb3d-129">3.1</span></span> |
| [<span data-ttu-id="1eb3d-130">如果顯示工具提示，則不會引發 CellFormatting 事件</span><span class="sxs-lookup"><span data-stu-id="1eb3d-130">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="1eb3d-131">3.1</span><span class="sxs-lookup"><span data-stu-id="1eb3d-131">3.1</span></span> |
| [<span data-ttu-id="1eb3d-132">DefaultFont 變更為 Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="1eb3d-132">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="1eb3d-133">3.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-133">3.0</span></span> |
| [<span data-ttu-id="1eb3d-134">FolderBrowserDialog 的現代化</span><span class="sxs-lookup"><span data-stu-id="1eb3d-134">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="1eb3d-135">3.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-135">3.0</span></span> |
| [<span data-ttu-id="1eb3d-136">SerializableAttribute 已從部分 Windows Forms 類型中移除</span><span class="sxs-lookup"><span data-stu-id="1eb3d-136">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="1eb3d-137">3.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-137">3.0</span></span> |
| [<span data-ttu-id="1eb3d-138">不支援 AllowUpdateChildControlIndexForTabControls 相容性參數</span><span class="sxs-lookup"><span data-stu-id="1eb3d-138">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="1eb3d-139">3.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-139">3.0</span></span> |
| [<span data-ttu-id="1eb3d-140">不支援 DomainUpDown UseLegacyScrolling 相容性參數</span><span class="sxs-lookup"><span data-stu-id="1eb3d-140">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="1eb3d-141">3.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-141">3.0</span></span> |
| [<span data-ttu-id="1eb3d-142">不支援 DoNotLoadLatestRichEditControl 相容性參數</span><span class="sxs-lookup"><span data-stu-id="1eb3d-142">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="1eb3d-143">3.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-143">3.0</span></span> |
| [<span data-ttu-id="1eb3d-144">不支援 DoNotSupportSelectAllShortcutInMultilineTextBox 相容性參數</span><span class="sxs-lookup"><span data-stu-id="1eb3d-144">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="1eb3d-145">3.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-145">3.0</span></span> |
| [<span data-ttu-id="1eb3d-146">不支援 >dontsupportreentrantfiltermessage 相容性參數</span><span class="sxs-lookup"><span data-stu-id="1eb3d-146">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="1eb3d-147">3.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-147">3.0</span></span> |
| [<span data-ttu-id="1eb3d-148">不支援 EnableVisualStyleValidation 相容性參數</span><span class="sxs-lookup"><span data-stu-id="1eb3d-148">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="1eb3d-149">3.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-149">3.0</span></span> |
| [<span data-ttu-id="1eb3d-150">不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性參數</span><span class="sxs-lookup"><span data-stu-id="1eb3d-150">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="1eb3d-151">3.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-151">3.0</span></span> |
| [<span data-ttu-id="1eb3d-152">不支援 UseLegacyImages 相容性參數</span><span class="sxs-lookup"><span data-stu-id="1eb3d-152">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="1eb3d-153">3.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-153">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="1eb3d-154">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-154">.NET 5.0</span></span>

[!INCLUDE [modifystring-field-of-textformatflags-obsolete](../../../includes/core-changes/windowsforms/5.0/modifystring-field-of-textformatflags-obsolete.md)]

***

[!INCLUDE [datagridview-doesnt-reset-custom-font-settings](../../../includes/core-changes/windowsforms/5.0/datagridview-doesnt-reset-custom-font-settings.md)]

<span data-ttu-id="1eb3d-155">\*\*_</span><span class="sxs-lookup"><span data-stu-id="1eb3d-155">\*\*_</span></span>

[!INCLUDE [automatically-infer-winexe-output-type](../../../includes/core-changes/windowsforms/5.0/automatically-infer-winexe-output-type.md)]

_*_

[!INCLUDE [null-owner-causes-invalidoperationexception](../../../includes/core-changes/windowsforms/5.0/null-owner-causes-invalidoperationexception.md)]

_*_

[!INCLUDE [sdk-and-target-framework-change](../../../includes/core-changes/windowsforms/5.0/sdk-and-target-framework-change.md)]

_*_

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

_*_

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

_*_

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

_*_

[!INCLUDE [invalid-args-cause-argumentoutofrangeexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentoutofrangeexception.md)]

_*_

## <a name="net-core-31"></a><span data-ttu-id="1eb3d-156">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="1eb3d-156">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

_*_

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

_*_

## <a name="net-core-30"></a><span data-ttu-id="1eb3d-157">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1eb3d-157">.NET Core 3.0</span></span>

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

<span data-ttu-id="1eb3d-158">_\*\*</span><span class="sxs-lookup"><span data-stu-id="1eb3d-158">_\*\*</span></span>

## <a name="see-also"></a><span data-ttu-id="1eb3d-159">請參閱</span><span class="sxs-lookup"><span data-stu-id="1eb3d-159">See also</span></span>

- [<span data-ttu-id="1eb3d-160">將 Windows Forms 應用程式移植到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="1eb3d-160">Port a Windows Forms app to .NET Core</span></span>](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
