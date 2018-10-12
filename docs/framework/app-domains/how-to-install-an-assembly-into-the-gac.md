---
title: 將組件安裝到 GAC
ms.date: 09/20/2018
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
ms.openlocfilehash: d365ac77fe6cd7fc4fca36705729ec12b06d6830
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46584577"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>操作說明：將組件安裝到全域組件快取

有兩種方式可以將強式名稱組件安裝到全域組件快取 (GAC) 中。

> [!IMPORTANT]
> 只有強式名稱組件才能安裝至 GAC。 如需如何建立強式名稱組件的資訊，請參閱[如何：使用強式名稱簽署組件](how-to-sign-an-assembly-with-a-strong-name.md)。

## <a name="windows-installer"></a>Windows Installer

[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache)，Windows 安裝引擎，這是將組件新增至全域組件快取的建議方式。 Windows Installer 會提供全域組件快取的組件參考計數，以及其他功能。 您可以使用[適用於 Visual Studio 2017 的 WiX Toolset 擴充功能](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension)，來建立 Windows Installer 的安裝程式套件。

## <a name="global-assembly-cache-tool"></a>全域組件快取工具

您可以使用[全域組件快取工具 (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) 將強式名稱的組件新增到全域組件快取，和檢視全域組件快取的內容。

   > [!NOTE]
   > Gacutil.exe 僅適合開發用途，不應用來安裝產品組件到全域組件快取中。

gacutil 的語法如下：

```shell
gacutil -i <assembly name>
```

在這個命令中，「組件名稱」是安裝在全域組件快取的組件名稱。

下列範例安裝檔名為 `hello.dll` 的組件到全域組件快取中。

```shell
gacutil -i hello.dll
```

> [!NOTE]
> 在舊版 .NET Framework 中，可利用 Shfusion.dll Windows Shell Extension 將組件拖曳到 [檔案總管] 中，藉此安裝組件。 從 .NET Framework 4 開始，Shfusion.dll 已淘汰。

## <a name="see-also"></a>另請參閱

- [使用組件和全域組件快取](working-with-assemblies-and-the-gac.md)
- [操作說明：從全域組件快取移除組件](how-to-remove-an-assembly-from-the-gac.md)
- [Gacutil.exe (全域組件快取工具)](../tools/gacutil-exe-gac-tool.md)
- [如何：使用強式名稱簽署組件](how-to-sign-an-assembly-with-a-strong-name.md)