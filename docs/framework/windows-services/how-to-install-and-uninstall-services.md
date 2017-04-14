---
title: "如何：安裝及解除安裝服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "安裝, Windows 服務"
  - "安裝 Windows 服務"
  - "installutil.exe 工具"
  - "服務, 安裝"
  - "服務, 解除安裝"
  - "解除安裝應用程式, Windows 服務"
  - "解除安裝 Windows 服務"
  - "Windows 服務應用程式, 部署"
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
caps.latest.revision: 19
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 17
---
# 如何：安裝及解除安裝服務
如果您正在使用 .NET Framework 開發 Windows 服務，您可以使用稱為 InstallUtil.exe 的命令列公用程式來快速安裝服務應用程式。  如果您是開發人員並且想發行使用者可安裝及解除安裝的 Windows 服務，則應該使用 InstallShield。  請參閱 [Windows Installer 部署](http://msdn.microsoft.com/zh-tw/121be21b-b916-43e2-8f10-8b080516d2a0)。  
  
> [!WARNING]
>  如果您想要從電腦解除安裝服務，則不要遵循本文中的步驟。  請改為找出安裝服務的程式或軟體套件，然後在 \[控制台\] 中選擇 \[新增\/移除程式\] 解除安裝該程式。  請注意，許多服務都是 Windows 不可或缺的一部分；如果移除這些服務，可能會導致系統不穩定。  
  
 若要使用本文中的步驟，首先需要將服務安裝程式加入 Windows 服務。  請參閱[逐步解說：在元件設計工具中建立 Windows 服務應用程式](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)。  
  
 您無法按下 F5，直接從 Visual Studio 開發環境中執行 Windows 服務專案。  這是因為您必須先安裝專案中的服務，才可以執行專案。  
  
> [!TIP]
>  您可以啟動 \[伺服器總管\]，並確認您的服務已經安裝或解除安裝。  如需詳細資訊，請參閱[如何：存取及初始化伺服器總管\/資料庫總管](../Topic/How%20to:%20Access%20and%20Initialize%20Server%20Explorer-Database%20Explorer.md)。  
  
### 以手動方式安裝您的服務  
  
1.  在 Windows 的 \[開始\] 功能表或 \[開始\] 畫面上，依序選擇 \[Visual Studio\]、\[Visual Studio Tools\] 和 \[開發人員命令提示字元\]。  
  
     Visual Studio 命令提示字元隨即出現。  
  
2.  存取您的專案已編譯之可執行檔所在的目錄。  
  
3.  從命令提示字元，以您專案的可執行檔做為參數來執行 InstallUtil.exe：  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     如果您使用 Visual Studio 命令提示字元，InstallUtil.exe 應該在系統路徑中。  如果不在，您可以將這個檔案加入路徑，或使用完整路徑來叫用這個檔案。  這個工具會隨 .NET Framework 安裝，且其路徑為 `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`。  例如，針對 32 位元版本的 .NET Framework 4 或 4.5.\*，如果您的 Windows 安裝目錄是 C:\\Windows，則路徑為 `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`。  針對 64 位元版本的 .NET Framework 4 或 4.5.\*，預設路徑為 `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`。  
  
### 以手動方式解除安裝您的服務  
  
1.  在 Windows 的 \[開始\] 功能表或 \[開始\] 畫面上，依序選擇 \[Visual Studio\]、\[Visual Studio Tools\] 和 \[開發人員命令提示字元\]。  
  
     Visual Studio 命令提示字元隨即出現。  
  
2.  從命令提示字元，以您專案的輸出做為參數來執行 InstallUtil.exe：  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  有時候，刪除服務的可執行檔之後，服務可能還是會在登錄中。  在這種情況下，請使用命令 [sc delete](http://technet.microsoft.com/library/cc742045.aspx) 從登錄中移除服務項目。  
  
## 請參閱  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)   
 [如何：建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)   
 [如何：加入 Installer 至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)   
 [Installutil.exe \(Installer Tool\)](../../../docs/framework/tools/installutil-exe-installer-tool.md)