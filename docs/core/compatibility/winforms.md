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
# <a name="breaking-changes-in-windows-forms"></a>Windows Forms 中的重大變更

版本3.0 中的 .NET Core 已加入 Windows Forms 支援。 本文列出其引進的 .NET Core 版本 Windows Forms 的重大變更。 如果您要從 .NET Framework 或舊版 .NET Core （3.0 或更新版本）升級 Windows Forms 應用程式，本文適用于您。

下列重大變更記載于此頁面：

- [移除的控制項](#removed-controls)
- [如果顯示工具提示，則不會引發 CellFormatting 事件](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [DefaultFont 已變更為 Segoe UI 9 pt](#default-control-font-changed-to-segoe-ui-9-pt)
- [FolderBrowserDialog 的現代化](#modernization-of-the-folderbrowserdialog)
- [已從某些 Windows Forms 類型中移除 SerializableAttribute](#serializableattribute-removed-from-some-windows-forms-types)
- [不支援 AllowUpdateChildControlIndexForTabControls 相容性切換](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [不支援 DomainUpDown. UseLegacyScrolling 相容性參數](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [不支援 DoNotLoadLatestRichEditControl 相容性切換](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [不支援 DoNotSupportSelectAllShortcutInMultilineTextBox 相容性切換](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [不支援 DontSupportReentrantFilterMessage 相容性切換](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [不支援 EnableVisualStyleValidation 相容性切換](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性切換](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [不支援 UseLegacyImages 相容性切換](#uselegacyimages-compatibility-switch-not-supported)
- [變更 AccessibleObject 的存取權。 RuntimeIDFirstItem](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [已從 Windows Forms 移除重複的 Api](#duplicated-apis-removed-from-windows-forms)

## <a name="net-core-31"></a>.NET Core 3.1

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

- [將 Windows Forms 應用程式移植到 .NET Core](../porting/winforms.md)
