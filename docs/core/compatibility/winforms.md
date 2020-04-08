---
title: 視窗表單中斷變更
description: 列出 .NET Core 的 Windows 窗體中的重大更改。
ms.date: 01/08/2020
ms.openlocfilehash: 25c568a8a0092a9c4874419c64c7dcebea4dce9e
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888106"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="1ba18-103">Windows 表單中的中斷變更</span><span class="sxs-lookup"><span data-stu-id="1ba18-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="1ba18-104">Windows 表單支援已添加到 3.0 版中的 .NET Core 中。</span><span class="sxs-lookup"><span data-stu-id="1ba18-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="1ba18-105">本文列出了引入 Windows 窗體的 .NET Core 版本對 Windows 窗體的重大變化。</span><span class="sxs-lookup"><span data-stu-id="1ba18-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="1ba18-106">如果要從 .NET 框架或從 .NET Core 的早期版本 (3.0 或更高版本)升級 Windows 窗體應用,本文適用於您。</span><span class="sxs-lookup"><span data-stu-id="1ba18-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="1ba18-107">此頁面將記錄以下變更:</span><span class="sxs-lookup"><span data-stu-id="1ba18-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="1ba18-108">重大變更</span><span class="sxs-lookup"><span data-stu-id="1ba18-108">Breaking change</span></span> | <span data-ttu-id="1ba18-109">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="1ba18-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="1ba18-110">WinForms API 現在引發參數無效</span><span class="sxs-lookup"><span data-stu-id="1ba18-110">WinForms APIs now throw ArgumentNullException</span></span>](#winforms-apis-now-throw-argumentnullexception) | <span data-ttu-id="1ba18-111">5.0</span><span class="sxs-lookup"><span data-stu-id="1ba18-111">5.0</span></span> |
| [<span data-ttu-id="1ba18-112">已移除控制項</span><span class="sxs-lookup"><span data-stu-id="1ba18-112">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="1ba18-113">3.1</span><span class="sxs-lookup"><span data-stu-id="1ba18-113">3.1</span></span> |
| [<span data-ttu-id="1ba18-114">如果顯示工具提示,則不引發單元格格式事件</span><span class="sxs-lookup"><span data-stu-id="1ba18-114">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="1ba18-115">3.1</span><span class="sxs-lookup"><span data-stu-id="1ba18-115">3.1</span></span> |
| [<span data-ttu-id="1ba18-116">控制項.預設字型變更為 Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="1ba18-116">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="1ba18-117">3.0</span><span class="sxs-lookup"><span data-stu-id="1ba18-117">3.0</span></span> |
| [<span data-ttu-id="1ba18-118">資料夾瀏覽器對話的現代化</span><span class="sxs-lookup"><span data-stu-id="1ba18-118">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="1ba18-119">3.0</span><span class="sxs-lookup"><span data-stu-id="1ba18-119">3.0</span></span> |
| [<span data-ttu-id="1ba18-120">從某些 Windows 表單型態移除的可序列化屬性</span><span class="sxs-lookup"><span data-stu-id="1ba18-120">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="1ba18-121">3.0</span><span class="sxs-lookup"><span data-stu-id="1ba18-121">3.0</span></span> |
| [<span data-ttu-id="1ba18-122">允許更新兒童控制索引ForTab控制相容性開關不支援</span><span class="sxs-lookup"><span data-stu-id="1ba18-122">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="1ba18-123">3.0</span><span class="sxs-lookup"><span data-stu-id="1ba18-123">3.0</span></span> |
| [<span data-ttu-id="1ba18-124">域向上向下.不使用舊捲滾動相容性開關</span><span class="sxs-lookup"><span data-stu-id="1ba18-124">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="1ba18-125">3.0</span><span class="sxs-lookup"><span data-stu-id="1ba18-125">3.0</span></span> |
| [<span data-ttu-id="1ba18-126">不支援不載入最新裡奇編輯控制相容性開關</span><span class="sxs-lookup"><span data-stu-id="1ba18-126">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="1ba18-127">3.0</span><span class="sxs-lookup"><span data-stu-id="1ba18-127">3.0</span></span> |
| [<span data-ttu-id="1ba18-128">不支援選擇全選件多行文字盒相容性開關</span><span class="sxs-lookup"><span data-stu-id="1ba18-128">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="1ba18-129">3.0</span><span class="sxs-lookup"><span data-stu-id="1ba18-129">3.0</span></span> |
| [<span data-ttu-id="1ba18-130">不支援不支援重新進入篩選器訊息相容性開關</span><span class="sxs-lookup"><span data-stu-id="1ba18-130">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="1ba18-131">3.0</span><span class="sxs-lookup"><span data-stu-id="1ba18-131">3.0</span></span> |
| [<span data-ttu-id="1ba18-132">不支援啟用視覺化樣式驗證相容性開關</span><span class="sxs-lookup"><span data-stu-id="1ba18-132">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="1ba18-133">3.0</span><span class="sxs-lookup"><span data-stu-id="1ba18-133">3.0</span></span> |
| [<span data-ttu-id="1ba18-134">不支援使用傳統上下文選單,提供資源控制值相容性開關</span><span class="sxs-lookup"><span data-stu-id="1ba18-134">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="1ba18-135">3.0</span><span class="sxs-lookup"><span data-stu-id="1ba18-135">3.0</span></span> |
| [<span data-ttu-id="1ba18-136">不支援使用傳統影像相容性開關</span><span class="sxs-lookup"><span data-stu-id="1ba18-136">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="1ba18-137">3.0</span><span class="sxs-lookup"><span data-stu-id="1ba18-137">3.0</span></span> |
| [<span data-ttu-id="1ba18-138">變更可存取物件的存取. 執行時 ID 第一專案</span><span class="sxs-lookup"><span data-stu-id="1ba18-138">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem) | <span data-ttu-id="1ba18-139">3.0</span><span class="sxs-lookup"><span data-stu-id="1ba18-139">3.0</span></span> |
| [<span data-ttu-id="1ba18-140">從 Windows 表單中移除的重複 API</span><span class="sxs-lookup"><span data-stu-id="1ba18-140">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms) | <span data-ttu-id="1ba18-141">3.0</span><span class="sxs-lookup"><span data-stu-id="1ba18-141">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="1ba18-142">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="1ba18-142">.NET 5.0</span></span>

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="1ba18-143">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="1ba18-143">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="1ba18-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1ba18-144">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1ba18-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ba18-145">See also</span></span>

- [<span data-ttu-id="1ba18-146">將 Windows 表單應用移植到 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="1ba18-146">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
