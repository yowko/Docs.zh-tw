---
title: .NET 框架和帶外版本
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: 058bc1a5180060d3c3c6ba4ead1f074a14336b53
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181570"
---
# <a name="net-framework-and-out-of-band-releases"></a>.NET 框架和帶外版本

.NET Framework 已發展為適應不同的平臺，如 UWP 應用和傳統桌面和 Web 應用，並最大限度地提高代碼重用。 除了常規的 .NET 框架版本外，新功能還從頻段 （OOB） 外發佈，以改進跨平臺開發或引入新功能。

## <a name="advantages-of-oob-releases"></a>OOB 版本的優點

將新元件或更新傳送到帶外元件使 Microsoft 能夠更頻繁地向 .NET Framework 提供更新。 此外，我們還能更迅速地彙總和回應客戶意見。

在應用中使用 OOB 功能時，使用者不必安裝最新版本的 .NET Framework 來運行應用，因為 OOB 程式集隨應用包一起部署。

## <a name="how-oob-packages-are-distributed"></a>OOB 套件散發的方式

核心通用語言運行時 （CLR） 元件的 OOB 版本通過[NuGet（](https://www.nuget.org/)是 .NET 的包管理器）提供。 NuGet 使您能夠從 Visual Studio 中輕鬆流覽 .NET 框架專案並將庫添加到專案中。 從 Visual Studio 2012 開始，所有版本的 Visual Studio 都包含 NuGet 套裝軟體管理器。 在視覺化工作室的 **"工具"** 功能表上查找**NuGet 包管理器**。 如果未安裝，請按照安裝[NuGet](/nuget/install-nuget-client-tools)的說明操作。 有關 NuGet 的詳細資訊，請參閱[NuGet 文檔](/nuget)。

## <a name="use-a-nuget-oob-package"></a>使用 NuGet OOB 套裝軟體

如果安裝了 NuGet 包管理器，則可以在 Visual Studio 中使用解決方案資源管理器流覽並添加對 NuGet 包的引用：

1. 開啟 Visual Studio 中專案的捷徑功能表，然後選擇 [管理 NuGet 套件]****。 (這個選項也可以在 [專案]**** 功能表中取得)。

2. 在左窗格中，選擇 [連線]****。

3. 如果您想要使用發行前套件，請在中間窗格的下拉式清單方塊中，選擇 [包含發行前版本]****，而不要選擇 [僅限穩定版本]****。

4. 在右窗格中，使用 [搜尋]**** 方塊尋找您要使用的套件。 某些 Microsoft 套件已獲得 Microsoft .NET Framework 標誌識別，而且所有套件都會將 Microsoft 識別為發行者。

![NuGet 包管理器。](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

如前面所述，當您部署使用 OOB 套件的應用程式時，OOB 組件會隨附於應用程式套件。

## <a name="types-of-oob-releases"></a>OOB 版本的類型

通常，OOB 套件會有一個或多個發行前版本和一個穩定版本。 發行前版本隨附的授權通常不允許轉散發，但是可讓您試用套件並提供意見。 意見會納入對套件的任何更新中。 最終版本會做為穩定套件隨 NuGet 一起散發，並且包含可讓您隨應用程式轉散發 NuGet 套件的授權。 Microsoft 支援穩定套件。 Microsoft 會為所有套件提供 IntelliSense 支援，以及其他類型的文件 (例如，部落格文章和論壇解答)。 此外，部分 (但不是所有) 套件可能會隨附原始程式碼。 如需有關新套件和更新套件的公告，您可以訂閱 [.NET Framework 部落格](https://devblogs.microsoft.com/dotnet/)。

要查找預發行包和穩定包，請在 NuGet 套裝軟體管理器中選擇 **"包括預發行**"。

## <a name="see-also"></a>另請參閱

- [開始使用](index.md)
