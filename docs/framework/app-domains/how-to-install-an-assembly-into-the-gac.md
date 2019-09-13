---
title: 作法：將組件安裝到全域組件快取
ms.date: 02/05/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e2d051cda9861da1af2caa65160b6e753b24bd1
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926506"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>作法：將組件安裝到全域組件快取

全域組件快取 (GAC) 會儲存數個應用程式共用的組件。 使用下列其中一個元件，將組件安裝到[全域組件快取](gac.md)： 

- [Windows Installer](#windows-installer)
- [全域組件快取工具](#global-assembly-cache-tool)

> [!IMPORTANT]
> 您只能將強式名稱組件安裝到 GAC。 如需如何建立強式名稱組件的資訊，請參閱[如何：使用強式名稱簽署組件](how-to-sign-an-assembly-with-a-strong-name.md)。

## <a name="windows-installer"></a>Windows Installer

[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache)，Windows 安裝引擎，這是將組件新增至全域組件快取的建議方式。 Windows Installer 會提供全域組件快取的組件參考計數，以及其他功能。 若要建立 Windows Installer 的安裝程式套件，請使用[適用於 Visual Studio 2017 的 WiX Toolset 延伸模組](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)。

## <a name="global-assembly-cache-tool"></a>全域組件快取工具

您可以使用[全域組件快取工具 (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) 將組件新增至全域組件快取，並檢視全域組件快取的內容。

   > [!NOTE]
   > *Gacutil.exe* 只能用於開發目的。 請勿使用這個檔案將生產組件安裝到全域組件快取。

使用 *gacutil.exe* 將組件安裝到 GAC 的語法如下所示：

```console
gacutil -i <assembly name>
```

在這個命令中，\<組件名稱> 是安裝在全域組件快取的組件名稱。

如果 *gacutil.exe* 不在您的系統路徑中，請使用 [VS \<版本> *開發人員命令提示字元*](../tools/developer-command-prompt-for-vs.md)。

下列範例會將檔案名稱為 *hello.dll* 的組件安裝到全域組件快取。

```console
gacutil -i hello.dll
```

> [!NOTE]
> 在舊版 .NET Framework 中，*Shfusion.dll* Windows 殼層延伸可讓您將組件拖曳到 [檔案總管]，藉此安裝組件。 從 .NET Framework 4 開始，*Shfusion.dll* 已淘汰。

## <a name="see-also"></a>另請參閱

- [使用組件和全域組件快取](working-with-assemblies-and-the-gac.md)
- [如何：從全域組件快取移除組件](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (全域組件快取工具)](../tools/gacutil-exe-gac-tool.md)
- [如何：使用強式名稱簽署組件](how-to-sign-an-assembly-with-a-strong-name.md)
