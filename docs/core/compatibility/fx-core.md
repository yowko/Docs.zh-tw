---
title: 重大變更-.NET Framework .NET Core
titleSuffix: ''
description: 列出從 .NET Framework 到 .NET Core 1.0-3.1 的重大變更。
ms.date: 05/05/2020
ms.openlocfilehash: 5904a359813b6d07bd2a27d882ade4395efe3256
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656362"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>從 .NET Framework 遷移至 .NET Core 的重大變更

如果您要將應用程式從 .NET Framework 遷移至 .NET Core 1.0 至3.1 版，本文所列的重大變更可能會對您造成影響。 中斷性變更是依類別目錄分組，而在這些類別中，則是以引入這些變更的 .NET Core 版本為依據。

> [!NOTE]
> 本文不是 .NET Framework 和 .NET Core 之間的重大變更完整清單。 在這裡新增最重要的中斷性變更，因為我們會注意到這些變更。

## <a name="core-net-libraries"></a>Core .NET 程式庫

- [UseShellExecute 預設值的變更](#change-in-default-value-of-useshellexecute)
- [FileSystemInfo 擲回的 System.unauthorizedaccessexception。屬性](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)
- [不支援處理損毀的進程狀態例外狀況](#handling-corrupted-state-exceptions-is-not-supported)
- [UriBuilder 屬性不再加上前置字元](#uribuilder-properties-no-longer-prepend-leading-characters)
- [StartInfo 會針對您未啟動的進程擲回 InvalidOperationException](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a>.NET Core 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***

## <a name="cryptography"></a>密碼編譯

- [已遵守 SignedCms 的布林值參數。 ComputeSignature](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="msbuild"></a>MSBuild

- [資源資訊清單檔案名變更](#resource-manifest-file-name-change)

### <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***

## <a name="networking"></a>網路

- [WebClient >cancelasync 不一定會立即取消](#webclientcancelasync-doesnt-always-cancel-immediately)

### <a name="net-core-20"></a>.NET Core 2.0

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***

## <a name="windows-forms"></a>Windows Forms

版本3.0 中的 .NET Core 已新增 Windows Forms 支援。 如果您要將 Windows Forms 應用程式從 .NET Framework 遷移至 .NET Core，此處所列的重大變更可能會影響您的應用程式。

- [已移除控制項](#removed-controls)
- [如果顯示工具提示，則不會引發 CellFormatting 事件](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [DefaultFont 變更為 Segoe UI 9 pt](#default-control-font-changed-to-segoe-ui-9-pt)
- [FolderBrowserDialog 的現代化](#modernization-of-the-folderbrowserdialog)
- [SerializableAttribute 已從部分 Windows Forms 類型中移除](#serializableattribute-removed-from-some-windows-forms-types)
- [不支援 AllowUpdateChildControlIndexForTabControls 相容性參數](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [不支援 DomainUpDown UseLegacyScrolling 相容性參數](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [不支援 DoNotLoadLatestRichEditControl 相容性參數](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [不支援 DoNotSupportSelectAllShortcutInMultilineTextBox 相容性參數](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [不支援 >dontsupportreentrantfiltermessage 相容性參數](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [不支援 EnableVisualStyleValidation 相容性參數](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [不支援 UseLegacyCoNtextMenuStripSourceControlValue 相容性參數](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [不支援 UseLegacyImages 相容性參數](#uselegacyimages-compatibility-switch-not-supported)

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

## <a name="see-also"></a>另請參閱

- [一律會在 .NET Core 上擲回例外狀況的 Api](unsupported-apis.md)
- [.NET Core 上無法使用的 .NET Framework 技術](../porting/net-framework-tech-unavailable.md)
