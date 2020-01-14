---
title: 重大變更-.NET Framework 至 .NET Core
description: 列出從 .NET Framework 到 .NET Core 的重大變更。
ms.date: 12/18/2019
ms.openlocfilehash: 9f4ecc8a9de7279bb4b222b3df77e1eb17b33f0a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937398"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>從 .NET Framework 遷移至 .NET Core 的突破性變更

如果您要將應用程式從 .NET Framework 遷移至 .NET Core，本文中所列的重大變更可能會對您造成影響。 中斷性變更會依類別目錄，以及在這些類別中，由在中引進的 .NET Core 版本來分組。

> [!NOTE]
> 本文不是 .NET Framework 和 .NET Core 之間的重大變更完整清單。 最重要的重大變更會在這裡新增，因為我們會注意到它們。

## <a name="corefx"></a>CoreFx

重大變更：

- [預設值為 UseShellExecute 的變更](#change-in-default-value-of-useshellexecute)

***

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

## <a name="windows-forms"></a>Windows 表單

版本3.0 中的 .NET Core 已加入 Windows Forms 支援。 如果您要將 Windows Forms 應用程式從 .NET Framework 遷移至 .NET Core，此處所列的重大變更可能會影響您的應用程式。

重大變更：

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

### <a name="net-core-31"></a>.NET Core 3.1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a>.NET Core 3.0

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

## <a name="see-also"></a>請參閱

- [在 .NET Core 上一律會擲回例外狀況的 Api](unsupported-apis.md)
- [.NET Core 上無法使用的 .NET Framework 技術](../porting/net-framework-tech-unavailable.md)
