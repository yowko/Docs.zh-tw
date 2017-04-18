---
title: "應用程式啟動時間 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "應用程式啟動 [WPF]"
  - "效能 [WPF], 啟動時間"
  - "啟動顯示畫面 [WPF], 啟動時間"
  - "啟動時間 [WPF]"
  - "WPF, 啟動時間"
ms.assetid: f0ec58d8-626f-4d8a-9873-c20f95e08b96
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 應用程式啟動時間
啟動 WPF 應用程式所需的時間量差異很大。  本主題所說明的各種技巧，可用於降低 Windows Presentation Foundation \(WPF\) 應用程式在認知上和實際上的啟動時間。  
  
## 認識冷啟動和暖啟動  
 冷啟動的發生時機，是在系統重新開機後第一次啟動應用程式時，或者是在啟動、關閉應用程式後，隔一段時間才再次啟動時。  啟動應用程式時，如果必要的分頁 \(程式碼、靜態資料、登錄等等\) 並不在 Windows 記憶體管理員的待命清單中，就會發生分頁錯誤。  這時就需要磁碟存取來將分頁帶入記憶體中。  
  
 暖啟動的發生時機，是在大部分的 Common Language Runtime \(CLR\) 主要元件分頁已經載入到記憶體時，這樣可以節省大量的磁碟存取時間。  這就是 Managed 應用程式在第二次執行時，啟動得比較快的原因。  
  
## 實作啟動顯示畫面  
 在啟動應用程式和顯示第一個 UI 兩項作業之間出現無法避免的明顯時間延遲情況時，可以藉由使用「*啟動顯示畫面*」\(Splash Screen\) 來最佳化實際啟動時間。  這個方法幾乎可在使用者啟動應用程式後立即顯示影像，  並在應用程式準備好顯示第一個 UI 時淡出啟動顯示畫面。  在 [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] 中進行啟動時，您可以使用 <xref:System.Windows.SplashScreen> 類別實作啟動顯示畫面。  如需詳細資訊，請參閱 [在 WPF 應用程式中加入啟動顯示畫面](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)。  
  
 您也可以藉由使用原生 Win32 圖形實作自己的啟動顯示畫面。  請在呼叫 <xref:System.Windows.Application.Run%2A> 方法前顯示您的實作。  
  
## 分析啟始程式碼  
 判斷冷啟動緩慢的原因。  有可能是因為磁碟 I\/O，但不見得一定是這種情況。  通常，您應該盡可能減少使用外部資源的機會，例如網路、Web 服務或磁碟。  
  
 在測試之前，請確認沒有其他執行中的應用程式或服務正在使用 Managed 程式碼或 WPF 程式碼。  
  
 在重新開機後立即啟動您的 WPF 應用程式，並判斷應用程式需要多久時間顯示畫面。  如果應用程式的所有後續啟動 \(暖啟動\) 都快很多，則冷啟動的問題很可能是由 I\/O 造成的。  
  
 如果應用程式的冷啟動問題與 I\/O 無關，則可能是應用程式執行的某項初始化作業或計算作業過於冗長、要等待某個事件完成，或者是啟動時需要許多 JIT 編譯。  下列小節將進一步說明這些狀況的其中一部分。  
  
## 最佳化模組載入  
 使用 Process Explorer \(Procexp.exe\) 和 Tlist.exe 這類的工具，判斷應用程式會載入哪些模組。  命令 `Tlist <pid>` 會顯示處理序所載入的所有模組。  
  
 例如，如果沒有連接至 Web 而您看到有載入 System.Web.dll，則表示應用程式中有模組會參考這個組件。  請檢查以確定該參考是否有必要。  
  
 如果應用程式有多個模組，請合併到單一模組中。  這個方法需要較少的 CLR 組件載入負荷。  較少的組件也就代表 CLR 要維護的狀態較少。  
  
## 延後初始化作業  
 請考慮將初始化程式碼延後到呈現主應用程式視窗後再進行。  
  
 請注意，初始化作業可能會在類別建構函式內執行，如果初始化程式碼會參考其他類別，則可能造成串聯效應，並在其中執行許多的類別建構函式。  
  
## 避免應用程式組態  
 請考慮避免使用應用程式組態。  例如，如果應用程式有簡單的組態需求和嚴格的啟動時間目標，則登錄項目或簡單的 INI 檔或許是比較快的啟動替代方案。  
  
## 使用 GAC  
 如果組件不是安裝在全域組件快取 \(GAC\) 中，當電腦中具有該組件的原生映像時，強式名稱組件的雜湊驗證和 Ngen 映像驗證就會造成延遲。  安裝在 GAC 中的所有組件會略過強式名稱驗證。  如需詳細資訊，請參閱[Gacutil.exe \(全域組件快取工具\)](../../../../docs/framework/tools/gacutil-exe-gac-tool.md)。  
  
## 使用 Ngen.exe  
 請考慮在應用程式中使用原生映像產生器 \(Ngen.exe\)。  使用 Ngen.exe 表示將 CPU 耗用量交換為更多的磁碟存取，因為 Ngen.exe 產生的原生映像可能比 MSIL 映像來得大。  
  
 為了改善暖啟動的時間，您應該永遠在應用程式上使用 Ngen.exe，因為這樣會避免應用程式程式碼在 JIT 編譯上的 CPU 使用時間。  
  
 在有些冷啟動的案例中，使用 Ngen.exe 也很有幫助。  這是因為不一定要載入 JIT 編譯器 \(mscorjit.dll\)。  
  
 同時具有 Ngen 和 JIT 模組可能會帶來最糟的效果。  這是因為必須載入 mscorjit.dll，而當 JIT 編譯器處理程式碼時，必須在 JIT 編譯器讀取組件中繼資料時存取 Ngen 映像中的許多分頁。  
  
### Ngen 和 ClickOnce  
 您計劃部署應用程式的方式也可能造成載入時間的差異。  [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 應用程式部署並不支援 Ngen。  如果決定應用程式要使用 Ngen.exe，則必須使用其他的部署機制，例如 Windows Installer。  
  
 如需詳細資訊，請參閱[Ngen.exe \(原生映像產生器\)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)。  
  
### 重定基底和 DLL 位址衝突  
 如果使用 Ngen.exe，請注意可能會在記憶體中載入原生映像時發生重定基底 \(Rebase\)。  如果因為已經配置位址範圍讓 DLL 沒有在其慣用的基底位址載入的話，則 Windows 載入器會將其載入到其他位址，而這可能會是個非常耗時的作業。  
  
 您可以使用 Virtual Address Dump \(Vadump.exe\) 工具，檢查是否有模組的所有分頁都是屬於私用的。  如果是這種情況的話，模組可能已經重定基底到其他位址。  因而無法共用其分頁。  
  
 如需如何設定基底位址的詳細資訊，請參閱[Ngen.exe \(原生映像產生器\)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)。  
  
## 最佳化 Authenticode  
 在啟動時間會加入 Authenticode 驗證。  Authenticode 簽署的組件必須使用憑證授權單位 \(CA\) 進行驗證。  這項驗證可能會很耗時，因為它可能需要連接網路數次來下載目前的憑證撤銷清單。  它也要確認在受信任的根授權路徑上，是否有完整的有效憑證鏈結。  這樣就可能會在載入組件時轉化為幾秒鐘的延遲。  
  
 請考慮在用戶端電腦上安裝 CA 憑證，或是在可能的情況下避免使用 Authenticode。  如果您知道應用程式不需要發行者辨識項，則您就不需要耗費資源在簽章驗證上。  
  
 在 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] 中進行啟動時，有一個組態選項可以允許略過 Authenticode 驗證。  若要進行這項作業，將下列設定加入至 app.exe.config 檔案中：  
  
```  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>   
    </runtime>  
</configuration>  
```  
  
 如需詳細資訊，請參閱 [\<generatePublisherEvidence\> 項目](../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)。  
  
## 比較 Windows Vista 上的效能  
 Windows Vista 中的記憶體管理員具有稱為 SuperFetch 的技術。  SuperFetch 會隨著時間分析記憶體使用模式，以判斷特定使用者的最佳記憶體內容。  它會持續不斷地運作，隨時維護該內容。  
  
 這個方法與 Windows XP 中使用的預先擷取技術不同，後者會在沒有分析使用模式的情況下將資料預先載入至記憶體。  如果使用者常常在 Windows Vista 上執行該 WPF 應用程式，那麼一段時間過後，應用程式的冷啟動時間可能就會有所改善。  
  
## 有效使用 AppDomains  
 如果可能的話，將組件載入至定義域中性的程式碼區域，可以確保將原生映像 \(如果有的話\) 用於應用程式建立的所有 AppDomains 中。  
  
 為了達到最佳效能，可以藉由減少跨定義域呼叫來強制執行有效的跨定義域通訊。  在使用呼叫時，盡可能不要使用引數或是使用基本型別引數。  
  
## 使用 NeutralResourcesLanguage 屬性  
 使用 <xref:System.Resources.NeutralResourcesLanguageAttribute> 指定 <xref:System.Resources.ResourceManager> 為中性文化特性。  這個方法可以避免不成功的組件查閱。  
  
## 使用 BinaryFormatter 類別進行序列化  
 如果必須使用序列化，請使用 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 類別，而不要使用 <xref:System.Xml.Serialization.XmlSerializer> 類別。  The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 類別是在 mscorlib.dll 組件的基底類別庫 \(BCL\) 中實作的。  <xref:System.Xml.Serialization.XmlSerializer> 則是在 System.Xml.dll 組件中實作的，這可能是要額外載入的 DLL。  
  
 如果必須使用 <xref:System.Xml.Serialization.XmlSerializer> 類別，預先產生序列化組件可以達到較佳的效能。  
  
## 設定 ClickOnce 在啟動後檢查更新  
 如果應用程式使用 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)]，藉由將 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 設定在應用程式啟動後再向部署網站檢查是否有更新，即可以避免網路存取。  
  
 如果使用的是 XAML 瀏覽器應用程式 \(XBAP\) 模型，請記得，即使 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 快取中已經有 XBAP，[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 還是會向部署網站檢查是否有更新。  如需詳細資訊，請參閱 [ClickOnce 安全性和部署](../Topic/ClickOnce%20Security%20and%20Deployment.md)。  
  
## 設定 PresentationFontCache 服務自動啟動  
 重新開機後第一個執行的 WPF 應用程式是 PresentationFontCache 服務。  該服務會快取系統字型、改善字型存取，以及改善整體效能。  啟動這個服務時有不少負荷，所以在有些受控制的環境，請考慮將這個服務設定為在系統重新開機時自動啟動。  
  
## 以程式設計方式設定資料繫結  
 除了使用 XAML 以宣告方式設定主視窗的 <xref:System.Windows.FrameworkElement.DataContext%2A> 之外，請考慮以程式設計方式在 <xref:System.Windows.Application.OnActivated%2A> 方法中進行設定。  
  
## 請參閱  
 <xref:System.Windows.SplashScreen>   
 <xref:System.AppDomain>   
 <xref:System.Resources.NeutralResourcesLanguageAttribute>   
 <xref:System.Resources.ResourceManager>   
 [在 WPF 應用程式中加入啟動顯示畫面](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)   
 [Ngen.exe \(原生映像產生器\)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)   
 [\<generatePublisherEvidence\> 項目](../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)