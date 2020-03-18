---
title: 突發更改 - .NET 框架到 .NET 核心
titleSuffix: ''
description: 列出從 .NET 框架到 .NET 核心的突發更改。
ms.date: 12/18/2019
ms.openlocfilehash: f712be14d7debc4b3008f8459e6ee925754b25f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449388"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>從 .NET 框架遷移到 .NET 核心的中斷更改

如果要將應用從 .NET 框架遷移到 .NET Core，本文中列出的重大更改可能會影響您。 分解更改按類別和在這些類別中按引入這些更改的 .NET Core 版本分組。

> [!NOTE]
> 本文不是 .NET 框架和 .NET Core 之間重大更改的完整清單。 當我們意識到這些更改時，這裡將添加最重要的重大更改。

## <a name="corefx"></a>CoreFx

- [使用殼牌執行的預設值更改](#change-in-default-value-of-useshellexecute)
- [檔案系統資訊.屬性引發的未經授權的訪問異常](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a>.NET Core 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

## <a name="cryptography"></a>Cryptography

- [簽名Cms的布林參數.計算簽名得到尊重](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a>Windows Forms

Windows 表單支援已添加到 3.0 版中的 .NET Core 中。 如果要將 Windows 表單應用從 .NET 框架遷移到 .NET Core，此處列出的重大更改可能會影響你的應用。

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

### <a name="net-core-31"></a>.NET 核心 3.1

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

## <a name="see-also"></a>另請參閱

- [始終在 .NET 內核上引發異常的 API](unsupported-apis.md)
- [.NET Core 上無法使用的 .NET Framework 技術](../porting/net-framework-tech-unavailable.md)
