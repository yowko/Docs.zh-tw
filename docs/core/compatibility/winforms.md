---
title: Windows Forms 重大變更
description: 列出適用于 .NET Core 和 .NET 5 的 Windows Forms 中的重大變更。
ms.date: 09/08/2020
ms.openlocfilehash: 01810a690227bbcab2103f00767315dbc5d5fae3
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400629"
---
# <a name="breaking-changes-in-windows-forms"></a>Windows Forms 中的重大變更

版本3.0 中的 .NET Core 已新增 Windows Forms 支援。 本文列出所引進之 .NET 版本 Windows Forms 的重大變更。 如果您要從 .NET Framework 或舊版 .NET Core (3.0 或更新版本的) 升級 Windows Forms 應用程式，本文適用于您。

此頁面記載了下列重大變更：

| 重大變更 | 引進的版本 |
| - | :-: |
| [TextFormatFlags. ModifyString 已淘汰](#textformatflagsmodifystring-is-obsolete) | 5.0 |
| [DataGridView 不會再重設自訂儲存格樣式的字型](#datagridview-no-longer-resets-fonts-for-customized-cell-styles) | 5.0 |
| [適用于 WPF 和 WinForms 應用程式的 OutputType 設定為 WinExe](#outputtype-set-to-winexe-for-wpf-and-winforms-apps) | 5.0 |
| [DataGridView 相關的 Api 現在會擲回 InvalidOperationException](#datagridview-related-apis-now-throw-invalidoperationexception) | 5.0 |
| [WinForms 和 WPF 應用程式使用 Microsoft .NET Sdk](#winforms-and-wpf-apps-use-microsoftnetsdk) | 5.0 |
| [已移除狀態列控制項](#removed-status-bar-controls) | 5.0 |
| [WinForms 方法現在會擲回 ArgumentException](#winforms-methods-now-throw-argumentexception) | 5.0 |
| [WinForms 方法現在會擲回 System.argumentnullexception](#winforms-methods-now-throw-argumentnullexception) | 5.0 |
| [WinForms 屬性現在會擲回 ArgumentOutOfRangeException](#winforms-properties-now-throw-argumentoutofrangeexception) | 5.0 |
| [已移除控制項](#removed-controls) | 3.1 |
| [如果顯示工具提示，則不會引發 CellFormatting 事件](#cellformatting-event-not-raised-if-tooltip-is-shown) | 3.1 |
| [DefaultFont 變更為 Segoe UI 9 pt](#default-control-font-changed-to-segoe-ui-9-pt) | 3.0 |
| [FolderBrowserDialog 的現代化](#modernization-of-the-folderbrowserdialog) | 3.0 |
| [SerializableAttribute 已從部分 Windows Forms 類型中移除](#serializableattribute-removed-from-some-windows-forms-types) | 3.0 |
| [不支援 AllowUpdateChildControlIndexForTabControls 相容性參數](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | 3.0 |
| [不支援 DomainUpDown UseLegacyScrolling 相容性參數](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | 3.0 |
| [不支援 DoNotLoadLatestRichEditControl 相容性參數](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | 3.0 |
| [不支援 DoNotSupportSelectAllShortcutInMultilineTextBox 相容性參數](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | 3.0 |
| [不支援 >dontsupportreentrantfiltermessage 相容性參數](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | 3.0 |
| [不支援 EnableVisualStyleValidation 相容性參數](#enablevisualstylevalidation-compatibility-switch-not-supported) | 3.0 |
| [不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性參數](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | 3.0 |
| [不支援 UseLegacyImages 相容性參數](#uselegacyimages-compatibility-switch-not-supported) | 3.0 |

## <a name="net-50"></a>.NET 5。0

[!INCLUDE [modifystring-field-of-textformatflags-obsolete](../../../includes/core-changes/windowsforms/5.0/modifystring-field-of-textformatflags-obsolete.md)]

***

[!INCLUDE [datagridview-doesnt-reset-custom-font-settings](../../../includes/core-changes/windowsforms/5.0/datagridview-doesnt-reset-custom-font-settings.md)]

**_

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

## <a name="net-core-31"></a>.NET Core 3.1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

_*_

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

_*_

## <a name="net-core-30"></a>.NET Core 3.0

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

_**

## <a name="see-also"></a>請參閱

- [將 Windows Forms 應用程式移植到 .NET Core](../porting/winforms.md)
