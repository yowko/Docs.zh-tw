---
title: 重大變更-.NET Framework 至 .NET Core
titleSuffix: ''
description: 列出從 .NET Framework 到 .NET Core 的重大變更。
ms.date: 05/05/2020
ms.openlocfilehash: 613c4e41e12be57d5631b347055140a4418e7207
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206452"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="0f0b7-103">從 .NET Framework 遷移至 .NET Core 的突破性變更</span><span class="sxs-lookup"><span data-stu-id="0f0b7-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="0f0b7-104">如果您要將應用程式從 .NET Framework 遷移至 .NET Core，本文中所列的重大變更可能會對您造成影響。</span><span class="sxs-lookup"><span data-stu-id="0f0b7-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="0f0b7-105">中斷性變更會依類別目錄，以及在這些類別中所引進的 .NET Core 版本進行分組。</span><span class="sxs-lookup"><span data-stu-id="0f0b7-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core in which they were introduced.</span></span>

> [!NOTE]
> <span data-ttu-id="0f0b7-106">本文不是 .NET Framework 和 .NET Core 之間的重大變更完整清單。</span><span class="sxs-lookup"><span data-stu-id="0f0b7-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="0f0b7-107">最重要的重大變更會在這裡新增，因為我們會注意到它們。</span><span class="sxs-lookup"><span data-stu-id="0f0b7-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="core-net-libraries"></a><span data-ttu-id="0f0b7-108">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="0f0b7-108">Core .NET libraries</span></span>

- [<span data-ttu-id="0f0b7-109">預設值為 UseShellExecute 的變更</span><span class="sxs-lookup"><span data-stu-id="0f0b7-109">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)
- [<span data-ttu-id="0f0b7-110">FileSystemInfo 擲回的 System.unauthorizedaccessexception</span><span class="sxs-lookup"><span data-stu-id="0f0b7-110">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)
- [<span data-ttu-id="0f0b7-111">不支援處理損毀的進程狀態例外狀況</span><span class="sxs-lookup"><span data-stu-id="0f0b7-111">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported)
- [<span data-ttu-id="0f0b7-112">UriBuilder 屬性不再前面加上前置字元</span><span class="sxs-lookup"><span data-stu-id="0f0b7-112">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters)

### <a name="net-core-21"></a><span data-ttu-id="0f0b7-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0f0b7-113">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a><span data-ttu-id="0f0b7-114">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="0f0b7-114">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

## <a name="cryptography"></a><span data-ttu-id="0f0b7-115">密碼編譯</span><span class="sxs-lookup"><span data-stu-id="0f0b7-115">Cryptography</span></span>

- [<span data-ttu-id="0f0b7-116">遵守 SignedCms 的布林值參數。 ComputeSignature</span><span class="sxs-lookup"><span data-stu-id="0f0b7-116">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a><span data-ttu-id="0f0b7-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0f0b7-117">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="msbuild"></a><span data-ttu-id="0f0b7-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="0f0b7-118">MSBuild</span></span>

- [<span data-ttu-id="0f0b7-119">資源資訊清單檔案名變更</span><span class="sxs-lookup"><span data-stu-id="0f0b7-119">Resource manifest file name change</span></span>](#resource-manifest-file-name-change)

### <a name="net-core-30"></a><span data-ttu-id="0f0b7-120">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0f0b7-120">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***

## <a name="networking"></a><span data-ttu-id="0f0b7-121">網路功能</span><span class="sxs-lookup"><span data-stu-id="0f0b7-121">Networking</span></span>

- [<span data-ttu-id="0f0b7-122">WebClient 地說 cancelasync 不一定會立即取消</span><span class="sxs-lookup"><span data-stu-id="0f0b7-122">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately)

### <a name="net-core-20"></a><span data-ttu-id="0f0b7-123">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="0f0b7-123">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="0f0b7-124">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f0b7-124">Windows Forms</span></span>

<span data-ttu-id="0f0b7-125">版本3.0 中的 .NET Core 已加入 Windows Forms 支援。</span><span class="sxs-lookup"><span data-stu-id="0f0b7-125">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="0f0b7-126">如果您要將 Windows Forms 應用程式從 .NET Framework 遷移至 .NET Core，此處所列的重大變更可能會影響您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f0b7-126">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

- [<span data-ttu-id="0f0b7-127">移除的控制項</span><span class="sxs-lookup"><span data-stu-id="0f0b7-127">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="0f0b7-128">如果顯示工具提示，則不會引發 CellFormatting 事件</span><span class="sxs-lookup"><span data-stu-id="0f0b7-128">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="0f0b7-129">DefaultFont 已變更為 Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="0f0b7-129">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="0f0b7-130">FolderBrowserDialog 的現代化</span><span class="sxs-lookup"><span data-stu-id="0f0b7-130">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="0f0b7-131">已從某些 Windows Forms 類型中移除 SerializableAttribute</span><span class="sxs-lookup"><span data-stu-id="0f0b7-131">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="0f0b7-132">不支援 AllowUpdateChildControlIndexForTabControls 相容性切換</span><span class="sxs-lookup"><span data-stu-id="0f0b7-132">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="0f0b7-133">不支援 DomainUpDown. UseLegacyScrolling 相容性參數</span><span class="sxs-lookup"><span data-stu-id="0f0b7-133">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="0f0b7-134">不支援 DoNotLoadLatestRichEditControl 相容性切換</span><span class="sxs-lookup"><span data-stu-id="0f0b7-134">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="0f0b7-135">不支援 DoNotSupportSelectAllShortcutInMultilineTextBox 相容性切換</span><span class="sxs-lookup"><span data-stu-id="0f0b7-135">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="0f0b7-136">不支援 DontSupportReentrantFilterMessage 相容性切換</span><span class="sxs-lookup"><span data-stu-id="0f0b7-136">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="0f0b7-137">不支援 EnableVisualStyleValidation 相容性切換</span><span class="sxs-lookup"><span data-stu-id="0f0b7-137">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="0f0b7-138">不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性切換</span><span class="sxs-lookup"><span data-stu-id="0f0b7-138">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="0f0b7-139">不支援 UseLegacyImages 相容性切換</span><span class="sxs-lookup"><span data-stu-id="0f0b7-139">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="0f0b7-140">變更 AccessibleObject 的存取權。 RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="0f0b7-140">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="0f0b7-141">已從 Windows Forms 移除重複的 Api</span><span class="sxs-lookup"><span data-stu-id="0f0b7-141">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="0f0b7-142">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="0f0b7-142">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="0f0b7-143">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0f0b7-143">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0f0b7-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="0f0b7-144">See also</span></span>

- [<span data-ttu-id="0f0b7-145">在 .NET Core 上一律會擲回例外狀況的 Api</span><span class="sxs-lookup"><span data-stu-id="0f0b7-145">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="0f0b7-146">.NET Core 上無法使用的 .NET Framework 技術</span><span class="sxs-lookup"><span data-stu-id="0f0b7-146">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
