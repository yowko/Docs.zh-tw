---
title: 操作說明：將組件安裝到全域組件快取
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 64878a795a7c5b790c8991064e32b82505685c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155559"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>操作說明：將組件安裝到全域組件快取

全域組件快取 (GAC) 會儲存數個應用程式共用的組件。 使用下列其中一個元件，將組件安裝到[全域組件快取](gac.md)：

- [Windows 安裝程式](#windows-installer)
- [全域組件快取工具](#global-assembly-cache-tool)

> [!IMPORTANT]
> 只能將強命名程式集安裝到全域組件快取中。 有關如何創建強式名稱程式集的資訊，請參閱[如何：使用強式名稱對程式集進行簽名](../../standard/assembly/sign-strong-name.md)。

## <a name="windows-installer"></a>Windows Installer

[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache)，Windows 安裝引擎，這是將組件新增至全域組件快取的建議方式。 Windows Installer 會提供全域組件快取的組件參考計數，以及其他功能。 若要建立 Windows Installer 的安裝程式套件，請使用[適用於 Visual Studio 2017 的 WiX Toolset 延伸模組](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)。

## <a name="global-assembly-cache-tool"></a>全域組件快取工具

可以使用[.NET 全域組件快取實用程式 （gacutil.exe）](../tools/gacutil-exe-gac-tool.md)將程式集添加到全域組件快取並查看全域組件快取的內容。

   > [!NOTE]
   > *Gacutil.exe* 只能用於開發目的。 請勿使用這個檔案將生產組件安裝到全域組件快取。

使用 *gacutil.exe* 將組件安裝到 GAC 的語法如下所示：

```cmd
gacutil -i <assembly name>
```

在此命令中，*\<程式集名稱>* 是要在全域組件快取中安裝的程式集的名稱。

如果*gacutil.exe*不在系統路徑中，請使用["開發人員"命令提示符進行 VS*\<版本>* ](../tools/developer-command-prompt-for-vs.md)。

下列範例會將檔案名稱為 *hello.dll* 的組件安裝到全域組件快取。

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> 在舊版 .NET Framework 中，*Shfusion.dll* Windows 殼層延伸可讓您將組件拖曳到 [檔案總管]，藉此安裝組件。 從 .NET Framework 4 開始，*Shfusion.dll* 已淘汰。

## <a name="see-also"></a>另請參閱

- [使用程式集和全域組件快取](working-with-assemblies-and-the-gac.md)
- [如何：從全域組件快取中刪除程式集](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe（全球裝配緩存工具）](../tools/gacutil-exe-gac-tool.md)
- [如何：使用強式名稱對程式集進行簽名](../../standard/assembly/sign-strong-name.md)
