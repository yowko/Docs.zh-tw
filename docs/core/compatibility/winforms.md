---
title: Windows Forms 的重大變更
description: 列出 .NET Core Windows Forms 中的重大變更。
ms.date: 01/08/2020
ms.openlocfilehash: 7fba78382d011bc9d489924fa185a44e598c5a76
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093015"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="15e92-103">Windows Forms 中的重大變更</span><span class="sxs-lookup"><span data-stu-id="15e92-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="15e92-104">版本3.0 中的 .NET Core 已加入 Windows Forms 支援。</span><span class="sxs-lookup"><span data-stu-id="15e92-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="15e92-105">本文列出其引進的 .NET Core 版本 Windows Forms 的重大變更。</span><span class="sxs-lookup"><span data-stu-id="15e92-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="15e92-106">如果您要從 .NET Framework 或舊版 .NET Core （3.0 或更新版本）升級 Windows Forms 應用程式，本文適用于您。</span><span class="sxs-lookup"><span data-stu-id="15e92-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="15e92-107">下列重大變更記載于此頁面：</span><span class="sxs-lookup"><span data-stu-id="15e92-107">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="15e92-108">移除的控制項</span><span class="sxs-lookup"><span data-stu-id="15e92-108">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="15e92-109">如果顯示工具提示，則不會引發 CellFormatting 事件</span><span class="sxs-lookup"><span data-stu-id="15e92-109">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="15e92-110">DefaultFont 已變更為 Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="15e92-110">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="15e92-111">FolderBrowserDialog 的現代化</span><span class="sxs-lookup"><span data-stu-id="15e92-111">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="15e92-112">已從某些 Windows Forms 類型中移除 SerializableAttribute</span><span class="sxs-lookup"><span data-stu-id="15e92-112">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="15e92-113">不支援 AllowUpdateChildControlIndexForTabControls 相容性切換</span><span class="sxs-lookup"><span data-stu-id="15e92-113">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="15e92-114">不支援 DomainUpDown. UseLegacyScrolling 相容性參數</span><span class="sxs-lookup"><span data-stu-id="15e92-114">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="15e92-115">不支援 DoNotLoadLatestRichEditControl 相容性切換</span><span class="sxs-lookup"><span data-stu-id="15e92-115">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="15e92-116">不支援 DoNotSupportSelectAllShortcutInMultilineTextBox 相容性切換</span><span class="sxs-lookup"><span data-stu-id="15e92-116">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="15e92-117">不支援 DontSupportReentrantFilterMessage 相容性切換</span><span class="sxs-lookup"><span data-stu-id="15e92-117">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="15e92-118">不支援 EnableVisualStyleValidation 相容性切換</span><span class="sxs-lookup"><span data-stu-id="15e92-118">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="15e92-119">不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性切換</span><span class="sxs-lookup"><span data-stu-id="15e92-119">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="15e92-120">不支援 UseLegacyImages 相容性切換</span><span class="sxs-lookup"><span data-stu-id="15e92-120">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="15e92-121">變更 AccessibleObject 的存取權。 RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="15e92-121">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="15e92-122">已從 Windows Forms 移除重複的 Api</span><span class="sxs-lookup"><span data-stu-id="15e92-122">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

## <a name="net-core-31"></a><span data-ttu-id="15e92-123">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="15e92-123">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="15e92-124">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="15e92-124">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="15e92-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15e92-125">See also</span></span>

- [<span data-ttu-id="15e92-126">將 Windows Forms 應用程式移植到 .NET Core</span><span class="sxs-lookup"><span data-stu-id="15e92-126">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
