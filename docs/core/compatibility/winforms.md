---
title: 視窗表單中斷更改
description: 列出 .NET Core 的 Windows 表單中的重大更改。
ms.date: 01/08/2020
ms.openlocfilehash: 7fba78382d011bc9d489924fa185a44e598c5a76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399095"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="ab08f-103">Windows 表單中的中斷更改</span><span class="sxs-lookup"><span data-stu-id="ab08f-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="ab08f-104">Windows 表單支援已添加到 3.0 版中的 .NET Core 中。</span><span class="sxs-lookup"><span data-stu-id="ab08f-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="ab08f-105">本文列出了引入 Windows 表單的 .NET Core 版本對 Windows 表單的重大變化。</span><span class="sxs-lookup"><span data-stu-id="ab08f-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="ab08f-106">如果要從 .NET 框架或從 .NET Core 的早期版本 （3.0 或更高版本）升級 Windows 表單應用，本文適用于您。</span><span class="sxs-lookup"><span data-stu-id="ab08f-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="ab08f-107">此頁面將記錄以下重大更改：</span><span class="sxs-lookup"><span data-stu-id="ab08f-107">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="ab08f-108">已刪除控制項</span><span class="sxs-lookup"><span data-stu-id="ab08f-108">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="ab08f-109">如果顯示工具提示，則不引發儲存格格式事件</span><span class="sxs-lookup"><span data-stu-id="ab08f-109">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="ab08f-110">控制項.預設字型更改為 Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="ab08f-110">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="ab08f-111">資料夾瀏覽器對話的現代化</span><span class="sxs-lookup"><span data-stu-id="ab08f-111">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="ab08f-112">從某些 Windows 表單類型中刪除的可序列化屬性</span><span class="sxs-lookup"><span data-stu-id="ab08f-112">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="ab08f-113">允許更新兒童控制索引ForTab控制相容性開關不支援</span><span class="sxs-lookup"><span data-stu-id="ab08f-113">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="ab08f-114">域向上向下.不使用舊卷滾動相容性開關</span><span class="sxs-lookup"><span data-stu-id="ab08f-114">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="ab08f-115">不支援不載入最新裡奇編輯控制相容性開關</span><span class="sxs-lookup"><span data-stu-id="ab08f-115">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="ab08f-116">不支援選擇全選件多行文本盒相容性開關</span><span class="sxs-lookup"><span data-stu-id="ab08f-116">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="ab08f-117">不支援不支援重新進入篩選器消息相容性開關</span><span class="sxs-lookup"><span data-stu-id="ab08f-117">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="ab08f-118">不支援啟用視覺化樣式驗證相容性開關</span><span class="sxs-lookup"><span data-stu-id="ab08f-118">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="ab08f-119">不支援使用傳統內容功能表，提供資源控制值相容性開關</span><span class="sxs-lookup"><span data-stu-id="ab08f-119">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="ab08f-120">不支援使用傳統圖像相容性開關</span><span class="sxs-lookup"><span data-stu-id="ab08f-120">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="ab08f-121">更改可訪問物件的訪問. 運行時 ID 第一專案</span><span class="sxs-lookup"><span data-stu-id="ab08f-121">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="ab08f-122">從 Windows 表單中刪除的重複 API</span><span class="sxs-lookup"><span data-stu-id="ab08f-122">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

## <a name="net-core-31"></a><span data-ttu-id="ab08f-123">.NET 核心 3.1</span><span class="sxs-lookup"><span data-stu-id="ab08f-123">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="ab08f-124">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ab08f-124">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ab08f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab08f-125">See also</span></span>

- [<span data-ttu-id="ab08f-126">將 Windows 表單應用移植到 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="ab08f-126">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
