---
title: 重大變更-.NET Framework 至 .NET Core
titleSuffix: ''
description: 列出從 .NET Framework 到 .NET Core 的重大變更。
ms.date: 12/18/2019
ms.openlocfilehash: 407f99adf5d400fce659ef71cda32ceac1e54491
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093054"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="c079e-103">從 .NET Framework 遷移至 .NET Core 的突破性變更</span><span class="sxs-lookup"><span data-stu-id="c079e-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="c079e-104">如果您要將應用程式從 .NET Framework 遷移至 .NET Core，本文中所列的重大變更可能會對您造成影響。</span><span class="sxs-lookup"><span data-stu-id="c079e-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="c079e-105">中斷性變更會依類別目錄，以及在這些類別中，由在中引進的 .NET Core 版本來分組。</span><span class="sxs-lookup"><span data-stu-id="c079e-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core they were introduced in.</span></span>

> [!NOTE]
> <span data-ttu-id="c079e-106">本文不是 .NET Framework 和 .NET Core 之間的重大變更完整清單。</span><span class="sxs-lookup"><span data-stu-id="c079e-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="c079e-107">最重要的重大變更會在這裡新增，因為我們會注意到它們。</span><span class="sxs-lookup"><span data-stu-id="c079e-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="corefx"></a><span data-ttu-id="c079e-108">CoreFx</span><span class="sxs-lookup"><span data-stu-id="c079e-108">CoreFx</span></span>

- [<span data-ttu-id="c079e-109">預設值為 UseShellExecute 的變更</span><span class="sxs-lookup"><span data-stu-id="c079e-109">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)

### <a name="net-core-21"></a><span data-ttu-id="c079e-110">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="c079e-110">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="c079e-111">Windows Form</span><span class="sxs-lookup"><span data-stu-id="c079e-111">Windows Forms</span></span>

<span data-ttu-id="c079e-112">版本3.0 中的 .NET Core 已加入 Windows Forms 支援。</span><span class="sxs-lookup"><span data-stu-id="c079e-112">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="c079e-113">如果您要將 Windows Forms 應用程式從 .NET Framework 遷移至 .NET Core，此處所列的重大變更可能會影響您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c079e-113">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

- [<span data-ttu-id="c079e-114">移除的控制項</span><span class="sxs-lookup"><span data-stu-id="c079e-114">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="c079e-115">如果顯示工具提示，則不會引發 CellFormatting 事件</span><span class="sxs-lookup"><span data-stu-id="c079e-115">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="c079e-116">DefaultFont 已變更為 Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="c079e-116">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="c079e-117">FolderBrowserDialog 的現代化</span><span class="sxs-lookup"><span data-stu-id="c079e-117">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="c079e-118">已從某些 Windows Forms 類型中移除 SerializableAttribute</span><span class="sxs-lookup"><span data-stu-id="c079e-118">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="c079e-119">不支援 AllowUpdateChildControlIndexForTabControls 相容性切換</span><span class="sxs-lookup"><span data-stu-id="c079e-119">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="c079e-120">不支援 DomainUpDown. UseLegacyScrolling 相容性參數</span><span class="sxs-lookup"><span data-stu-id="c079e-120">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="c079e-121">不支援 DoNotLoadLatestRichEditControl 相容性切換</span><span class="sxs-lookup"><span data-stu-id="c079e-121">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="c079e-122">不支援 DoNotSupportSelectAllShortcutInMultilineTextBox 相容性切換</span><span class="sxs-lookup"><span data-stu-id="c079e-122">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="c079e-123">不支援 DontSupportReentrantFilterMessage 相容性切換</span><span class="sxs-lookup"><span data-stu-id="c079e-123">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="c079e-124">不支援 EnableVisualStyleValidation 相容性切換</span><span class="sxs-lookup"><span data-stu-id="c079e-124">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="c079e-125">不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性切換</span><span class="sxs-lookup"><span data-stu-id="c079e-125">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="c079e-126">不支援 UseLegacyImages 相容性切換</span><span class="sxs-lookup"><span data-stu-id="c079e-126">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="c079e-127">變更 AccessibleObject 的存取權。 RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="c079e-127">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="c079e-128">已從 Windows Forms 移除重複的 Api</span><span class="sxs-lookup"><span data-stu-id="c079e-128">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="c079e-129">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="c079e-129">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="c079e-130">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c079e-130">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9 pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

***

## <a name="see-also"></a><span data-ttu-id="c079e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c079e-131">See also</span></span>

- [<span data-ttu-id="c079e-132">在 .NET Core 上一律會擲回例外狀況的 Api</span><span class="sxs-lookup"><span data-stu-id="c079e-132">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="c079e-133">.NET Core 上無法使用的 .NET Framework 技術</span><span class="sxs-lookup"><span data-stu-id="c079e-133">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
