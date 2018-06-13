---
title: 設定 WS-Atomic 異動支援
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
ms.openlocfilehash: a89caad51f098e17bca1a5ba3df600a6dbf1dd9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495154"
---
# <a name="configuring-ws-atomic-transaction-support"></a>設定 WS-Atomic 異動支援
這個主題說明如何使用 [WS-AT 組態公用程式] 來設定 WS-AtomicTransaction (WS-AT) 支援。  
  
## <a name="using-the-ws-at-configuration-utility"></a>使用 WS-AT 組態公用程式  
 WS-AT 組態公用程式 (wsatConfig.exe) 可用來進行 WS-AT 設定。 若要啟用 WS-AT 通訊協定服務，您必須使用組態公用程式來設定 WS-AT 的 HTTPS 連接埠、將 X.509 憑證繫結至 HTTPS 連接埠，並藉由指定憑證主體名稱或指紋來設定授權的夥伴憑證。 組態公用程式也可讓您選取追蹤模式，並設定預設傳出和最大傳入的交易逾時值。  
  
 您可以使用 [元件服務] 管理主控台中的 Microsoft Management Console (MMC) 屬性頁嵌入式管理單元，或透過命令列視窗存取這個工具的功能。 透過命令列視窗在本機電腦上設定 WS-AT 支援；使用 MMC 嵌入式管理單元同時在本機和遠端電腦上進行設定。  
  
 您可以在 Windows SDK 安裝位置 "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation" 中存取命令列視窗。  
  
 如需命令列工具的詳細資訊，請參閱[Ws-atomictransaction 組態公用程式 (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)。  
  
 如果您正在[!INCLUDE[wxp](../../../../includes/wxp-md.md)]或[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]，您可以存取 MMC 嵌入式管理單元，依序巡覽至**控制控制台/系統管理工具/元件服務**、 以滑鼠右鍵按一下**我的電腦**，和選取**屬性**。 這個位置和您設定 Microsoft Distributed Transaction Coordinator (MSDTC) 的位置一樣。 組態的可用選項會分組在之下**WS-AT**  索引標籤。如果您執行 Windows Vista 或[!INCLUDE[lserver](../../../../includes/lserver-md.md)]，MMC 嵌入式管理單元可以找到按一下**啟動** 按鈕，並輸入`dcomcnfg.exe`中**搜尋**方塊。 當 MMC 開啟時，瀏覽至**我的電腦 \ 分散式交易協調器 \ 本機 DTC**節點、 以滑鼠右鍵按一下，然後選取**屬性**。 組態的可用選項會分組在之下**WS-AT**  索引標籤。  
  
 如需嵌入式管理單元的詳細資訊，請參閱[Ws-atomictransaction 組態 MMC 嵌入式管理單元](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md)。  
  
 若要啟用工具的使用者介面，您必須先登錄下列路徑中的 WsatUI.dll 檔  
  
 %PROGRAMFILES%\Microsoft SDKs\Windows\v6.0\Bin  
  
 若要登錄產品，請在 [命令提示字元] 視窗中執行下列命令：  
  
 `regasm.exe /codebase WsatUI.dll`  
  
## <a name="enabling-ws-at"></a>啟用 WS-AT  
 若要使用連接埠 443 和 X.509 憑證 (此憑證具有已安裝在本機電腦存放區中的私密金鑰) 啟用 MSDTC 內部的 WS-AT 通訊協定服務，請以下列命令使用 wsatConfig.exe 工具。  
  
 `WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`  
  
 以與您環境相關的值取代相對的參數。  
  
 若要停用 MSDTC 內部的 WS-AT 通訊協定服務，請以下列命列使用 wsatConfig.exe 工具。  
  
 `WsatConfig.exe –network:disable -restart`  
  
## <a name="configuring-trust-between-two-machines"></a>設定兩部電腦之間的信任  
 WS-AT 通訊協定服務需要系統管理員明確授權個別帳戶，才能參與分散式交易。 如果您是兩部電腦的系統管理員，可以透過下列方式設定這兩部電腦，以建立相互信任關係：交換這兩部電腦之間的正確憑證組、將這些憑證安裝到適當的憑證存放區，然後使用 wsatConfig.exe 工具將每部電腦的憑證新增至授權之參與者憑證的其他清單。 這是使用 WS-AT 在兩部電腦之間執行分散式交易的必要步驟。  
  
 下列範例說明在 A 和 B 這兩部電腦之間建立信任的步驟。  
  
### <a name="creating-and-exporting-certificates"></a>建立和匯出憑證  
 這個程序需要 MMC 憑證嵌入式管理單元。 依序開啟 [開始]、[執行] 功能表，並在輸入方塊中輸入 "mmc" 然後按下 [確定]，即可存取嵌入式管理單元。 然後，在**Console1**視窗中，瀏覽至**檔案/新增移除**嵌入式管理單元，按一下 [新增]，然後選擇**憑證**從**可用的獨立嵌入式管理單元**清單。 最後，選取**電腦帳戶**來管理和按一下**確定**。 **憑證**節點會出現在嵌入式管理單元主控台。  
  
 您必須已擁有必要的憑證，才能建立信任。 若要了解如何建立及安裝新的憑證，在以下步驟前，請參閱[How to： 建立和安裝暫時用戶端憑證在開發期間 WCF](http://go.microsoft.com/fwlink/?LinkId=158925)。  
  
1.  在電腦 A 上，使用 MMC 憑證嵌入式管理單元將現有的憑證 (certA) 匯入 LocalMachine\MY (個人節點) 和 LocalMachine\ROOT 存放區 (受信任的根憑證授權單位節點)。 若要將憑證匯入特定的節點，以滑鼠右鍵按一下節點，然後選擇 **所有工作/匯入**。  
  
2.  在電腦 B 上，使用 MMC 憑證嵌入式管理單元，建立或取得具有私密金鑰的憑證 certB，並將該憑證匯入 LocalMachine\MY (個人節點) 和 LocalMachine\ROOT 存放區 (受信任的根憑證授權單位節點)。  
  
3.  將 certA 的公開金鑰匯出至檔案 (如果尚未匯出的話)。  
  
4.  將 certB 的公開金鑰匯出至檔案 (如果尚未匯出的話)。  
  
### <a name="establishing-mutual-trust-between-machines"></a>建立電腦之間的相互信任  
  
1.  在電腦 A 上，將 certB 的檔案代表匯入 LocalMachine\MY 和 LocalMachine\ROOT 存放區。 這樣表示電腦 A 信任 certB，並可進行通訊。  
  
2.  在電腦 B 上，將 certA 的檔案匯入 LocalMachine\MY 和 LocalMachine\ROOT 存放區。 這樣表示電腦 B 信任 certA，並可進行通訊。  
  
 完成這些步驟之後，兩部電腦之間隨即建立信任，並可將這些電腦設定為使用 WS-AT 彼此通訊。  
  
### <a name="configuring-msdtc-to-use-certificates"></a>設定 MSDTC 以使用憑證  
 由於 WS-AT 通訊協定服務可同時作用為用戶端和伺服器，此服務必須同時接聽連入連線並初始化連出連線。 因此，您必須設定 MSDTC，讓它在與外部的另一方進行通訊時知道要使用的憑證，以及在接受連入通訊時知道要授權的憑證。  
  
 您可以使用 MMC WS-AT 嵌入式管理單元設定此項。 如需這項工具的詳細資訊，請參閱[Ws-atomictransaction 組態 MMC 嵌入式管理單元](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md)主題。 下列步驟描述如何在執行 MSDTC 的兩部電腦之間建立信任。  
  
1.  進行電腦 A 的設定。 「 端點憑證 」，請選取 certA。 為 「 授權憑證 」，請選取 certB。  
  
2.  進行電腦 B 的設定。 「 端點憑證 」，請選取 certB。 針對 「 授權憑證 」，請選取 certA。  
  
> [!NOTE]
>  當某一部電腦將訊息傳送至其他電腦時，傳送者會嘗試驗證收件者憑證的主體名稱和收件者的電腦名稱是否相符。 如果不符，憑證驗證就會失敗，而這兩部電腦則無法進行通訊。  
>   
>  若要讓電腦加入網域，該名稱必須為完整的網域名稱。 根據預設，工作群組上的電腦名稱為電腦的 NetBIOS 名稱。 不過，如果兩部電腦之間使用的連線中顯示了網域名稱系統 (DNS) 尾碼，則名稱也可以是該尾碼。  
>   
>  如果變更電腦的名稱，例如工作群組電腦加入網域時，您必須重新發出憑證或手動設定 DNS 尾碼。  
  
## <a name="security"></a>安全性  
 由於某些與 MSDTC 和 WS-AT 相關的設定會分別存放在 HKLM\Software\Microsoft\MSDTC 和 HKLM\Software\Microsoft\WSAT 登錄中，請確定這些登錄機碼都已受到保護，只有系統管理員可以寫入。 在 [登錄編輯程式] 工具中，以滑鼠右鍵按一下您想要保護選取的索引鍵**權限**設定適當的存取控制。 低權限使用者對於重要機碼只有唯讀權限這點，對於系統的安全性和完整性相當重要。  
  
 部署 MSDTC 時，系統管理員必須確定任何 MSDTC 資料交換都很安全。 在工作群組部署中，請對惡意使用者隔離交易基礎結構；在叢集部署中，請保護叢集登錄。  
  
## <a name="tracing"></a>追蹤  
 WS-AT 通訊協定服務支援整合式的交易特定的追蹤，可啟用及管理使用[Ws-atomictransaction 組態 MMC 嵌入式管理單元](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md)工具。  追蹤所包含的資料會指出登記特定異動的時間、異動到達終結狀態的時間、每個異動登記所接收的結果等。 您可以使用檢視的所有追蹤[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)工具。  
  
 WS-AT 通訊協定服務也支援經由 ETW 追蹤工作階段的整合式 ServiceModel 追蹤。 如此除了現有的交易追蹤之外，也會提供更詳細的通訊特定追蹤。  若要啟用這些額外的追蹤，請遵循這些步驟  
  
1.  開啟**開始/執行**功能表上，輸入方塊中輸入"regedit"，然後選取**確定**。  
  
2.  在**登錄編輯程式**，瀏覽至下列資料夾，在左窗格中，Hkey_Local_Machine\SOFTWARE\Microsoft\WSAT\3.0\  
  
3.  以滑鼠右鍵按一下`ServiceModelDiagnosticTracing`右窗格中的值，並選取**修改**。  
  
4.  在**數值資料**輸入方塊中，輸入下列有效的值，指定您想要啟用的追蹤層級的其中一個。  
  
-   0：關閉  
  
-   1：嚴重  
  
-   3：錯誤。 這是預設值  
  
-   7：警告  
  
-   15：資訊  
  
-   31：詳細資訊  
  
## <a name="see-also"></a>另請參閱  
 [WS-AtomicTransaction 設定公用程式 (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)  
 [WS-AtomicTransaction 設定 MMC 嵌入式管理單元](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md)
