---
title: 作法：安裝和解除安裝 Windows 服務
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
ms.openlocfilehash: 0119fee443aafd1d4215260d2cf42cec9f7eba74
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59308467"
---
# <a name="how-to-install-and-uninstall-windows-services"></a>作法：安裝和解除安裝 Windows 服務
如果您正在使用 .NET Framework 開發 Windows 服務，您可以使用 [*InstallUtil.exe*](../tools/installutil-exe-installer-tool.md) 命令列公用程式來快速安裝服務應用程式。 開發人員若想發行使用者可安裝及解除安裝的 Windows 服務，則應該使用 InstallShield。 如需詳細資訊，請參閱[建立安裝程式套件 (Windows 用戶端)](https://docs.microsoft.com/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-client)。
  
> [!WARNING]
>  如果您想要從電腦解除安裝服務，則不要遵循本文中的步驟。 請改為找出安裝服務的程式或軟體套件，然後在 [設定] 中選擇 [應用程式] 以解除安裝該程式。 請注意，許多服務都是 Windows 不可或缺的一部分；如果移除這些服務，可能會導致系統不穩定。  
  
 若要使用本文中的步驟，首先需要將服務安裝程式新增至 Windows 服務。 如需詳細資訊，請參閱[逐步解說：建立 Windows 服務應用程式](../windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)。  
  
 您無法按下 F5，直接從 Visual Studio 開發環境中執行 Windows 服務專案。 您必須先安裝專案中的服務，才可以執行專案。  
  
> [!TIP]
>  您可以使用 [伺服器總管] 來確認您已安裝或解除安裝服務。 如需詳細資訊，請參閱 [How to use Server Explorer in Visual Studio](https://support.microsoft.com/help/316649/how-to-use-the-server-explorer-in-visual-studio-net-and-visual-studio) (如何在 Visual Studio 中使用伺服器總管)。
  
### <a name="install-your-service-manually"></a>以手動方式安裝您的服務  
  
1. 從 [開始] 功能表，選取 [Visual Studio \<版本>] 目錄，然後選取 [VS \<版本> 開發人員命令提示字元]。
  
     隨即顯示 Visual Studio 開發人員命令提示字元。 
  
2. 存取您的專案已編譯之可執行檔所在的目錄。  
  
3. 從命令提示字元，以您專案的可執行檔作為參數來執行 *InstallUtil.exe*：  
  
    ```console
    installutil <yourproject>.exe  
    ```  

     如果您使用 Visual Studio 開發人員命令提示字元，*InstallUtil.exe* 應該位在系統路徑中。 否則，您可以將這個檔案新增至路徑，或使用完整路徑來叫用這個檔案。 此工具會透過 .NET Framework 安裝至 %WINDIR%\Microsoft.NET\Framework[64]\\<Framework 版本>。
     
     例如：
     - 針對 32 位元版本的 .NET Framework 4 或 4.5 和更新版本，如果您的 Windows 安裝目錄是 *C:\Windows*，則預設路徑為 *C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe*。
     - 針對 64 位元版本的 .NET Framework 4 或 4.5 和更新版本，預設路徑為 *C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe*。
  
### <a name="uninstall-your-service-manually"></a>以手動方式解除安裝您的服務  
  
1. 從 [開始] 功能表，選取 [Visual Studio \<版本>] 目錄，然後選取 [VS \<版本> 開發人員命令提示字元]。
  
     隨即顯示 Visual Studio 開發人員命令提示字元。  
  
2. 從命令提示字元，以您專案的輸出作為參數來執行 *InstallUtil.exe*：  
  
    ```console  
    installutil /u <yourproject>.exe  
    ```  
  
3. 刪除服務的可執行檔之後，服務可能還是會在登錄中。 如果是這種情況，請使用命令 [sc delete](/windows-server/administration/windows-commands/sc-delete) 來從登錄中移除服務項目。  
  
## <a name="see-also"></a>另請參閱

- [Windows 服務應用程式簡介](../windows-services/introduction-to-windows-service-applications.md)
- [作法：建立 Windows 服務](../windows-services/how-to-create-windows-services.md)
- [作法：將安裝程式新增至服務應用程式](../windows-services/how-to-add-installers-to-your-service-application.md)
- [Installutil.exe (安裝程式工具)](../tools/installutil-exe-installer-tool.md)
