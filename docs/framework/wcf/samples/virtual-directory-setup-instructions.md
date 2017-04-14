---
title: "虛擬目錄安裝指示 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
caps.latest.revision: 36
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 36
---
# 虛擬目錄安裝指示
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 範例的目的是共用名為 servicemodelsamples 的共用虛擬目錄，它會對應到 %SystemDrive%\\inetpub\\wwwroot\\servicemodelsamples 資料夾。  
  
> [!NOTE]
>  %SystemDrive% 通常是 C: 或 D:，這視安裝 Internet Information Services \(IIS\) 的磁碟機位置而定。  
  
 您可以執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)中的 Setupvroot.bat 和 Cleanupvroot.bat 檔案，以建立虛擬目錄。如果您偏好手動建立虛擬目錄，請使用下列程序。  
  
## 程序  
  
#### 在 IIS 7.0 或 7.5 中建立虛擬目錄  
  
1.  從 \[**開始**\] 功能表中，按一下 \[**執行**\]，再輸入 **inetmgr**，以開啟網際網路資訊服務 \(IIS\) MMC 嵌入式管理單元。  
  
2.  在左窗格中，展開電腦名稱的節點，再展開 \[**網站**\] 節點。  
  
3.  以滑鼠右鍵按一下 \[**預設的網站**\]，然後選取 \[**新增應用程式**\] 以開啟 \[**新增應用程式**\] 視窗。  
  
4.  在視窗中，輸入 `servicemodelsamples` 做為您所建立虛擬目錄的別名。  
  
5.  建立下列目錄：%SystemDrive%\\inetpub\\wwwroot\\servicemodelsamples  
  
6.  設定到 %SystemDrive%\\inetpub\\wwwroot\\servicemodelsamples 的實體路徑。建立時，大部分的 WCF 範例會將服務可執行檔複製到這個位置。  
  
7.  按一下 \[**確定**\]。隨即為 WCF 範例建立 Web 應用程式。  
  
    > [!NOTE]
    >  這個工作只需執行一次，因為所有的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例都使用相同的 servicemodelsamples Web 應用程式。  
  
    > [!NOTE]
    >  就此文件的用途而言，`virtual directory`一詞是 `Web application`的同義詞。  
  
     除了建立虛擬目錄外，您也必須設定其屬性，以啟用要執行的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。如需詳細資訊，請參閱下方。  
  
#### 在 IIS 5.1 或 6.0 中建立虛擬目錄  
  
1.  開啟命令提示視窗，並輸入 `start inetmgr`，以開啟網際網路資訊服務 \(IIS\) MMC 嵌入式管理單元。  
  
2.  在左窗格中，展開電腦名稱的節點，再展開 \[**網站**\] 節點。  
  
3.  以滑鼠右鍵按一下 \[**預設的網站**\]，然後依序選取 \[新增\]、\[**虛擬目錄**\] 以開啟 \[虛擬目錄建立精靈\]。  
  
4.  在精靈中，輸入 `servicemodelsamples` 做為您所建立虛擬目錄的別名。  
  
5.  設定到 %SystemDrive%\\inetpub\\wwwroot\\servicemodelsamples 的路徑。在建置時，大部分的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例會將服務可執行檔複製到這個位置。  
  
6.  接著，請按 \[**下一步**\]。  
  
7.  預設會選取下列核取方塊：  
  
    -   **讀取**  
  
    -   **執行指令碼 \(如 ASP\)**  
  
8.  按 \[**下一步**\]，然後按一下 \[**完成**\] 完成精靈。  
  
    > [!NOTE]
    >  這個工作只需執行一次，因為所有的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例都使用相同的 servicemodelsamples 虛擬目錄。  
  
#### 在 IIS 7.0 或 7.5 中設定額外的虛擬目錄屬性  
  
1.  按一下 servicemodelsamples 節點。視窗的底部會有兩個檢視。如果尚未選取 \[**功能檢視**\]，請予以選取。  
  
2.  連按兩下 \[**瀏覽目錄**\] 項目。  
  
3.  在 \[執行\] 窗格中，按一下 \[**啟用**\] 選項。這可讓您使用 Internet Explorer 存取目錄的目錄；如此將有助於偵錯服務。  
  
 最後，您必須設定 servicemodelsamples 資料夾的安全性屬性，讓其他使用者能夠存取此資料夾。如需詳細資訊，請參閱下方。  
  
#### 若要在 IIS 5.1 或 6.0 中設定額外的虛擬目錄屬性  
  
1.  以滑鼠右鍵按一下 servicemodelsamples 節點，然後按一下 \[**屬性**\]。  
  
2.  預設會選取下列核取方塊：  
  
    -   **讀取**  
  
    -   **記錄查閱**  
  
    -   **編製這個資源的索引**  
  
3.  選取 \[**瀏覽目錄**\] 核取方塊。這可讓您使用 Internet Explorer 存取目錄的目錄；如此將有助於偵錯服務。  
  
#### 設定 IIS 7.0 或 7.5 中資料夾的安全性屬性  
  
1.  巡覽至 %SystemDrive%\\inetpub\\wwwroot\\servicemodelsamples。  
  
2.  以滑鼠右鍵按一下 servicemodelsamples 資料夾，然後按一下 \[**共用**\] 或 \[**共用對象**\]。  
  
3.  按一下 \[**新增**\] 按鈕左邊的向下箭號。  
  
4.  選取 \[**尋找**\] 項目。\[**選取使用者或群組**\] 視窗隨即開啟。  
  
5.  按一下 \[**進階**\]。  
  
6.  按一下 \[**位置**\]。\[**位置**\] 視窗隨即開啟。  
  
7.  選取使用的電腦項目。請務必選取本機電腦，而非列出的任何網域或網路項目。選取電腦之後，請按一下 \[**確定**\]。  
  
8.  按一下 \[**立即尋找**\]。這會將與本機電腦相關聯的物件填入到搜尋結果中。  
  
9. 在 \[**名稱 \(RDN\)**\] 欄中尋找 \[**IIS\_IUSRS**\] 項目。選取該項目並按一下 \[**確定**\]，以關閉搜尋結果視窗。  
  
10. 按一下 \[**確定**\]，以關閉 \[**選取使用者或群組**\] 視窗。  
  
11. 按一下 \[**共用**\] 來保留變更。  
  
12. 在完成能夠啟用共用的變更後，按一下 \[**完成**\] 關閉 \[**檔案共用**\] 視窗。  
  
#### 設定 IIS 5.1 或 6.0 中資料夾的安全性屬性  
  
1.  巡覽至 %SystemDrive%\\inetpub\\wwwroot\\servicemodelsamples。  
  
2.  以滑鼠右鍵按一下 \[**servicemodelsamples**\] 資料夾，然後按一下 \[**共用和安全性**\]。  
  
3.  按一下 \[**安全性**\] 索引標籤。  
  
4.  如果您使用的是 IIS 6.0，請在 \[**群組或使用者名稱**\] 方塊中，檢查是否列出 \[**Internet Guest 帳戶**\]。  
  
     如果未列出：  
  
    1.  按一下 \[**開始**\]，然後按一下 \[**控制台**\]。  
  
    2.  如果您沒看到 \[**使用者帳戶**\] 圖示，則按一下 \[**切換到類別目錄檢視**\]。  
  
    3.  按一下 \[**使用者帳戶**\] 圖示。  
  
    4.  在 \[或選取 \[控制台\] 圖示\] 下，按一下 \[**使用者帳戶**\]。  
  
    5.  在 \[**使用者帳戶**\] 對話方塊中，按一下 \[**進階**\] 索引標籤。  
  
    6.  按一下 \[**進階**\]。  
  
    7.  在 \[**本機使用者和群組**\] 對話方塊中，按一下以展開 \[**使用者**\] 資料夾。  
  
    8.  在右窗格中，連按兩下 \[**Internet Guest 帳戶**\]。  
  
    9. 在 \[**屬性**\] 對話方塊中，複製 Internet Guest 帳戶的名稱。根據預設，該名稱開頭為 "USR\_"，後面會加上電腦的名稱。  
  
    10. 關閉 \[**屬性**\] 對話方塊。  
  
    11. 關閉 \[**本機使用者或群組**\] 對話方塊。  
  
    12. 關閉 \[**使用者帳戶**\] 對話方塊。  
  
    13. 關閉其他 \[**使用者帳戶**\] 對話方塊。  
  
    14. 在 \[**servicemodelsamples 屬性**\] 對話方塊中的 \[**安全性**\] 索引標籤上，按一下 \[**新增**\]。  
  
    15. 輸入電腦名稱，後面再加上反斜線，然後貼上網際網路使用者帳戶的名稱，例如 myMachineName\\%InternetGuestAccountName%  
  
    16. 按一下 \[**檢查名稱**\] 驗證新增的內容。如果有效，該名稱會是全部大寫字母並加上底線。  
  
5.  對於 IIS 6.0，亦請檢查列於 \[**群組或使用者名稱**\] 方塊中的 NETWORK SERVICE。  
  
     如果未列示 NETWORK SERVICE：  
  
    1.  按一下 \[**加入**\]。  
  
    2.  在 \[**選取使用者或群組**\] 對話方塊中，輸入電腦名稱，然後再加上反斜線。  
  
    3.  在反斜線後面輸入服務 \(沒有空格\)。  
  
    4.  按一下 \[**檢查名稱**\]。  
  
    5.  如果找到多個名稱，請選取 \[**NETWORK SERVICE**\]，再按一下 \[**確定**\]。  
  
    6.  按一下 \[**確定**\]，以關閉 \[**選取使用者或群組**\] 對話方塊。  
  
6.  如果您是使用 Windows XP SP2 搭配 IIS 5.1，請確認 Internet Guest 帳戶和 ASPNET 都已列在 \[**群組或使用者名稱**\] 方塊中。  
  
     請注意，ASPNET 使用者可以是內建 \[**使用者**\] 安全性群組的成員。如果是的話，若 \[**使用者**\] 群組列於對話方塊中，則您不需要將它做為個別項目新增至允許的使用者清單。  
  
     檢查 ASPNET 是否為 \[**使用者**\] 安全性群組的一部分：  
  
    1.  在 \[**開始**\] 功能表上，按一下 \[**控制台**\]。  
  
    2.  按一下 \[**使用者帳戶**\] 圖示。  
  
    3.  在 \[**群組**\] 欄中，確認 \[**ASPNET**\] 的值為 "Users"。  
  
## 請參閱  
 [Internet Information Service 裝載指示](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)