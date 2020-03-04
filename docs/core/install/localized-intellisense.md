---
title: 安裝當地語系化的 IntelliSense 檔案
description: 了解如何設定開發電腦，以在 Visual Studio 中使用 .NET Core 專案的當地語系化 IntelliSense 檔案。
ms.date: 01/23/2020
ms.openlocfilehash: e45e225e58865ca2b529000ada0984fbeca850f3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157709"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a>如何安裝 .NET Core 的當地語系化 IntelliSense 檔案

[IntelliSense](/visualstudio/ide/using-intellisense) 是一種可在不同整合式開發環境 (IDE)，例如 Visual Studio 中使用的程式碼完成輔助工具。 根據預設，在開發 .NET Core 專案時，SDK 只會包含 IntelliSense 檔案的英文版本。 本文說明：

- 如何安裝這些檔案的當地語系化版本。
- 如何修改 Visual Studio 安裝以使用不同語言。

## <a name="prerequisites"></a>Prerequisites

- [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) 或更新版本。
- [Visual Studio 2019 版本 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 或更新版本。

## <a name="download-and-install-the-localized-intellisense-files"></a>下載及安裝當地語系化 IntelliSense 檔案

> [!IMPORTANT]
> 此程序需要具備將 IntelliSense 檔案複製到 .NET Core 安裝資料夾的系統管理員權限。

1. 前往[下載 IntelliSense 檔案](https://dotnet.microsoft.com/download/dotnet-core/intellisense)頁面。

1. 下載要使用的 IntelliSense 語言及版本檔案。

1. 解壓縮 ZIP 檔案的內容。

1. 流覽至 [.NET Core Intellisense] 資料夾。

   1. 巡覽至 .NET Core 安裝資料夾。 根據預設，其位於 *%ProgramFiles%\dotnet\packs*。
   1. 選擇要為其安裝 IntelliSense 的 SDK，然後巡覽至相關聯的路徑。 您有下列選擇：

      | SDK 類型        | Path                               |
      | --------------- | ---------------------------------- |
      | .NET Core       | *Microsoft.NETCore.App.Ref*        |
      | Windows 桌面 | *Microsoft.WindowsDesktop.App.Ref* |
      | .NET Standard   | *NETStandard.Library.Ref*          |

   1. 巡覽至要為其安裝當地語系化 IntelliSense 的版本。 例如，*3.1.0*。
   1. 開啟 *ref* 資料夾。
   1. 開啟 Moniker 資料夾。 例如，*netcoreapp3.1*。

   因此，您巡覽的目標完整路徑看起來會如下：*C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*。

1. 在剛開啟的 Moniker 資料夾中建立子資料夾。 資料夾名稱會指出所要使用的語言。 下表指定不同選項：

   | Language              | 資料夾名稱 |
   | --------------------- | ----------- |
   | 巴西葡萄牙文  | *pt-br*     |
   | 中文 (簡體)  | *zh-hans*   |
   | 中文 (繁體) | *zh-hant*   |
   | 法文                | *fr*        |
   | 德文                | *de*        |
   | 義大利文               | *it*        |
   | 日文              | *ja*        |
   | 韓文                | *ko*        |
   | 俄文               | *ru*        |
   | 西班牙文               | *es*        |

1. 將您在步驟 3 解壓縮的 *.xml* 檔案複製到此新資料夾。 *.xml* 檔案會依照 SDK 資料夾細分，因此請將這些檔案複製到在步驟 4 選擇的相符 SDK。

## <a name="modify-visual-studio-language"></a>修改 Visual Studio 語言

若要讓 Visual Studio 使用不同的 IntelliSense 語言，請安裝適當的語言套件。 這可以透過在[安裝期間](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional)或於稍後修改 Visual Studio 安裝來進行。 如果您已將 Visual Studio 設為選擇的語言，則 IntelliSense 安裝便已準備就緒。

### <a name="install-the-language-pack"></a>安裝語言套件

如果您並未在安裝期間安裝所需要的語言套件，請遵循以下方式更新 Visual Studio 來安裝語言套件：

> [!IMPORTANT]
> 若要安裝、更新或修改 Visual Studio，您必須使用具有系統管理員許可權的帳戶登入。 如需詳細資訊，請參閱[使用者權限和 Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio)。

1. 在電腦上找到 Visual Studio 安裝程式。

   例如，在執行 Windows 10，的電腦上，選取 [開始]，然後捲動到字母 [V]，它在其中列為 [Visual Studio Installer]。

   ![在 Windows 上開啟 Visual Studio 安裝程式](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > 您也可以在下列位置找到 Visual Studio 安裝程式：
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   您可能需要更新安裝程式才能繼續。 若是如此，請遵循提示。

1. 在安裝程式中，尋找要新增語言套件的目標 Visual Studio 版本，然後選擇 [修改]。

   ![更新或修改 Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > 如果您沒有看到 [修改] 按鈕，但有看到 [更新] 按鈕，則表示您需要先更新 Visual Studio，之後才能修改安裝。
   > 更新完成後，[修改] 按鈕應該會隨即出現。

1. 在 [語言套件] 索引標籤中，選取或取消選取要安裝或解除安裝的語言。

   ![Visual Studio [語言套件] 索引標籤](./media/localized-intellisense/vs-modify-language-packs.png)

1. 選擇 [修改]。 更新會開始進行。

### <a name="modify-language-settings-in-visual-studio"></a>修改 Visual Studio 中的語言設定

在安裝所需要的語言套件後，請修改您的 Visual Studio 設定，以使用不同語言：

1. 開啟 Visual Studio。

1. 在 [開始] 視窗中，選擇 [不使用程式碼繼續]。

1. 在功能表列上，選取 [**工具**] [ > **選項**]。 [選項] 對話方塊隨即開啟。

1. 在 [**環境**] 節點底下，選擇 [**國際設定**]。

1. 在 [語言] 下拉式清單中，選取所需要的語言。 選擇 [確定]。

1. 對話方塊會通知您必須重新啟動 Visual Studio，才能使變更生效。 選擇 [確定]。

1. 重新啟動 Visual Studio。

之後在開啟以您剛安裝 IntelliSense 檔案版本為目標的 .NET Core 專案時，IntelliSense 應該就會如預期般運作。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的 IntelliSense](/visualstudio/ide/using-intellisense)
