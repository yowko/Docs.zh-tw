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
# <a name="breaking-changes-in-windows-forms"></a>Windows 表單中的中斷更改

Windows 表單支援已添加到 3.0 版中的 .NET Core 中。 本文列出了引入 Windows 表單的 .NET Core 版本對 Windows 表單的重大變化。 如果要從 .NET 框架或從 .NET Core 的早期版本 （3.0 或更高版本）升級 Windows 表單應用，本文適用于您。

此頁面將記錄以下重大更改：

- [已刪除控制項](#removed-controls)
- [如果顯示工具提示，則不引發儲存格格式事件](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [控制項.預設字型更改為 Segoe UI 9 pt](#default-control-font-changed-to-segoe-ui-9-pt)
- [資料夾瀏覽器對話的現代化](#modernization-of-the-folderbrowserdialog)
- [從某些 Windows 表單類型中刪除的可序列化屬性](#serializableattribute-removed-from-some-windows-forms-types)
- [允許更新兒童控制索引ForTab控制相容性開關不支援](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [域向上向下.不使用舊卷滾動相容性開關](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [不支援不載入最新裡奇編輯控制相容性開關](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [不支援選擇全選件多行文本盒相容性開關](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [不支援不支援重新進入篩選器消息相容性開關](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [不支援啟用視覺化樣式驗證相容性開關](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [不支援使用傳統內容功能表，提供資源控制值相容性開關](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [不支援使用傳統圖像相容性開關](#uselegacyimages-compatibility-switch-not-supported)
- [更改可訪問物件的訪問. 運行時 ID 第一專案](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [從 Windows 表單中刪除的重複 API](#duplicated-apis-removed-from-windows-forms)

## <a name="net-core-31"></a>.NET 核心 3.1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

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

## <a name="see-also"></a>另請參閱

- [將 Windows 表單應用移植到 .NET 核心](../porting/winforms.md)
