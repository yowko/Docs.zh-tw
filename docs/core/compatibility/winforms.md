---
title: Windows Forms 的重大變更
description: 列出 .NET Core Windows Forms 中的重大變更。
ms.date: 01/08/2020
ms.openlocfilehash: 75d369c7fb999da81a50fe46716e125c3840eb7a
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158433"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="531b9-103">Windows Forms 中的重大變更</span><span class="sxs-lookup"><span data-stu-id="531b9-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="531b9-104">版本3.0 中的 .NET Core 已加入 Windows Forms 支援。</span><span class="sxs-lookup"><span data-stu-id="531b9-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="531b9-105">本文列出其引進的 .NET Core 版本 Windows Forms 的重大變更。</span><span class="sxs-lookup"><span data-stu-id="531b9-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="531b9-106">如果您要從 .NET Framework 或舊版 .NET Core （3.0 或更新版本）升級 Windows Forms 應用程式，本文適用于您。</span><span class="sxs-lookup"><span data-stu-id="531b9-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="531b9-107">下列重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="531b9-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="531b9-108">重大變更</span><span class="sxs-lookup"><span data-stu-id="531b9-108">Breaking change</span></span> | <span data-ttu-id="531b9-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="531b9-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="531b9-110">已移除狀態列控制項</span><span class="sxs-lookup"><span data-stu-id="531b9-110">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="531b9-111">5.0</span><span class="sxs-lookup"><span data-stu-id="531b9-111">5.0</span></span> |
| [<span data-ttu-id="531b9-112">WinForms 方法現在會擲回 ArgumentException</span><span class="sxs-lookup"><span data-stu-id="531b9-112">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="531b9-113">5.0</span><span class="sxs-lookup"><span data-stu-id="531b9-113">5.0</span></span> |
| [<span data-ttu-id="531b9-114">WinForms 方法現在會擲回 System.argumentnullexception</span><span class="sxs-lookup"><span data-stu-id="531b9-114">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="531b9-115">5.0</span><span class="sxs-lookup"><span data-stu-id="531b9-115">5.0</span></span> |
| [<span data-ttu-id="531b9-116">移除的控制項</span><span class="sxs-lookup"><span data-stu-id="531b9-116">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="531b9-117">3.1</span><span class="sxs-lookup"><span data-stu-id="531b9-117">3.1</span></span> |
| [<span data-ttu-id="531b9-118">如果顯示工具提示，則不會引發 CellFormatting 事件</span><span class="sxs-lookup"><span data-stu-id="531b9-118">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="531b9-119">3.1</span><span class="sxs-lookup"><span data-stu-id="531b9-119">3.1</span></span> |
| [<span data-ttu-id="531b9-120">DefaultFont 已變更為 Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="531b9-120">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="531b9-121">3.0</span><span class="sxs-lookup"><span data-stu-id="531b9-121">3.0</span></span> |
| [<span data-ttu-id="531b9-122">FolderBrowserDialog 的現代化</span><span class="sxs-lookup"><span data-stu-id="531b9-122">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="531b9-123">3.0</span><span class="sxs-lookup"><span data-stu-id="531b9-123">3.0</span></span> |
| [<span data-ttu-id="531b9-124">已從某些 Windows Forms 類型中移除 SerializableAttribute</span><span class="sxs-lookup"><span data-stu-id="531b9-124">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="531b9-125">3.0</span><span class="sxs-lookup"><span data-stu-id="531b9-125">3.0</span></span> |
| [<span data-ttu-id="531b9-126">不支援 AllowUpdateChildControlIndexForTabControls 相容性切換</span><span class="sxs-lookup"><span data-stu-id="531b9-126">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="531b9-127">3.0</span><span class="sxs-lookup"><span data-stu-id="531b9-127">3.0</span></span> |
| [<span data-ttu-id="531b9-128">不支援 DomainUpDown. UseLegacyScrolling 相容性參數</span><span class="sxs-lookup"><span data-stu-id="531b9-128">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="531b9-129">3.0</span><span class="sxs-lookup"><span data-stu-id="531b9-129">3.0</span></span> |
| [<span data-ttu-id="531b9-130">不支援 DoNotLoadLatestRichEditControl 相容性切換</span><span class="sxs-lookup"><span data-stu-id="531b9-130">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="531b9-131">3.0</span><span class="sxs-lookup"><span data-stu-id="531b9-131">3.0</span></span> |
| [<span data-ttu-id="531b9-132">不支援 DoNotSupportSelectAllShortcutInMultilineTextBox 相容性切換</span><span class="sxs-lookup"><span data-stu-id="531b9-132">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="531b9-133">3.0</span><span class="sxs-lookup"><span data-stu-id="531b9-133">3.0</span></span> |
| [<span data-ttu-id="531b9-134">不支援 DontSupportReentrantFilterMessage 相容性切換</span><span class="sxs-lookup"><span data-stu-id="531b9-134">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="531b9-135">3.0</span><span class="sxs-lookup"><span data-stu-id="531b9-135">3.0</span></span> |
| [<span data-ttu-id="531b9-136">不支援 EnableVisualStyleValidation 相容性切換</span><span class="sxs-lookup"><span data-stu-id="531b9-136">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="531b9-137">3.0</span><span class="sxs-lookup"><span data-stu-id="531b9-137">3.0</span></span> |
| [<span data-ttu-id="531b9-138">不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性切換</span><span class="sxs-lookup"><span data-stu-id="531b9-138">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="531b9-139">3.0</span><span class="sxs-lookup"><span data-stu-id="531b9-139">3.0</span></span> |
| [<span data-ttu-id="531b9-140">不支援 UseLegacyImages 相容性切換</span><span class="sxs-lookup"><span data-stu-id="531b9-140">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="531b9-141">3.0</span><span class="sxs-lookup"><span data-stu-id="531b9-141">3.0</span></span> |
| [<span data-ttu-id="531b9-142">變更 AccessibleObject 的存取權。 RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="531b9-142">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem) | <span data-ttu-id="531b9-143">3.0</span><span class="sxs-lookup"><span data-stu-id="531b9-143">3.0</span></span> |
| [<span data-ttu-id="531b9-144">已從 Windows Forms 移除重複的 Api</span><span class="sxs-lookup"><span data-stu-id="531b9-144">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms) | <span data-ttu-id="531b9-145">3.0</span><span class="sxs-lookup"><span data-stu-id="531b9-145">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="531b9-146">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="531b9-146">.NET 5.0</span></span>

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

***

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

***

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="531b9-147">.NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="531b9-147">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="531b9-148">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="531b9-148">.NET Core 3.0</span></span>

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

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

***

## <a name="see-also"></a><span data-ttu-id="531b9-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="531b9-149">See also</span></span>

- [<span data-ttu-id="531b9-150">將 Windows Forms 應用程式移植到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="531b9-150">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
