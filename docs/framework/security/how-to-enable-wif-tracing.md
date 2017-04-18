---
title: "如何：啟用 WIF 追蹤 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
caps.latest.revision: 3
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 3
---
# 如何：啟用 WIF 追蹤
## 適用於  
  
-   Microsoft® Windows® Windows Identity Foundation \(WIF\)  
  
-   ASP.NET® Web Form  
  
## 摘要  
 這個 HOW TO 為啟用 ASP.NET 應用程式的 WIF 追蹤提供詳細的逐步程序。  它也提供測試應用程式的指示驗證追蹤接聽項和記錄正常運作。  這個 HOW TO 沒有建立的 Security Token Service \(STS\) 詳細指示和會使用識別和存取工具的開發 STS。  為了進行測試開發 STS 不會執行實際的驗證和預期得只。  您必須安裝識別和存取工具完成本 HOW TO。  您可以從下列位置下載: [識別和存取工具](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
> [!IMPORTANT]
>  啟用被動應用程式的，也就是說，使用 WS\-同盟通訊協定的應用程式 WIF 追蹤，可能會公開應用程式在移除 Service \(DoS\) 攻擊或在資訊洩露處於惡意的一方。  這包括被動 RPs 和被動 STSes。  因此，我們建議您不要啟用被動 RPs 的 WIF 在實際執行的追蹤或 STSes。  
  
## 內容  
  
-   目標  
  
-   概觀  
  
-   步驟摘要  
  
-   步驟 1 \- 建立簡單的 ASP.NET Web Form 應用程式並啟用追蹤。  
  
-   步驟 2 \- 測試方案  
  
## 目標  
  
-   建立使用 WIF 和開發從識別的 STS 的簡單 ASP.NET 應用程式和存取工具  
  
-   啟用追蹤並驗證其運作。  
  
## 概觀  
 追蹤能夠讓您偵錯和疑難排解問題的許多型別與 WIF 的，包含語彙基元、Cookie、宣告，通訊協定訊息等等。  WIF 追蹤類似 WCF 追蹤;例如，您可以選擇追蹤詳細等級顯示所有從重要訊息到所有訊息。  WIF 追蹤可以產生在 **.xml** 檔案或在可檢視使用服務追蹤檢視器工具的 **.svclog** 檔案。  這個工具位於 Windows SDK 安裝路徑的 **bin** 目錄電腦，: **C:\\Program Files\\Microsoft SDKs \\ Windows \\ v7.1 \\ bin \\ SvcTraceViewer.exe**。  
  
## 步驟摘要  
  
-   步驟 1 \- 建立簡單的 ASP.NET Web Form 應用程式並啟用追蹤。  
  
-   步驟 2 \- 測試方案  
  
## 步驟 1 \- 建立簡單的 ASP.NET Web Form 應用程式並啟用追蹤。  
 在這個步驟中，您將建立新的 ASP.NET Web Form 應用程式並修改 *Web.config 檔* 中啟用追蹤。  
  
#### 建立簡單的 ASP.NET 應用程式  
  
1.  啟動 Visual Studio 並按一下 **檔案**、 **新增**和 **專案**。  
  
2.  在 **新的專案** 視窗中，按一下 **ASP.NET Web Form 應用程式**。  
  
3.  在 **名稱**中，輸入 `TestApp` 並按 **好**。  
  
4.  以滑鼠右鍵按一下 **機碼** 中的 **方案總管**，然後選取 **識別和存取**。  
  
5.  **識別和存取** 視窗隨即出現。  在 **提供者**下，選取 **測試與本機開發 STS 的應用程式**\]，然後按一下 **應用程式**。  
  
6.  會在名為 **記錄** 的新資料夾在 **C:** 磁碟的根目錄，如下所示: **C:\\logs**  
  
7.  將下列項目加入至 **\<system.diagnostics\>** 在右邊的 **\<\/configSections\>** 項目之後的 *Web.config 組態檔* ，如下所示:  
  
    ```  
    <configuration>  
        <configSections>  
        …  
        </configSections>  
        <system.diagnostics>  
            <sources>  
                <source name="System.IdentityModel" switchValue="Verbose">  
                    <listeners>  
                        <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="C:\logs\WIF.xml" />  
                    </listeners>  
                </source>  
            </sources>  
            <trace autoflush="true" />  
        </system.diagnostics>  
    ```  
  
    > [!NOTE]
    >  在記錄開始之前，在 **initializeData** 屬性中指定的目錄位置必須存在。  如果位置不存在，則不會建立。  
  
     上面的組態設定會啟用追蹤 WIF 的 **詳細資訊** 並儲存此結果記錄到 **C:\\logs\\WIF.xml** 檔案。  
  
## 步驟 2 \- 測試方案  
 在這個步驟中，您將測試 WIF 可讓 ASP.NET 應用程式來確認記錄檔中。  
  
#### 測試是成功追蹤的 WIF 可讓 ASP.NET 應用程式  
  
1.  方案由按 **F5** 鍵執行。  您應顯示預設 ASP.NET 主網頁和自動驗證的使用者名稱 *特里*，是預設使用者開發 STS 傳回。  
  
2.  關閉瀏覽器視窗並巡覽至 **C:\\logs** 資料夾。  使用文字編輯器中，開啟 **C:\\logs\\WIF.xml** 檔案。  
  
3.  檢查 **WIF.xml** 檔案並確認它是否包含以 **\<E2ETraceEvent\>**開頭的項目。  這些追蹤將會包含描述的 **\<TraceRecord\>** 項目中追蹤的活動，例如 **驗證 SecurityToken**。