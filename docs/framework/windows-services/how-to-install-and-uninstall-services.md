---
title: 如何:安裝和卸載 Windows 服務
ms.date: 02/05/2019
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, apps, Windows services
- installation, Windows services
- uninstalling Windows services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
author: ghogen
ms.openlocfilehash: 8937ef8b4007253b06444e59b292395084e4df2f
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607915"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>如何:安裝和卸載 Windows 服務

如果您使用 .NET 框架開發 Windows 服務,則可以使用[*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md)命令列實用程式或[PowerShell](/powershell/scripting/overview)快速安裝服務應用。 開發人員若想發行使用者可安裝及解除安裝的 Windows 服務，則應該使用 InstallShield。 有關詳細資訊,請參閱[創建安裝程式包(Windows 桌面)。](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop)

> [!WARNING]
> 如果您想要從電腦解除安裝服務，則不要遵循本文中的步驟。 請改為找出安裝服務的程式或軟體套件，然後在 [設定] 中選擇 [應用程式]**** 以解除安裝該程式。 請注意，許多服務都是 Windows 不可或缺的一部分；如果移除這些服務，可能會導致系統不穩定。

若要使用本文中的步驟，首先需要將服務安裝程式新增至 Windows 服務。 有關詳細資訊,請參閱[演練:創建 Windows 服務應用](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)。

您無法按下 F5，直接從 Visual Studio 開發環境中執行 Windows 服務專案。 您必須先安裝專案中的服務，才可以執行專案。

> [!TIP]
> 您可以使用 [伺服器總管]**** 來確認您已安裝或解除安裝服務。 如需詳細資訊，請參閱 [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio) (如何在 Visual Studio 中使用伺服器總管)。

### <a name="install-your-service-manually-using-installutilexe-utility"></a>使用 InstallUtil.exe 實用程式手動安裝服務

1. 從 [開始]**** 功能表，選取 [Visual Studio \<版本**>]**** 目錄，然後選取 [VS \<版本**> 開發人員命令提示字元]****。

     隨即顯示 Visual Studio 開發人員命令提示字元。

2. 存取您的專案已編譯之可執行檔所在的目錄。

3. 從命令提示字元，以您專案的可執行檔作為參數來執行 *InstallUtil.exe*：

    ```console
    installutil <yourproject>.exe
    ```

     如果您使用 Visual Studio 開發人員命令提示字元，*InstallUtil.exe* 應該位在系統路徑中。 否則，您可以將這個檔案新增至路徑，或使用完整路徑來叫用這個檔案。 此工具與 .NET 框架一起安裝*在\\%WINDIR% _Microsoft.NET_Framework[64]\><framework_version。*

     例如：
     - 針對 32 位元版本的 .NET Framework 4 或 4.5 和更新版本，如果您的 Windows 安裝目錄是 *C:\Windows*，則預設路徑為 *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*。
     - 針對 64 位元版本的 .NET Framework 4 或 4.5 和更新版本，預設路徑為 *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*。

### <a name="uninstall-your-service-manually-using-installutilexe-utility"></a>使用 InstallUtil.exe 實用程式手動卸載服務

1. 從 [開始]**** 功能表，選取 [Visual Studio \<版本**>]**** 目錄，然後選取 [VS \<版本**> 開發人員命令提示字元]****。

     隨即顯示 Visual Studio 開發人員命令提示字元。

2. 從命令提示字元，以您專案的輸出作為參數來執行 *InstallUtil.exe*：

    ```console
    installutil /u <yourproject>.exe
    ```

3. 刪除服務的可執行檔之後，服務可能還是會在登錄中。 如果是這種情況，請使用命令 [sc delete](/windows-server/administration/windows-commands/sc-delete) 來從登錄中移除服務項目。

### <a name="install-your-service-manually-using-powershell"></a>使用 PowerShell 手動安裝服務

1. 在 **「開始」** 選單中,選擇**Windows PowerShell**目錄,然後選擇**Windows PowerShell**。

2. 存取您的專案已編譯之可執行檔所在的目錄。

3. 使用項目輸出執行[**New-服務**](/powershell/module/microsoft.powershell.management/new-service)cmdlet,並將服務名稱作為參數執行:

    ```powershell
    New-Service -Name "YourServiceName" -BinaryPathName <yourproject>.exe
    ```

### <a name="uninstall-your-service-manually-using-powershell"></a>使用 PowerShell 手動卸載服務

1. 在 **「開始」** 選單中,選擇**Windows PowerShell**目錄,然後選擇**Windows PowerShell**。

2. 執行以服務名稱稱為參數的[**刪除服務**](/powershell/module/microsoft.powershell.management/remove-service)cmdlet:

    ```powershell
    Remove-Service -Name "YourServiceName"
    ```

3. 刪除服務的可執行檔之後，服務可能還是會在登錄中。 如果是這種情況，請使用命令 [sc delete](/windows-server/administration/windows-commands/sc-delete) 來從登錄中移除服務項目。

    ```powershell
    sc.exe delete "YourServiceName"
    ```

## <a name="see-also"></a>另請參閱

- [Windows 服務應用程式簡介](../windows-services/introduction-to-windows-service-applications.md)
- [如何:建立 Windows 服務](../windows-services/how-to-create-windows-services.md)
- [如何:將安裝程式新增到服務應用程式](../windows-services/how-to-add-installers-to-your-service-application.md)
- [Installutil.exe (安裝程式工具)](../tools/installutil-exe-installer-tool.md)
