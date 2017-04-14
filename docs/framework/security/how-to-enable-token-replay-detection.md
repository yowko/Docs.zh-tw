---
title: "HOW TO：啟用語彙基元重新執行偵測 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# HOW TO：啟用語彙基元重新執行偵測
## 適用於  
  
-   Microsoft® Windows®識別基礎 \(WIF\)  
  
-   ASP.NET® Web Form  
  
## 摘要  
 本 HOW TO 提供了可在使用 WIF 的 ASP.NET 應用程式的語彙基元重新執行偵測提供詳細的逐步程序。  它提供如何測試應用程式也提供指示驗證語彙基元重新執行偵測啟用。  本 HOW TO 沒有建立的安全性權杖服務 \(STS\) 詳細說明和使用隨附識別和存取工具的開發 STS。  為了進行測試開發 STS 不會執行實際的驗證與預定只取得。  您需要安裝識別和存取工具完成本 HOW TO。  您可以從下列位置下載: [識別和存取工具](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
## 內容  
  
-   目標  
  
-   概觀  
  
-   步驟摘要  
  
-   步驟 1 \-建立簡單的 ASP.NET Web Form 應用程式並啟用重新執行偵測  
  
-   步驟 2 \-測試方案。  
  
## 目標  
  
-   建立使用 WIF 和開發由識別的 STS 的簡單 ASP.NET 應用程式和存取工具  
  
-   啟用語彙基元重新執行偵測並驗證其運作。  
  
## 概觀  
 重新執行攻擊時發生，當用戶端嘗試驗證加入與用戶端已使用的 STS 語彙基元時的一個相依的一方。  若要避免這種攻擊， WIF 包含重新執行偵測快取先前使用的 STS 語彙基元。  啟用時，重新執行偵測檢查連入要求的語彙基元並確認是否已經使用了這個語彙基元。  如果已使用語彙基元，要求遭拒，並 <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> 擲回例外狀況。  
  
 下列步驟示範組態變更要求啟用重新執行偵測。  
  
## 步驟摘要  
  
-   步驟 1 \-建立簡單的 ASP.NET Web Form 應用程式並啟用重新執行偵測  
  
-   步驟 2 \-測試方案。  
  
## 步驟 1 \-建立簡單的 ASP.NET Web Form 應用程式並啟用重新執行偵測  
 在這個步驟中，您將建立新的 ASP.NET Web Form 應用程式並修改 *Web.config 檔案內* 啟用重新執行偵測。  
  
#### 建立簡單的 ASP.NET 應用程式  
  
1.  啟動 Visual Studio 並按一下 **檔案**、 **新增**然後 **專案**。  
  
2.  在 **新增專案** 視窗，請按一下 **ASP.NET Web Form 應用程式**。  
  
3.  在 **名稱**，請輸入並按下 `TestApp`**確定**。  
  
4.  以滑鼠右鍵按一下 **機碼** 專案在 **方案總管**下的，然後選取 **識別和存取**。  
  
5.  **識別和存取** 視窗隨即出現。  在 **提供者**下，選取的 **測試您的變更與本機開發 STS 的應用程式**，然後按一下 **套用**。  
  
6.  將下列項目加入至 **\<tokenReplayDetection\>** **\<system.identityModel\>** 和 **\<identityConfiguration\>** 項目後的 *Web.config 組態檔* ，如下範例所示:  
  
    ```  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled=”true”/>  
    ```  
  
## 步驟 2 \-測試方案。  
 在這個步驟中，您將測試 WIF 啟用 ASP.NET 應用程式以確認不再會偵測啟用。  
  
#### 測試您的變更重新執行偵測的 WIF 啟用 ASP.NET 應用程式  
  
1.  方案 **F5** 向上鍵來執行。  您應該會看到 ASP.NET 預設首頁和自動驗證的使用者名稱 *特里*，這是預設的使用者是由開發 STS 傳回。  
  
2.  按瀏覽器的 **背景** 按鈕。  您應該會看到具有下列描述的 **在「\/」的伺服器錯誤應用程式** 網頁: *ID1062:重新執行時偵測到為:語彙基元:* System.IdentityModel.Tokens.SamlSecurityToken，後面接著 *AssertionId*和*發行者*。  
  
     您會看到這個錯誤頁面，因為型別的 <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> 擲回例外狀況，在偵測到語彙基元重新執行。  這個錯誤的原因，是您嘗試重新傳送初始 POST 要求，以及第一次出現的語彙基元。  **背景** 按鈕不會使後續要求的行為加入至伺服器。