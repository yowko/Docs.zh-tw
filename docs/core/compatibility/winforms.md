---
title: Windows Forms 重大變更
description: 列出 .NET Core 3.0 和 3.1 Windows Forms 的重大變更。
ms.date: 09/08/2020
ms.openlocfilehash: b944f7eea89b61f41feb8eef99e949c2d6017960
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726427"
---
# <a name="breaking-changes-in-windows-forms-for-net-core-30-and-31"></a>.NET Core 3.0 和 3.1 Windows Forms 的重大變更

版本3.0 中的 .NET Core 已新增 Windows Forms 支援。 本文列出所引進之 .NET 版本 Windows Forms 的重大變更。 如果您要從 .NET Framework 或舊版 .NET Core (3.0 或更新版本的) 升級 Windows Forms 應用程式，本文適用于您。

此頁面記載了下列重大變更：

| 重大變更 | 引進的版本 |
| - | :-: |
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

## <a name="net-core-31"></a>.NET Core 3.1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

**_

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

## <a name="see-also"></a>另請參閱

- [將 Windows Forms 應用程式移植到 .NET Core](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
