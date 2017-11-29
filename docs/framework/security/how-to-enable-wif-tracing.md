---
title: "如何：啟用 WIF 追蹤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 516e065bc360538e7b62807a5492c0c6c9d16e69
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-wif-tracing"></a>如何：啟用 WIF 追蹤
## <a name="applies-to"></a>適用於  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web Forms  
  
## <a name="summary"></a>摘要  
 這個操作說明提供了在 ASP.NET 應用程式中啟用 WIF 追蹤的詳細逐步程序。 還提供了一些指示，說明如何測試應用程式以確認追蹤接聽項和記錄檔正常運作。 這篇使用方法文章並沒有提供建立 Security Token Service (STS) 的詳細指示，而是使用識別和存取工具隨附的「開發 STS」。 「開發 STS」並不會執行實際的驗證，而只是用於測試用途。 您必須安裝識別和存取工具才能完成這篇使用方法文章。 您可以從下列位置下載：[Identity and Access Tool](http://go.microsoft.com/fwlink/?LinkID=245849) (身分識別與存取工具)  
  
> [!IMPORTANT]
>  為被動應用程式 (也就是使用 WS-同盟通訊協定的應用程式) 啟用 WIF 追蹤，可能會使應用程式暴露於阻斷服務 (DoS) 攻擊或洩漏資訊給惡意方的風險下。 這同時包括被動 RP 和被動 STS。 基於這個理由，建議您不要在生產環境中為被動 RP 或 STS 啟用 WIF 追蹤。  
  
## <a name="contents"></a>內容  
  
-   目標  
  
-   概觀  
  
-   步驟摘要  
  
-   步驟 1 – 建立簡單的 ASP.NET Web Form 應用程式並啟用追蹤  
  
-   步驟 2 – 測試方案  
  
## <a name="objectives"></a>目標  
  
-   建立從身分識別與存取工具使用 WIF 和開發 STS 的簡單 ASP.NET 應用程式  
  
-   啟用追蹤，並確認它能夠正常運作  
  
## <a name="overview"></a>概觀  
 追蹤可讓您對 WIF 的許多類型問題進行偵錯和疑難排解，包括權杖、Cookie、宣告、通訊協定訊息等等。 WIF 追蹤類似於 WCF 追蹤；例如，您可以選擇追蹤的詳細資訊來顯示從重大訊息到所有訊息的一切項目。 WIF 追蹤是在 **.xml** 檔案或 **.svclog** 檔案中產生，而您可以使用服務追蹤檢視器工具來檢視這些檔案。 此工具位於電腦上 Windows SDK 安裝路徑的 **bin** 目錄中，例如：**C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**。  
  
## <a name="summary-of-steps"></a>步驟摘要  
  
-   步驟 1 – 建立簡單的 ASP.NET Web Form 應用程式並啟用追蹤  
  
-   步驟 2 – 測試方案  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a>步驟 1 – 建立簡單的 ASP.NET Web Form 應用程式並啟用追蹤  
 在此步驟中，您將建立新的 ASP.NET Web Form 應用程式，並修改 *Web.config* 檔案以啟用追蹤。  
  
#### <a name="to-create-a-simple-aspnet-application"></a>建立簡單的 ASP.NET 應用程式  
  
1.  啟動 Visual Studio，並依序按一下 [檔案]、[新增] 和 [專案]。  
  
2.  在 [新增專案] 視窗中，按一下 [ASP.NET Web Forms 應用程式]。  
  
3.  在 [名稱] 中，輸入 `TestApp`，然後按 [確定]。  
  
4.  以滑鼠右鍵按一下方案總管底下的 [TestApp] 專案，然後選取 [身分識別與存取]。  
  
5.  [身分識別與存取] 視窗隨即出現。 在 [提供者] 底下，選取 [使用本機開發 STS 測試應用程式]，然後按一下 [套用]。  
  
6.  在 **C:** 磁碟機的根目錄中建立名為 **logs** 的新資料夾，如下所示：**C:\logs**  
  
7.  將下列 **\<system.diagnostics>** 元素加入 *Web.config* 組態檔中緊接在 **\</configSections>** 結尾元素後面的位置，如下所示：  
  
    ```xml  
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
    >  **initializeData** 屬性中指定的目錄位置必須已存在，才能開始進行記錄。 如果位置不存在，就不會建立任何記錄檔。  
  
     上述組態設定會為 WIF 啟用 **Verbose** 追蹤，並將產生的記錄檔儲存到 **C:logsWIF.xml** 檔案。  
  
## <a name="step-2--test-your-solution"></a>步驟 2 – 測試方案  
 在此步驟中，您將測試啟用 WIF 的 ASP.NET 應用程式以確認記錄檔會被記錄。  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a>測試啟用 WIF 的 ASP.NET 應用程式以成功追蹤  
  
1.  按 **F5** 鍵執行方案。 您應該會看到預設的 ASP.NET 首頁，並且會以使用者名稱 *Terry* (這是開發 STS 傳回的預設使用者) 自動進行驗證。  
  
2.  關閉瀏覽器視窗，然後巡覽至 **C:\logs** 資料夾。 使用文字編輯器開啟 **C:\logs\WIF.xml** 檔案。  
  
3.  檢查 **WIF.xml** 檔案，並確認其中包含開頭為 **\<E2ETraceEvent>** 的項目。 這些追蹤將包含 **\<TraceRecord>** 元素以及所追蹤之活動的描述，例如**正在驗證 SecurityToken**。
