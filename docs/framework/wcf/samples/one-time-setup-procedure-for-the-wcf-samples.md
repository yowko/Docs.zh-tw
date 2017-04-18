---
title: "Windows Communication Foundation 範例的單次安裝程序 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
caps.latest.revision: 83
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 83
---
# Windows Communication Foundation 範例的單次安裝程序
大部分的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 範例都是裝載在網際網路資訊服務 \(IIS\) 中，並且從共用虛擬目錄執行。這個單次安裝程序會在磁碟上建立資料夾，也會將名為 **ServiceModelSamples** 的虛擬目錄加入至 IIS。  
  
 **ServiceModelSamples** 虛擬目錄會用在建立及執行所有使用裝載於 IIS 之服務的範例。這是執行範例時唯一必要的虛擬目錄。建立範例將會取代此虛擬目錄中所有先前部署的服務；此虛擬目錄中只會部屬並提供最近建立的範例。  
  
> [!NOTE]
>  您必須在本機系統管理員帳戶下執行所有的命令。如果您是使用 Windows 7、[!INCLUDE[windowsver](../../../../includes/windowsver-md.md)] 或 Windows Server 2008 R2，也必須使用更高的權限來執行命令提示字元。如果要執行這項操作，請以滑鼠右鍵按一下命令提示字元圖示，然後按一下 \[**以系統管理員身分執行**\]。本主題中的所有命令都必須在擁有適當路徑設定的命令提示字元下執行。最簡單的確保方式就是使用 Visual Studio 命令提示字元。若要開啟此提示字元，請按一下 \[**開始**\]、選取 \[**所有程式**\]、向下捲動到 \[**Visual Studio 2010**\]、選取 \[**Visual Studio Tools**\]、以滑鼠右鍵按一下 \[**Visual Studio 命令提示字元 \(2010\)**\]，然後按一下 \[**以系統管理員身分執行**\]。如果您已經安裝其中一個 Visual Studio Express Edition，就無法使用這個命令提示字元，而且您必須將 "C:\\Windows\\Microsoft.Net\\Framework\\v4.0" 加入至系統路徑中。  
  
### WCF 範例的單次安裝程序  
  
1.  請確定已安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]如何安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 的詳細資訊，請參閱[Internet Information Service 裝載指示](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)。  
  
2.  請確定已安裝 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]。然後，在下列目錄中搜尋 v4.0 \(或更新版本\)：**\\Windows\\Microsoft.NET\\Framework**  
  
3.  如果未安裝 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]，而且您的作業系統不是 Windows Server 2008 SP2 或更新版本，請安裝 [Hotfix 251798](http://go.microsoft.com/fwlink/?LinkId=184693)。  
  
4.  執行下列命令。如需為什麼必須執行這些命令的詳細資訊，請參閱 [IIS Hosted Service Fails](http://msdn.microsoft.com/zh-tw/ee5499fc-1b10-4cda-a9b1-13dba70f05f8)。  
  
    > [!WARNING]
    >  如果您重新安裝了 IIS，就必須再次執行下列命令。  
  
    ```  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r  
    ```  
  
    > [!WARNING]
    >  使用 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] 執行命令 `aspnet_regiis –i –enable` 將會執行預設應用程式集區，這可能會對相同電腦上的其他應用程式產生不相容的問題。  
  
5.  請依照[防火牆指示](../../../../docs/framework/wcf/samples/firewall-instructions.md)執行，以啟用範例所使用的通訊埠。  
  
6.  請檢查下列預設目錄：\<InstallDrive\>:**\\WF\_WCF\_Samples**。如果先前安裝了範例，這就是預設目錄。  
  
7.  如果未安裝範例，您可以從 [Visual C\#](http://go.microsoft.com/fwlink/?LinkId=190939) 或 [Visual Basic](http://go.microsoft.com/fwlink/?LinkID=193373) 的範例下載位置進行安裝。  
  
8.  安裝範例之後，請移至：\<InstallDrive\>:**\\WF\_WCF\_Samples\\WCF\\Setup\\**  
  
9. 執行 **Setupvroot.bat** 批次檔。系統會執行下列步驟：  
  
    -   在 IIS 中建立名為 ServiceModelSamples 的虛擬目錄。  
  
    -   建立名為 %SystemDrive%\\Inetpub\\wwwroot\\ServiceModelSamples 和 %SystemDrive%\\Inetpub\\wwwroot\\ServiceModelSamples\\bin 的新磁碟目錄。  
  
     如果您想要手動設定這些目錄，請參閱[虛擬目錄安裝指示](../../../../docs/framework/wcf/samples/virtual-directory-setup-instructions.md)。若要還原此步驟中完成的所有變更，請在範例使用完畢之後執行 cleanupvroot.bat。  
  
    > [!NOTE]
    >  除非您執行 cleanupvroot.bat，否則只要在電腦上執行這個程序一次即可。  
  
10. 您必須將修改 %SystemDrive%\\inetpub\\wwwroot 的權限，授與您要用來建置範例和 Network Service 使用者的帳戶。在建立時，有些 Web 裝載的範例可能會嘗試將編譯後的二進位複製到先前所述的位置，如果您沒有設定適當的權限，建立就會中斷。或者，您可以不改變權限，而以系統管理員身分執行 SDK 命令提示字元或 Visual Studio 命令提示字元 \(2012\)，或在以系統管理員身分執行的 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中建置範例。  
  
    > [!NOTE]
    >  如果沒有完成這個步驟，所有 IIS 裝載的範例都會在建立時失敗。請確定權限的設定正確，或以系統管理員身分同時執行 SDK 命令提示字元和 Visual Studio 命令提示字元 \(2012\)。  
  
11. 在電腦上建立 C:\\logs 目錄；某些案例可能會需要這個目錄。請確認適當的帳戶已經將寫入權限授與此資料夾。若是 Windows 7、[!INCLUDE[wv](../../../../includes/wv-md.md)] 和 Windows Server 2008 R2，此帳戶為 **Network Service**。若是 [!INCLUDE[lserver](../../../../includes/lserver-md.md)]，此帳戶為 NT Authority\\Network Service。若是 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 和 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]，此帳戶則為 ASPNET。  
  
12. 執行 Setupcerttool.bat 檔案。此檔案位於 \<InstallPath\>\\WF\_WCF\_Samples\\WCF\\Setup\\ 資料夾。這個指令碼會執行下列工作：  
  
    -   建立 FindPrivateKey 工具。  
  
    -   建立名為 %ProgramFiles%\\ServiceModelSampleTools 的目錄。  
  
    -   將新的 FindPrivateKey 工具複製到此目錄。  
  
     使用憑證且裝載在 IIS 中的範例需要這項工具。  
  
    > [!NOTE]
    >  基於安全性考量，在您完成範例後，請記得執行名為 Cleanupvroot.bat 的批次檔，移除虛擬目錄定義以及在上述安裝步驟中授與的權限。  
  
13. 自我裝載 \(而非裝載於 IIS\) 的範例必須有權限將 HTTP 位址註冊到電腦上，以便進行接聽。HTTP 命名空間保留區的權限來自用以執行範例的使用者帳戶。根據預設，系統管理員帳戶擁有註冊任何 HTTP 位址的權限。至於非系統管理員帳戶，則必須具有範例所用之 HTTP 命名空間的權限。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]如何設定命名空間保留的詳細資訊，請參閱[設定 HTTP 和 HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)。  
  
14. 有些範例需要訊息佇列。如需安裝指示，請參閱[安裝訊息佇列 \(MSMQ\)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)。  
  
    > [!NOTE]
    >  請務必在您執行需要訊息佇列的任何範例之前，啟動 MSMQ 服務。  
  
15. 有些範例需要憑證。請參閱 [網際網路資訊服務 \(IIS\) 伺服器憑證安裝指示](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)。  
  
## 請參閱