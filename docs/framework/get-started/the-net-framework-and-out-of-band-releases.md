---
title: .NET Framework 和頻外發行
description: 瞭解 .NET 和頻外發行。 新功能會以頻外（OOB）發行，以改善跨平臺開發或引進新功能。
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: 9653696f46279e0c23418f92030d64839cc20518
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618762"
---
# <a name="net-framework-and-out-of-band-releases"></a>.NET Framework 與不定期發行

.NET Framework 已演進以配合不同的平臺（例如 UWP 應用程式和傳統桌面和 web 應用程式），並可讓程式碼重複使用。 除了一般 .NET Framework 版本外，新功能會以頻外（OOB）發行，以改善跨平臺開發或引進新功能。

## <a name="advantages-of-oob-releases"></a>OOB 版本的優點

將新元件或元件的更新傳送至頻外，可讓 Microsoft 為 .NET Framework 提供更頻繁的更新。 此外，我們還能更迅速地彙總和回應客戶意見。

當您在應用程式中使用 OOB 功能時，您的使用者不需要安裝最新版本的 .NET Framework 來執行您的應用程式，因為 OOB 元件會隨您的應用程式套件一起部署。

## <a name="how-oob-packages-are-distributed"></a>OOB 套件散發的方式

核心通用語言執行平臺（CLR）元件的 OOB 版本是透過[NuGet](https://www.nuget.org/)傳遞，這是 .net 的套件管理員。 NuGet 可讓您從 Visual Studio 內輕鬆流覽並將程式庫新增至您的 .NET Framework 專案。 從 Visual Studio 2012 開始，NuGet 套件管理員隨附于所有版本的 Visual Studio。 在 Visual Studio 的 [**工具**] 功能表上尋找 [ **NuGet 套件管理員**]。 如果未安裝，請依照[安裝 NuGet](/nuget/install-nuget-client-tools)上的指示進行。 如需 NuGet 的詳細資訊，請參閱[nuget](/nuget)檔。

## <a name="use-a-nuget-oob-package"></a>使用 NuGet OOB 套件

如果已安裝 NuGet 套件管理員，您可以使用 Visual Studio 中的方案總管，流覽並新增 NuGet 套件的參考：

1. 開啟 Visual Studio 中專案的捷徑功能表，然後選擇 [管理 NuGet 套件]****。 (這個選項也可以在 [專案]**** 功能表中取得)。

2. 在左窗格中，選擇 [連線]****。

3. 如果您想要使用發行前套件，請在中間窗格的下拉式清單方塊中，選擇 [包含發行前版本]****，而不要選擇 [僅限穩定版本]****。

4. 在右窗格中，使用 [搜尋]**** 方塊尋找您要使用的套件。 某些 Microsoft 套件已獲得 Microsoft .NET Framework 標誌識別，而且所有套件都會將 Microsoft 識別為發行者。

![NuGet 套件管理員。](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

如前面所述，當您部署使用 OOB 套件的應用程式時，OOB 組件會隨附於應用程式套件。

## <a name="types-of-oob-releases"></a>OOB 版本的類型

通常，OOB 套件會有一個或多個發行前版本和一個穩定版本。 發行前版本隨附的授權通常不允許轉散發，但是可讓您試用套件並提供意見。 意見會納入對套件的任何更新中。 最終版本會做為穩定套件隨 NuGet 一起散發，並且包含可讓您隨應用程式轉散發 NuGet 套件的授權。 Microsoft 支援穩定套件。 Microsoft 會為所有套件提供 IntelliSense 支援，以及其他類型的文件 (例如，部落格文章和論壇解答)。 此外，部分 (但不是所有) 套件可能會隨附原始程式碼。 如需有關新套件和更新套件的公告，您可以訂閱 [.NET Framework 部落格](https://devblogs.microsoft.com/dotnet/)。

若要尋找發行前版本和穩定套件，請在 NuGet 套件管理員中選擇 [**包含發行**前版本]。

## <a name="see-also"></a>另請參閱

- [快速入門](index.md)
