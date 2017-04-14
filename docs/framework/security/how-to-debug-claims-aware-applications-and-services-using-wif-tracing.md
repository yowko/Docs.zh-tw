---
title: "HOW TO：使用 WIF 追蹤來偵錯宣告感知應用程式和服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# HOW TO：使用 WIF 追蹤來偵錯宣告感知應用程式和服務
## 適用於  
  
-   Microsoft® Windows® Identity Foundation \(WIF\)  
  
-   服務追蹤檢視器工具 \(SvcTraceViewer.exe\)  
  
-   疑難排解和偵錯 WIF 應用程式  
  
## 摘要  
 本使用說明針對如何設定 WIF 追蹤、收集追蹤記錄檔，以及如何使用追蹤檢視器工具來分析追蹤記錄檔，說明所需的步驟。  其針對 WIF 相關問題的疑難排解，提供所需之追蹤項目對動作的一般對應。  
  
## 內容  
  
-   目標  
  
-   步驟摘要  
  
-   步驟 1 – 使用 Web.config 組態檔來設定 WIF 追蹤  
  
-   步驟 2 – 使用追蹤檢視器工具來分析 WIF 追蹤檔案  
  
-   步驟 3 – 識別用來修正 WIF 相關問題的方案  
  
-   相關項目  
  
## 目標  
  
-   設定 WIF 追蹤。  
  
-   在追蹤檢視器工具中檢視追蹤記錄檔。  
  
-   在追蹤記錄檔中識別 WIF 的相關問題。  
  
-   將更正動作套用到在追蹤記錄中發現的 WIF 相關問題。  
  
## 步驟摘要  
  
-   步驟 1 – 使用 Web.config 組態檔來設定 WIF 追蹤  
  
-   步驟 2 – 使用追蹤檢視器工具來分析 WIF 追蹤檔案  
  
-   步驟 3 – 識別用來修正 WIF 相關問題的方案  
  
## 步驟 1 – 使用 Web.config 組態檔來設定 WIF 追蹤  
 在此步驟中，您要將變更加入 *Web.config* 檔案中的組態區段，讓 WIF 能夠追蹤它的事件，並將其儲存在追蹤記錄檔中。  
  
#### 使用 Web.config 組態檔來設定 WIF 追蹤  
  
1.  在 \[方案總管\] 中按兩下根 **Web.config** 或 **App.config** 組態檔，以在 Visual Studio 編輯器將其開啟。  如果您的方案沒有 **Web.config** 或 **App.config** 組態檔案，請在 \[方案總管\] 中，以滑鼠右鍵按一下該方案，並按一下 \[加入\]，然後按一下 \[新增項目...\]，以加入檔案。  在 \[新增項目\] 對話方塊中，從清單選取 \[應用程式組態檔\] \(若要使用 **App.config**\) 或 \[Web 組態檔\] \(若要使用 **Web.config**\)，然後按一下 \[確定\]。  
  
2.  將類似下列的組態項目加入組態檔，位於組態檔結尾的 **\<configuration\>** 節點中：  
  
    ```xml  
    <system.diagnostics>  
        <sources>  
            <source name="System.IdentityModel" switchValue="Verbose">  
                <listeners>  
                    <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="WIFTrace.e2e"/>  
                </listeners>  
            </source>  
        </sources>  
        <trace autoflush="true"/>  
    </system.diagnostics>  
    ```  
  
3.  上述組態會指示 WIF 產生詳細追蹤事件，並將其記錄在 *WIFTrace.e2e* 檔案中。  如需 **switchValue** 變數值的完整清單，請參閱下列主題中的「追蹤層級」表格：[設定追蹤](http://msdn.microsoft.com/library/ms733025.aspx)。  
  
## 步驟 2 – 使用追蹤檢視器工具來分析 WIF 追蹤檔案  
 在此步驟中，您要使用追蹤檢視器工具 \(SvcTraceViewer.exe\) 來分析 WIF 追蹤記錄檔。  
  
#### 使用追蹤檢視器工具 \(SvcTraceViewer.exe\) 來分析 WIF 追蹤記錄檔  
  
1.  追蹤檢視器工具 \(SvcTraceViewer.exe\) 隨附於 Windows SDK。  如果您還沒有安裝 Windows SDK，可以在這裡下載：[Windows SDK](http://www.microsoft.com/download/en/details.aspx?id=8279)。  
  
2.  執行追蹤檢視器工具 \(SvcTraceViewer.exe\)。  它通常會在安裝路徑的 **Bin** 資料夾中。  
  
3.  在功能表中選取 \[檔案\]、\[開啟...\] 選項，或使用 **Ctrl \+ O** 快速鍵，以開啟 WIF 追蹤記錄檔 \(例如 WIFTrace.e2e\)。  追蹤記錄檔會在追蹤檢視器工具中開啟。  
  
4.  檢閱 \[活動\] 索引標籤中的項目。  每個項目都應該會包含活動號碼、所記錄的追蹤數目、活動的持續時間，以及其開始和結束時間戳記。  
  
5.  按一下 \[活動\] 索引標籤。  您應該會在此工具的主要區域中，看到詳細的追蹤項目。  使用功能表上的 \[層級\] 下拉式清單，來篩選特定層級的追蹤，例如：**全部**、**警告**、**錯誤**、**資訊**等等。  
  
6.  按一下特定追蹤項目，以檢閱工具下方區域中的詳細資料。  您可以選擇對應的索引標籤，使用 \[格式化\] 和 \[XML\] 檢視來檢視詳細資料。  
  
## 步驟 3 – 識別用來修正 WIF 相關問題的方案  
 在此步驟中，您可以針對使用 WIF 追蹤記錄檔和追蹤檢視器工具來識別的 WIF 相關問題，找出方案。  本文將針對 WIF 相關例外狀況與可能的方案或疑難排解此問題所需的動作，提供一般對應。  
  
#### 識別用來修正 WIF 相關問題的方案  
  
1.  檢閱下面 WIF 例外狀況與更正問題所需動作的表格。  
  
||||  
|-|-|-|  
|**錯誤識別碼**|**錯誤訊息**|**修正錯誤所需的動作**|  
|ID4175|IssuerNameRegistry 無法辨識安全性權杖的簽發者。  若要接受來自這個簽發者的安全性權杖，請設定 IssuerNameRegistry，以傳回此簽發者的有效名稱。|造成此錯誤的原因，可能是您從 MMC 嵌入式管理單元複製憑證指模，並將其貼在 *Web.config* 檔案中。  具體而言，您可以在從憑證屬性視窗複製時，在文字字串中取得額外的不可列印字元。  這個額外的字元導致憑證指模比對失敗，您可以在這裡找到正確複製憑證指模的程序： [http:\/\/msdn.microsoft.com\/library\/ff359102.aspx](http://msdn.microsoft.com/library/ff359102.aspx)|  
  
## 相關項目  
  
-   [使用服務追蹤檢視器檢視相關追蹤並進行疑難排解](http://msdn.microsoft.com/library/aa751795.aspx)