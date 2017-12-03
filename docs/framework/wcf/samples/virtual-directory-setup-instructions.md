---
title: "虛擬目錄安裝指示"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72487c4a6720f80119beb837fbb3b5ea25ac3b93
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="virtual-directory-setup-instructions"></a>虛擬目錄安裝指示
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 範例的目的是共用名為 servicemodelsamples 的共用虛擬目錄，它會對應到 %SystemDrive%\inetpub\wwwroot\servicemodelsamples 資料夾。  
  
> [!NOTE]
>  %SystemDrive% 通常是 C: 或 D:，這視安裝 Internet Information Services (IIS) 的磁碟機位置而定。  
  
 您可以執行的 Setupvroot.bat 和 Cleanupvroot.bat 檔案[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)建立虛擬目錄。 如果您偏好手動建立虛擬目錄，請使用下列程序。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a>若要建立虛擬目錄在 IIS 7.0 或 7.5  
  
1.  從**啟動**功能表上，按一下 **執行**，然後輸入**inetmgr**以開啟 網際網路資訊服務 (IIS) MMC 嵌入式管理單元。  
  
2.  在左窗格中，展開電腦名稱的節點，然後展開**網站**節點。  
  
3.  以滑鼠右鍵按一下**Default Web Site**，然後選取**新增應用程式**開啟**新增應用程式視窗**。  
  
4.  在視窗中，輸入`servicemodelsamples`做為您建立的虛擬目錄的別名。  
  
5.  建立下列目錄：%SystemDrive%\inetpub\wwwroot\servicemodelsamples  
  
6.  設定到 %SystemDrive%\inetpub\wwwroot\servicemodelsamples 的實體路徑。  建立時，大部分的 WCF 範例會將服務可執行檔複製到這個位置。  
  
7.  按一下 [確定]。 隨即為 WCF 範例建立 Web 應用程式。  
  
    > [!NOTE]
    >  這個工作只需執行一次，因為所有的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例都使用相同的 servicemodelsamples Web 應用程式。  
  
    > [!NOTE]
    >  就此文件的用途而言，`virtual directory`一詞是 `Web application`的同義詞。  
  
     除了建立虛擬目錄外，您也必須設定其屬性，以啟用要執行的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。 如需詳細資訊，請參閱下方。  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a>在 IIS 5.1 或 6.0 中建立虛擬目錄  
  
1.  開啟命令提示字元視窗並輸入`start inetmgr`以開啟 網際網路資訊服務 (IIS) MMC 嵌入式管理單元。  
  
2.  在左窗格中，展開電腦名稱的節點，然後展開**網站**節點。  
  
3.  以滑鼠右鍵按一下**Default Web Site**選取**新的虛擬目錄**以開啟 虛擬目錄建立精靈。  
  
4.  在精靈中，輸入`servicemodelsamples`做為您建立的虛擬目錄的別名。  
  
5.  設定到 %SystemDrive%\inetpub\wwwroot\servicemodelsamples 的路徑。 在建置時，大部分的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例會將服務可執行檔複製到這個位置。  
  
6.  按 [ **下一步**]。  
  
7.  預設會選取下列核取方塊：  
  
    -   **讀取**  
  
    -   **執行指令碼 （例如 ASP)**  
  
8.  按一下**下一步**，然後按一下 **完成**以完成精靈。  
  
    > [!NOTE]
    >  這個工作只需執行一次，因為所有的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例都使用相同的 servicemodelsamples 虛擬目錄。  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a>若要設定其他的虛擬目錄內容，在 IIS 7.0 或 7.5  
  
1.  按一下 servicemodelsamples 節點。 視窗的底部會有兩個檢視。 選取**功能檢視**如果尚未選取它。  
  
2.  按兩下項目**目錄瀏覽**。  
  
3.  在 [動作] 窗格中，選取**啟用**選項。 這可讓您使用 Internet Explorer 存取目錄的目錄；如此將有助於偵錯服務。  
  
 最後，您必須設定 servicemodelsamples 資料夾的安全性屬性，讓其他使用者能夠存取此資料夾。 如需詳細資訊，請參閱下方。  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a>若要在 IIS 5.1 或 6.0 中設定額外的虛擬目錄屬性  
  
1.  以滑鼠右鍵按一下 servicemodelsamples 節點，然後按一下 **屬性**。  
  
2.  預設會選取下列核取方塊：  
  
    -   **讀取**  
  
    -   **記錄查閱**  
  
    -   **此資源編製索引**  
  
3.  選取**目錄瀏覽**核取方塊。 這可讓您使用 Internet Explorer 存取目錄的目錄；如此將有助於偵錯服務。  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a>若要在 IIS 7.0 或 7.5 中設定資料夾安全性屬性  
  
1.  巡覽至 %SystemDrive%\inetpub\wwwroot\servicemodelsamples。  
  
2.  以滑鼠右鍵按一下 servicemodelsamples 資料夾，然後按一下**共用**或**共用與**。  
  
3.  按一下左邊的向下箭號**新增** 按鈕。  
  
4.  選取**尋找**項目。 **選取使用者或群組**視窗隨即開啟。  
  
5.  按一下 [ **進階**]。  
  
6.  按一下**位置**。 **位置** 視窗隨即開啟。  
  
7.  選取使用的電腦項目。 請務必選取本機電腦，而非列出的任何網域或網路項目。 您已選取電腦之後，請按一下**確定**。  
  
8.  按一下**立即尋找**。 這會將與本機電腦相關聯的物件填入到搜尋結果中。  
  
9. 尋找**IIS_IUSRS**中的項目**名稱 (Rdn)**資料行。 選取該項目，然後按一下**確定**以關閉搜尋結果視窗。  
  
10. 按一下**確定**關閉**選取使用者或群組**視窗。  
  
11. 按一下**共用**保存變更。  
  
12. 若要啟用共用變更已完成之後，請按一下**完成**關閉**檔案共用**視窗。  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a>設定 IIS 5.1 或 6.0 中資料夾的安全性屬性  
  
1.  巡覽至 %SystemDrive%\inetpub\wwwroot\servicemodelsamples。  
  
2.  以滑鼠右鍵按一下**servicemodelsamples**資料夾，然後按一下**共用和安全性。**  
  
3.  按一下 [ **安全性** ] 索引標籤。  
  
4.  如果您使用 IIS 6.0 中**群組或使用者名稱**方塊中，檢查是否**Internet Guest 帳戶**列。  
  
     如果未列出：  
  
    1.  按一下**啟動**，然後按一下 **控制台**。  
  
    2.  如果您沒有看到**使用者帳戶**圖示，按一下 **切換至 類別檢視**。  
  
    3.  按一下**使用者帳戶**圖示。  
  
    4.  在 或選取 控制台 圖示，「 按一下**使用者帳戶**。  
  
    5.  在**使用者帳戶**對話方塊中，按一下 [**進階**] 索引標籤。  
  
    6.  按一下 [ **進階**]。  
  
    7.  在**本機使用者和群組**對話方塊中，按一下以展開**使用者**資料夾。  
  
    8.  在右窗格中，按兩下**Internet Guest 帳戶**。  
  
    9. 在**屬性**對話方塊中，複製名稱做為 Internet guest 帳戶。 根據預設，該名稱開頭為 "USR_"，後面會加上電腦的名稱。  
  
    10. 關閉 [內容]  對話方塊。  
  
    11. 關閉**本機使用者和群組** 對話方塊。  
  
    12. 關閉**使用者帳戶** 對話方塊。  
  
    13. 關閉其他**使用者帳戶** 對話方塊。  
  
    14. 在**servicemodelsamples 屬性**對話方塊**安全性**索引標籤上，按一下 **新增**。  
  
    15. 輸入一個反斜線，後面接著電腦名稱，然後貼上網際網路使用者帳戶，例如 myMachineName 名稱\\%internetguestaccountname%  
  
    16. 按一下**檢查名稱**驗證新增。 如果有效，該名稱會是全部大寫字母並加上底線。  
  
5.  IIS 6.0，也請確認網路服務列在**群組或使用者名稱**方塊。  
  
     如果未列示 NETWORK SERVICE：  
  
    1.  按一下 [加入] 。  
  
    2.  在**選取使用者或群組** 對話方塊中，輸入電腦的名稱以及反斜線。  
  
    3.  型別**服務**反斜線 （不含空格） 後。  
  
    4.  按一下**檢查名稱**。  
  
    5.  如果找到多個名稱，選取**NETWORK SERVICE**按一下**確定**。  
  
    6.  按一下**確定**關閉**選取使用者或群組** 對話方塊。  
  
6.  如果您使用 Windows XP SP2 搭配 IIS 5.1，請確認 Internet Guest 帳戶和 ASPNET 都列在**群組或使用者名稱**方塊。  
  
     請注意，ASPNET 使用者可能是內建成員**使用者**安全性群組。 若是如此，如果**使用者**群組列於對話方塊中，您不需要將它當做個別項目加入至允許的使用者清單。  
  
     若要檢查 ASPNET 是否屬於**使用者**安全性群組：  
  
    1.  在**啟動**功能表上，按一下 **控制台**。  
  
    2.  按一下**使用者帳戶**圖示。  
  
    3.  在**群組**資料行，請檢查值**ASPNET**是 「 使用者 」。  
  
## <a name="see-also"></a>另請參閱  
 [Internet Information Service 裝載指示](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
