---
title: Windows Communication Foundation 範例的單次安裝程序
ms.date: 03/30/2017
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
ms.openlocfilehash: 954ec04d2ef1ca7667b4f75a8a6652010b5dbd33
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121622"
---
# <a name="one-time-setup-procedure-for-the-windows-communication-foundation-samples"></a>Windows Communication Foundation 範例的單次安裝程序

大多數 Windows 通訊基礎 (WCF) 範例託管在 Internet 資訊服務 (IIS) 中,並且從公共虛擬目錄運行。 此一次性設置過程在磁碟上創建一個資料夾;它還向名為 **「服務模型範例**」的 IIS 添加了一個虛擬目錄。

**ServiceModelSample**虛擬目錄用於生成和運行使用IIS託管服務的所有範例。 這是執行範例時唯一必要的虛擬目錄。 建立範例將會取代此虛擬目錄中所有先前部署的服務；此虛擬目錄中只會部屬並提供最近建立的範例。

> [!NOTE]
> 您必須在本機系統管理員帳戶下執行所有的命令。 如果使用 Windows 7、Windows Vista 或 Windows Server 2008 R2,則還必須使用提升的許可權執行命令提示符。 為此,請右鍵單擊命令提示圖示,然後單擊"**以管理員身份運行**"。 本主題中的所有命令都必須在擁有適當路徑設定的命令提示字元下執行。  最簡單的確保方式就是使用 Visual Studio 命令提示字元。 要打開此提示,請按下 **「開始**」,選擇 **「所有程式**」,向下滾動到**Visual Studio 2010**,選擇**視覺化工作室工具**,右鍵按下**視覺工作室命令提示(2010),** 然後按下 **「 以管理員身份執行**」。。 如果您已經安裝其中一個 Visual Studio Express Edition，就無法使用這個命令提示字元，而且您必須將 "C:\Windows\Microsoft.Net\Framework\v4.0" 加入至系統路徑中。

### <a name="one-time-setup-procedure-for-wcf-samples"></a>WCF 範例的單次安裝程序

1. 確保設置了ASP.NET。 有關如何設置ASP.NET的詳細資訊,請參閱[網路資訊服務託管說明](internet-information-service-hosting-instructions.md)。

2. 確保安裝了 .NET 框架 4。 搜尋以下目錄搜尋 v4.0(或更高版本): **[Windows]Microsoft.NET_Framework**

3. 確保您安裝了 Visual Studio 2012 或更高版本,或者您的作業系統是 Windows Server 2008 SP2 或更高版本。

4. 執行下列命令。 有關必須運行這些命令的原因的詳細資訊,請參閱[IIS 託管服務失敗](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752252(v=vs.90))。

    > [!WARNING]
    > 如果您重新安裝了 IIS，就必須再次執行下列命令。

    ```console
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r
    ```

    > [!WARNING]
    > 運行該命令`aspnet_regiis –i –enable`將使預設應用池使用 .NET Framework 4 運行,這可能會為同一台電腦上的其他應用程序帶來不相容問題。

5. 按照[防火牆說明](firewall-instructions.md)啟用示例使用的埠。

6. 檢查以下預設目錄:\<安裝磁碟機>:**\WF_WCF_Samples**。 如果先前安裝了範例，這就是預設目錄。

7. 如果未安裝範例,請從 .NET 框架 4 的[Windows 通信基礎 (WCF) 和 Windows 工作流基礎 (WF) 範例](https://www.microsoft.com/download/details.aspx?id=21459)安裝它們。

8. 安裝範例後,轉到\<: 安裝驅動器>:**\\{WF_WCF_Samples\WCF_ 安裝程式**

9. 運行**Setupvroot.bat**批次處理檔。 會執行下列步驟：

    - 在 IIS 中建立名為 ServiceModelSamples 的虛擬目錄。

    - 建立名為 %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples 和 %SystemDrive%\Inetpub\wwwroot\ServiceModelSamples\bin 的新磁碟目錄。

    如果您希望手動設定這些目錄,請參考[虛擬目錄設定說明](virtual-directory-setup-instructions.md)。 若要還原此步驟中完成的所有變更，請在範例使用完畢之後執行 cleanupvroot.bat。

    > [!NOTE]
    > 除非您執行 cleanupvroot.bat，否則只要在電腦上執行這個程序一次即可。

10. 您必須將修改 %SystemDrive%\inetpub\wwwroot 的權限，授與您要用來建置範例和 Network Service 使用者的帳戶。 在建立時，有些 Web 裝載的範例可能會嘗試將編譯後的二進位複製到先前所述的位置，如果您沒有設定適當的權限，建立就會中斷。 或者,您可以保留許可權,並將 SDK 命令提示符或 Visual Studio 命令提示符 (2012) 作為管理員運行,或者在 Visual Studio 2012 中生成範例,也可以作為管理員運行。

    > [!NOTE]
    > 如果沒有完成這個步驟，所有 IIS 裝載的範例都會在建立時失敗。 請確定權限的設定正確，或以系統管理員身分同時執行 SDK 命令提示字元和 Visual Studio 命令提示字元 (2012)。

11. 在電腦上建立 C:\logs 目錄；某些案例可能會需要這個目錄。 請確認適當的帳戶已經將寫入權限授與此資料夾。 對於 Windows 7、Windows Vista 和 Windows 伺服器 2008 R2,此帳戶為**網路服務**。 對於 Windows 伺服器 2008,該帳戶為 NT 頒發機構+網路服務。 對於 Windows XP 和 Windows 伺服器 2003,該帳戶為 ASPNET。

12. 執行 Setupcerttool.bat 檔案。 此檔案位於\<「安裝路徑>\WF_WCF_Samples_WCF_安裝程式]資料夾中。  這個指令碼會執行下列工作：

    - 建立 FindPrivateKey 工具。

    - 建立名為 %ProgramFiles%\ServiceModelSampleTools 的目錄。

    - 將新的 FindPrivateKey 工具複製到此目錄。

    使用憑證且裝載在 IIS 中的範例需要這項工具。

    > [!NOTE]
    > 基於安全性考量，在您完成範例後，請記得執行名為 Cleanupvroot.bat 的批次檔，移除虛擬目錄定義以及在上述安裝步驟中授與的權限。

13. 自我裝載 (而非裝載於 IIS) 的範例必須有權限將 HTTP 位址註冊到電腦上，以便進行接聽。 HTTP 命名空間保留區的權限來自用以執行範例的使用者帳戶。 根據預設，系統管理員帳戶擁有註冊任何 HTTP 位址的權限。 至於非系統管理員帳戶，則必須具有範例所用之 HTTP 命名空間的權限。 如需如何設定命名空間保留的詳細資訊，請參閱[設定 HTTP 和 HTTPS](../feature-details/configuring-http-and-https.md)。

14. 有些範例需要訊息佇列。 有關安裝說明,請參閱[安裝消息佇列 (MSMQ)。](installing-message-queuing-msmq.md)

    > [!NOTE]
    > 請務必在您執行需要訊息佇列的任何範例之前，啟動 MSMQ 服務。

15. 有些範例需要憑證。 請參考[網際網路資訊服務 (IIS) 伺服器憑證安裝說明](iis-server-certificate-installation-instructions.md)。
