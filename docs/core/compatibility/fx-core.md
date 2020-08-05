---
title: 重大變更-.NET Framework 至 .NET Core
titleSuffix: ''
description: 列出從 .NET Framework 到 .NET Core 的重大變更。
ms.date: 05/05/2020
ms.openlocfilehash: 5f7424fdd959044b729dfb04f4f0147fbc946bfd
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556302"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>從 .NET Framework 遷移至 .NET Core 的突破性變更

如果您要將應用程式從 .NET Framework 遷移至 .NET Core，本文中所列的重大變更可能會對您造成影響。 中斷性變更會依類別目錄，以及在這些類別中所引進的 .NET Core 版本進行分組。

> [!NOTE]
> 本文不是 .NET Framework 和 .NET Core 之間的重大變更完整清單。 最重要的重大變更會在這裡新增，因為我們會注意到它們。

## <a name="core-net-libraries"></a>Core .NET 程式庫

- [預設值為 UseShellExecute 的變更](#change-in-default-value-of-useshellexecute)
- [FileSystemInfo 擲回的 System.unauthorizedaccessexception](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)
- [不支援處理損毀的進程狀態例外狀況](#handling-corrupted-state-exceptions-is-not-supported)
- [UriBuilder 屬性不再前面加上前置字元](#uribuilder-properties-no-longer-prepend-leading-characters)
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

- [遵守 SignedCms 的布林值參數。 ComputeSignature](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="msbuild"></a>MSBuild

- [資源資訊清單檔案名變更](#resource-manifest-file-name-change)

### <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***

## <a name="networking"></a>網路功能

- [WebClient 地說 cancelasync 不一定會立即取消](#webclientcancelasync-doesnt-always-cancel-immediately)

### <a name="net-core-20"></a>.NET Core 2.0

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***

## <a name="windows-forms"></a>Windows Forms

版本3.0 中的 .NET Core 已加入 Windows Forms 支援。 如果您要將 Windows Forms 應用程式從 .NET Framework 遷移至 .NET Core，此處所列的重大變更可能會影響您的應用程式。

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

- [在 .NET Core 上一律會擲回例外狀況的 Api](unsupported-apis.md)
- [.NET Core 上無法使用的 .NET Framework 技術](../porting/net-framework-tech-unavailable.md)
