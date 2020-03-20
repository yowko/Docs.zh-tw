---
title: 平臺安全性原則
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform security model [WPF]
- Common Language Runtime (CLR) security features
- operating system security model [WPF]
- Internet Explorer security features [WPF]
- Security-Critical method
- CLR security features [WPF]
- security model [WPF]
- security model [WPF], platform
- WPF [WPF], about security model
- Windows Presentation Foundation [WPF], about security model
- security model [WPF], operating system
ms.assetid: 2a39a054-3e2a-4659-bcb7-8bcea490ba31
ms.openlocfilehash: 258fcd7c51ea59de03fe60a4eeb9a82dd1c7efca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174598"
---
# <a name="wpf-security-strategy---platform-security"></a>WPF 安全性策略 – 平台安全性
雖然 Windows 演示基礎 （WPF） 提供各種安全服務，但它也利用了底層平臺的安全功能，其中包括作業系統、CLR 和 Internet 資源管理器。 這些層組合為 WPF 提供強大的縱深防禦安全模型，可嘗試避免任何單點故障，如下圖所示：  
  
 ![顯示 WPF 安全模型的圖表。](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 本主題的其餘部分將討論每個層中專門與 WPF 相關的功能。  

## <a name="operating-system-security"></a>作業系統安全性  
Windows 的核心提供了幾個安全功能，這些功能構成了所有 Windows 應用程式的安全基礎，包括使用 WPF 構建的應用程式。 本主題討論這些對 WPF 重要的安全功能的廣度，以及 WPF 如何與這些功能集成以提供更深入的防禦。  
  
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 除了對 Windows 的一般回顧和加強外，本主題中還將討論 Windows XP SP2 中的三個關鍵功能：  
  
- /GS 編譯  
  
- 微軟視窗更新。  
  
#### <a name="gs-compilation"></a>/GS 編譯  
 Windows XP SP2 通過重新編譯許多核心系統庫（包括 CLR 等所有 WPF 依賴項）來提供保護，以説明緩解緩衝區溢位。 搭配 C/C++ 命令列編譯器使用 /GS 參數即可達成這個目的。 雖然這樣做應該能夠明確避免發生緩衝區滿溢的情況，但是 /GS 編譯還提供一個深入防禦範例，可防止無意中或惡意利用緩衝區滿溢所造成的潛在弱點遭到攻擊。  
  
 在過去，緩衝區滿溢一直是造成許多重大安全性攻擊的原因。 當攻擊者利用程式碼弱點，插入將緩衝區寫爆的惡意程式碼時，就會發生緩衝區滿溢的情況。 這會讓攻擊者有機會透過覆寫函式的傳回位址，來劫持執行該程式碼的處理序，以執行攻擊者的程式碼。 結果是，惡意程式碼可以利用與被劫持的處理序相同的權限來執行任意程式碼。  
  
 在高級別上，-GS 編譯器標誌通過注入特殊安全 Cookie 來保護具有本地字串緩衝區的函數的返回位址，從而防止某些潛在的緩衝區溢位。 在函式傳回之後，安全性 Cookie 會與其原先的值做比較。 如果這個值已變更，則可能發生緩衝區滿溢的情況，而且會停止處理序並顯示錯誤狀況。 停止處理序可防止執行可能惡意的程式碼。 有關詳細資訊，請參閱[-GS（緩衝區安全檢查）。](/cpp/build/reference/gs-buffer-security-check)  
  
 WPF 使用 /GS 標誌編譯，以便為 WPF 應用程式添加另一層防禦。  
  
### <a name="windows-vista"></a>Windows Vista  
Windows Vista 上的 WPF 使用者將受益于作業系統的其他安全增強功能，包括"最低許可權使用者訪問"、代碼完整性檢查和許可權隔離。  
  
#### <a name="user-account-control-uac"></a>使用者帳戶控制 (UAC)  
 如今，Windows 使用者傾向于使用管理員許可權運行，因為許多應用程式需要安裝或執行，或者兩者兼而有之。 其中一個例子是，使用者必須能夠將預設應用程式設定寫入至登錄。  
  
 以系統管理員權限執行，實際上表示應用程式會從具有系統管理員權限的處理序執行。 這樣做會有安全性風險，那就是劫持以系統管理員權限執行之處理序的任何惡意程式碼，都會自動繼承這些權限，包括重要系統資源的存取權。  
  
 防範這個安全性威脅的方法之一，就是以最少的必要權限執行應用程式。 這稱為最小特權原則，是 Windows 作業系統的核心功能。 此功能稱為使用者帳戶控制 （UAC），Windows UAC 以兩種關鍵方式使用：  
  
- 讓大多數的應用程式預設以 UAC 權限執行，即使使用者是系統管理員也一樣。只有需要系統管理員權限的應用程式才會以系統管理員權限執行。 若要以系統管理員權限執行，應用程式必須在其應用程式資訊清單中明確標記，或明確標記為安全性原則中的項目。  
  
- 提供像是虛擬化的相容性解決方案。 例如，許多應用程式會嘗試寫入限制位置，例如 C:\Program Files。 如果應用程式是以 UAC 執行，則會建立依使用者而定的替代位置，應用程式不需要有系統管理員權限就能寫入至這個位置。 如果應用程式是以 UAC 執行，則 UAC 會將 C:\Program Files 虛擬化，讓以為寫入至這個位置的應用程式，實際上是寫入至依使用者而定的替代位置。 這種相容性轉換工作可讓作業系統執行更多應用程式 (之前在 UAC 中執行時，並無法執行這麼多應用程式)。  
  
#### <a name="code-integrity-checks"></a>程式碼完整性檢查  
 Windows Vista 集成了更深入的代碼完整性檢查，以説明防止惡意程式碼在載入/運行時注入到系統檔或內核中。 這已經超過系統檔案保護範圍。  

### <a name="limited-rights-process-for-browser-hosted-applications"></a>瀏覽器裝載之應用程式的有限權限處理序  
 瀏覽器託管的 WPF 應用程式在 Internet 區域沙箱中執行。 WPF 與 Microsoft IExplorer 的集成提供了額外的支援，擴展了此保護。  
  
 由於 XAML 瀏覽器應用程式 （XBAPs） 通常由 Internet 區域許可權集進行沙箱處理，因此從相容性角度刪除這些特權不會損害 XAML 瀏覽器應用程式 （XBAPs）。 反而可以建立多一層的深層防禦。即使沙箱化的應用程式能夠攻擊其他層級並劫持處理序，處理序仍然只會有有限的權限。  
  
 請參閱[使用最低許可權的使用者帳戶](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29)。  
  
## <a name="common-language-runtime-security"></a>Common Language Runtime 安全性  
 通用語言運行時 （CLR） 提供了許多關鍵安全優勢，包括驗證和驗證、代碼訪問安全 （CAS） 和安全關鍵方法。  

### <a name="validation-and-verification"></a>驗證 (Validation 和 Verification)  
 為了提供程式集隔離和完整性，CLR 使用驗證過程。 CLR 驗證通過驗證程式集的可移植可執行 （PE） 檔案格式來驗證在程式集外部點的位址，從而隔離程式集。 CLR 驗證還驗證嵌入在程式集中的中繼資料的完整性。  
  
 為了確保型別安全，有助於防止常見的安全問題（例如緩衝區溢位），並通過子進程隔離啟用沙箱，CLR 安全部門使用驗證概念。  
  
 Managed 應用程式會編譯成 Microsoft 中繼語言 (MSIL)。 執行 Managed 應用程式中的方法時，應用程式的 MSIL 會透過 Just-In-Time (JIT) 編譯被編譯成機器碼。 JIT 編譯包含驗證程序，這個程序會套用許多安全和穩定性規則，以確保程式碼不會：  
  
- 違反類型合約  
  
- 引入緩衝區滿溢  
  
- 大量存取記憶體  
  
 不符合驗證規則的 Managed 程式碼除非受到信任，否則無法執行。  
  
 可驗證代碼的優點是 WPF 在 .NET 框架上構建的一個關鍵原因。 只要是使用可驗證程式碼的地方，潛在弱點遭受攻擊的可能性都會大幅降低。  
  
### <a name="code-access-security"></a>程式碼存取安全性  
 用戶端電腦公開了可供 Managed 應用程式存取的各種資源，包括檔案系統、登錄、列印服務、使用者介面、反映和環境變數。 在託管應用程式可以訪問用戶端電腦上的任何資源之前，它必須具有 .NET Framework 許可權才能執行此操作。 CAS 中的許可權是 中的<xref:System.Security.CodeAccessPermission>子類。CAS 為託管應用程式可以訪問的每個資源實現一個子類。  
  
 託管應用程式開始執行時授予的一組許可權稱為許可權集，由應用程式提供的證據確定。 對於 WPF 應用程式，提供的證據是啟動應用程式的位置或區域。 CAS 標識以下區域：  
  
- **我的電腦**。 從用戶端電腦啟動的應用程式 (完全信任)。  
  
- **近端內部網路**。 從內部網路啟動的應用程式 (部分受信任)。  
  
- **互聯網**. 從網際網路啟動的應用程式 (最不受信任)。  
  
- **信任的網站**。 使用者指定要信任的應用程式 (最不受信任)。  
  
- **限制的網站**。 使用者指定不要信任的應用程式 (未受信任)。  
  
 對於每個區域，CAS 提供了一個預定義的許可權集，其中包含與每個區域關聯的信任層級相匹配的許可權。 其中包括：  
  
- **FullTrust**。 對於從 **"我的電腦"** 區域啟動的應用程式。 會授與所有可能的權限。  
  
- **本地內聯網**。 適用于從**本地 Intranet**區域啟動的應用程式。 會授與權限的子集，以提供對用戶端電腦資源的中度存取權，包括隔離儲存區、無限制的 UI 存取權、無限制的檔案對話方塊、有限的反映、對環境變數的有限存取權。 不會提供重要資源 (例如登錄) 的權限。  
  
- **互聯網**. 適用于從**Internet**或**受信任的網站**區域啟動的應用程式。 會授與權限的子集，以提供對用戶端電腦資源的有限存取權，包括隔離儲存區、限檔案開啟，以及有限的 UI。 從本質上講，此許可權集將應用程式與用戶端電腦隔離。  
  
 CAS 不會授予來自**不受信任的網站**區域的應用程式。 因此，這些應用程式沒有預先定義的權限集合。  
  
 下圖說明瞭區域、許可權集、許可權和資源之間的關係：  
  
 ![顯示 CAS 許可權集的圖表。](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 Internet 區域安全沙箱的限制同樣適用于 XBAP 從系統庫中導入的任何代碼，包括 WPF。 這可確保鎖定代碼的每個位，甚至 WPF。 遺憾的是，為了能夠執行，XBAP 需要執行比 Internet 區域安全沙箱啟用的許可權更多的功能。  
  
 請考慮包含以下頁面的 XBAP 應用程式：  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 要執行此 XBAP，基礎 WPF 代碼必須執行比調用 XBAP 可用的功能更多的功能，包括：  
  
- 創建用於渲染的視窗控制碼 （HWND）  
  
- 分派訊息  
  
- 載入新細明體字型  
  
 從安全性觀點來看，允許沙箱化應用程式直接存取上述任何作業將會引發十分嚴重的後果。  
  
 幸運的是，WPF 允許這些操作代表沙箱應用程式以較高的權限執行，從而滿足這種情況。 雖然所有 WPF 操作都針對 XBAP 應用程式域的應用程式域的有限 Internet 區域安全許可權進行檢查，但 WPF（與其他系統庫一樣）被授予包含所有可能許可權的許可權集。
  
 這要求 WPF 接收較高的權限，同時防止這些特權受主機應用程式域的 Internet 區域許可權集控制。  
  
 WPF 使用許可權的**Assert**方法來這樣做。 下列程式碼會顯示這個過程。  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 **斷言**基本上可以防止 WPF 所需的無限許可權受到 XBAP 的 Internet 區域許可權的限制。  
  
 從平臺的角度來看，WPF 負責正確使用**Assert;** 對**Assert**的不正確使用可能會使惡意程式碼提升特權。 因此，重要的是，只有在需要時調用**Assert，** 並確保沙箱限制保持不變。 例如，沙箱化程式碼不可以開啟隨機檔案，但可以使用字型。 WPF 使沙箱應用程式能夠使用字體功能，通過調用**Assert**， 並使 WPF 能夠讀取已知代表沙箱應用程式包含這些字體的檔。  
  
### <a name="clickonce-deployment"></a>ClickOnce 部署  
 ClickOnce 是一種全面的部署技術，包含在 .NET 框架中，並與 Visual Studio 集成（有關詳細資訊，請參閱[ClickOnce 安全和部署](/visualstudio/deployment/clickonce-security-and-deployment)）。 可以使用 ClickOnce 部署獨立 WPF 應用程式，而瀏覽器託管的應用程式必須使用 ClickOnce 部署。  
  
 使用 ClickOnce 部署的應用程式在代碼訪問安全性 （CAS） 上獲得了額外的安全層;實質上，ClickOnce部署的應用程式請求他們需要的許可權。 只有在所要求的權限不超過應用程式部署來源區域的權限集合時，才會將這些權限授與應用程式。 通過將許可權集減少到僅需要的許可權集（即使的許可權小於啟動區域的許可權集提供的許可權），應用程式有權訪問的資源數量將減少到最低限度。 因此，如果應用程式遭到劫持，用戶端電腦遭到破壞的可能性將會降低。  
  
### <a name="security-critical-methodology"></a>安全性關鍵方法  
 使用許可權為 XBAP 應用程式啟用 Internet 區域沙箱的 WPF 代碼必須保持到最高程度的安全審核和控制。 為了方便此要求，.NET Framework 為管理提升特權的代碼提供了新的支援。 具體而言，CLR 使您能夠標識提升特權的代碼，並將其標記為<xref:System.Security.SecurityCriticalAttribute>。使用此方法，任何未<xref:System.Security.SecurityCriticalAttribute>標記的代碼都變得*透明*。 相反地，未標記為 <xref:System.Security.SecurityCriticalAttribute> 的 Managed 程式碼將無法提高權限。  
  
 安全關鍵方法允許組織 WPF 代碼，將權限提高到*安全關鍵型內核*，其餘部分是透明的。 隔離安全關鍵代碼使 WPF 工程團隊能夠將額外的安全分析和原始程式碼控制重點放在標準安全實踐之外的安全關鍵內核上（請參閱[WPF 安全性原則 - 安全工程](wpf-security-strategy-security-engineering.md)）。  
  
 請注意，.NET Framework 允許受信任的代碼通過允許開發人員編寫標記為<xref:System.Security.AllowPartiallyTrustedCallersAttribute>（APTCA） 並部署到使用者的全域組件快取 （GAC） 的託管程式集來擴展 XBAP Internet 區域沙箱。 在組件上標記 APTCA 是一項極為敏感的安全性作業，因為這可讓任何程式碼 (包括來自網際網路的惡意程式碼) 呼叫該組件。 執行這項操作時請謹慎為之，一定要採取最佳做法，而且使用者必須選擇信任該軟體才能安裝軟體。  
  
## <a name="microsoft-internet-explorer-security"></a>Microsoft Internet Explorer 安全性  
 除了減少安全問題和簡化安全配置外，Microsoft IEE 6 （SP2） 還包含幾個安全改進功能，這些功能增強了 XAML 瀏覽器應用程式 （XBAPs） 使用者的安全性。 這些功能的主要目的是要讓使用者更能掌控自己的瀏覽體驗。  
  
 在 IE6 SP2 之前，使用者可能受以下任何情況的約束：  
  
- 隨機跳出的快顯視窗。  
  
- 令人困惑的指令碼重新導向。  
  
- 某些網站上的大量安全性對話方塊。  
  
 在某些情況下，不可信的網站會嘗試欺騙安裝[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]或重複顯示 Microsoft ActiveX 安裝對話方塊來欺騙使用者，即使使用者可能已取消該對話方塊。 透過這些手法，許多使用者可能信以為真，做出錯誤決定，因而安裝了間諜軟體應用程式。  
  
 IE6 SP2 包括幾個功能來緩解這些類型的問題，這些功能圍繞使用者啟動的概念展開。 IE6 SP2 檢測使用者在操作之前按一下連結或頁面元素（稱為*使用者啟動*）時，它對待它的方式與頁面上的腳本觸發類似操作時不同。 例如，IE6 SP2 集成了一個**快顯視窗阻止程式**，用於檢測使用者在創建快顯視窗的頁面之前按一下按鈕時。 這使得 IE6 SP2 能夠允許大多數無害的快顯視窗，同時防止使用者既不要求也不想要的快顯視窗。 阻止的快顯視窗被捕獲到新的**資訊列**下，它允許使用者手動覆蓋該塊並查看快顯視窗。  
  
 相同的使用者啟動邏輯也適用于**打開**/**保存**安全提示。 ActiveX 安裝對話方塊始終受困在資訊列下，除非它們表示從以前安裝的控制項升級。 這些措施一起為使用者提供了更安全、更受控制的使用者經驗，因為使用者將可擺脫陌生網站為了讓使用者安裝不必要或惡意的軟體，而一再進行的騷擾。  
  
 這些功能還保護使用 IE6 SP2 流覽到允許他們下載和安裝 WPF 應用程式的網站的客戶。 特別是，這是因為 IE6 SP2 提供了更好的使用者體驗，減少了使用者安裝惡意或狡猾應用程式的機會，而不管使用何種技術來構建它，包括 WPF。 WPF 通過使用 ClickOnce 來簡化這些保護，以方便通過互聯網下載其應用程式。 由於 XAML 瀏覽器應用程式 （XBAPs） 在 Internet 區域安全沙箱中執行，因此可以無縫啟動它們。 另一方面，獨立 WPF 應用程式需要完全信任才能執行。 對於這些應用程式，ClickOnce 將在啟動過程中顯示一個安全對話方塊，以通知應用程式的其他安全要求。 不過，這必須由使用者啟始、同時受到使用者啟始的邏輯控制，並且可以取消。  
  
 Internet Explorer 7 整合並擴展了 IE6 SP2 的安全功能，作為持續致力於安全性的一部分。  
  
## <a name="see-also"></a>另請參閱

- [代碼訪問安全性](../misc/code-access-security.md)
- [安全性](security-wpf.md)
- [WPF 部分信任安全性](wpf-partial-trust-security.md)
- [WPF 安全性策略 – 安全性工程](wpf-security-strategy-security-engineering.md)
