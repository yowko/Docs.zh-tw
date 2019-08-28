---
title: 虛擬目錄安裝指示
ms.date: 03/30/2017
ms.assetid: 3c62cab5-81a4-48b6-ac8c-9ce33a85a157
ms.openlocfilehash: 6dccc5174e3fb9ab67023310d8c060d598a707c9
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038639"
---
# <a name="virtual-directory-setup-instructions"></a>虛擬目錄安裝指示
Windows Communication Foundation (WCF) 範例的目的是共用名稱為 servicemodelsamples 的通用虛擬目錄, 其對應至%SystemDrive%\inetpub\wwwroot\servicemodelsamples 資料夾。  
  
> [!NOTE]
> %SystemDrive% 通常是 C: 或 D:，這視安裝 Internet Information Services (IIS) 的磁碟機位置而定。  
  
 您可以從[Windows Communication Foundation 範例的一次性安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)執行 Setupvroot.bat 和 cleanupvroot.bat 檔案, 以建立虛擬目錄。 如果您偏好手動建立虛擬目錄，請使用下列程序。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-create-a-virtual-directory-in-iis-70-or-75"></a>若要在 IIS 7.0 或7.5 中建立虛擬目錄  
  
1. 在 [**開始**] 功能表中, 按一下 [**執行**], 然後輸入**inetmgr**以開啟 [Internet Information Services (IIS) mmc 嵌入式管理單元]。  
  
2. 在左窗格中, 展開具有電腦名稱稱的節點, 然後展開 [**網站**] 節點。  
  
3. 以滑鼠右鍵按一下 [**預設的網站**], 然後選取 [**新增應用程式**] 以開啟 [**新增應用程式] 視窗**。  
  
4. 在視窗中, 輸入`servicemodelsamples`做為您所建立虛擬目錄的別名。  
  
5. 建立下列目錄：%SystemDrive%\inetpub\wwwroot\servicemodelsamples  
  
6. 設定到 %SystemDrive%\inetpub\wwwroot\servicemodelsamples 的實體路徑。  建立時，大部分的 WCF 範例會將服務可執行檔複製到這個位置。  
  
7. 按一下 [確定]。 隨即為 WCF 範例建立 Web 應用程式。  
  
    > [!NOTE]
    > 這項工作只需執行一次, 因為所有 WCF 範例都使用相同的 servicemodelsamples Web 應用程式。  
  
    > [!NOTE]
    > 就此文件的用途而言，`virtual directory`一詞是 `Web application`的同義詞。  
  
     除了建立虛擬目錄以外, 您還必須設定其屬性, 讓 WCF 服務得以執行。 如需詳細資訊，請參閱下方。  
  
#### <a name="to-create-a-virtual-directory-in-iis-51-or-60"></a>在 IIS 5.1 或 6.0 中建立虛擬目錄  
  
1. 開啟 [命令提示字元] 視窗`start inetmgr` , 然後輸入以開啟 Internet Information Services (IIS) MMC 嵌入式管理單元。  
  
2. 在左窗格中, 展開具有電腦名稱稱的節點, 然後展開 [**網站**] 節點。  
  
3. 以滑鼠右鍵按一下 [**預設的網站**], 然後選取 [新增] **、[虛擬目錄**] 以開啟 [虛擬目錄建立嚮導]。  
  
4. 在嚮導中, 輸入`servicemodelsamples`做為您所建立虛擬目錄的別名。  
  
5. 設定到 %SystemDrive%\inetpub\wwwroot\servicemodelsamples 的路徑。 建立時，大部分的 WCF 範例會將服務可執行檔複製到這個位置。  
  
6. 按 [ **下一步**]。  
  
7. 預設會選取下列核取方塊：  
  
    - **Read**  
  
    - **執行腳本 (例如 ASP)**  
  
8. 按 **[下一步**], 然後按一下 **[完成**] 以完成嚮導。  
  
    > [!NOTE]
    > 這項工作只需執行一次, 因為所有 WCF 範例都使用相同的 servicemodelsamples 虛擬目錄。  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-70-or-75"></a>若要在 IIS 7.0 或7.5 中設定其他虛擬目錄屬性  
  
1. 按一下 servicemodelsamples 節點。 視窗的底部會有兩個檢視。 選取 [功能] [**視圖**] (如果尚未選取)。  
  
2. 按兩下專案以**流覽目錄**。  
  
3. 在 [動作] 窗格中, 選取 [**啟用**] 選項。 這可讓您使用 Internet Explorer 存取目錄的目錄；如此將有助於偵錯服務。  
  
 最後，您必須設定 servicemodelsamples 資料夾的安全性屬性，讓其他使用者能夠存取此資料夾。 如需詳細資訊，請參閱下方。  
  
#### <a name="to-set-additional-virtual-directory-properties-in-iis-51-or-60"></a>若要在 IIS 5.1 或 6.0 中設定額外的虛擬目錄屬性  
  
1. 以滑鼠右鍵按一下 [servicemodelsamples] 節點, 然後按一下 [**屬性**]。  
  
2. 預設會選取下列核取方塊：  
  
    - **Read**  
  
    - **記錄造訪**  
  
    - **為此資源編制索引**  
  
3. 選取 [**流覽目錄**] 核取方塊。 這可讓您使用 Internet Explorer 存取目錄的目錄；如此將有助於偵錯服務。  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-70-or-75"></a>若要在 IIS 7.0 或7.5 中設定資料夾的安全性屬性  
  
1. 巡覽至 %SystemDrive%\inetpub\wwwroot\servicemodelsamples。  
  
2. 以滑鼠右鍵按一下 [servicemodelsamples] 資料夾, 然後按一下 [**共用**] 或 [**共用于**]。  
  
3. 按一下 [**新增**] 按鈕左邊的向下箭號。  
  
4. 選取 [**尋找**] 專案。 [**選取使用者或群組**] 視窗隨即開啟。  
  
5. 按一下 [ **進階**]。  
  
6. 按一下 [**位置**]。 [**位置**] 視窗隨即開啟。  
  
7. 選取使用的電腦項目。 請務必選取本機電腦，而非列出的任何網域或網路項目。 選取電腦後, 按一下 **[確定]** 。  
  
8. 按一下 [**立即尋找**]。 這會將與本機電腦相關聯的物件填入到搜尋結果中。  
  
9. 在 [**名稱 (相對辨別名稱)** ] 資料行中尋找**IIS_IUSRS**專案。 選取該專案, 然後按一下 **[確定**] 以關閉搜尋結果視窗。  
  
10. 按一下 **[確定]** 以關閉 [**選取使用者或群組**] 視窗。  
  
11. 按一下 [**共用**] 保存變更。  
  
12. 啟用共用的變更完成後, 請按一下 [**完成**] 以關閉 [檔案**共用**] 視窗。  
  
#### <a name="to-set-security-properties-of-the-folder-in-iis-51-or-60"></a>設定 IIS 5.1 或 6.0 中資料夾的安全性屬性  
  
1. 巡覽至 %SystemDrive%\inetpub\wwwroot\servicemodelsamples。  
  
2. 以滑鼠右鍵按一下 [ **servicemodelsamples** ] 資料夾, 然後按一下 [**共用和安全性]。**  
  
3. 按一下 [ **安全性** ] 索引標籤。  
  
4. 如果您使用 IIS 6.0, 請在 [**群組或使用者名稱**] 方塊中, 檢查是否列出 [ **Internet Guest 帳戶**]。  
  
     如果未列出：  
  
    1. 按一下 [開始]，然後按一下 [控制台]。  
  
    2. 如果您看不到 [**使用者帳戶**] 圖示, 請按一下 [**切換到類別目錄檢視**]。  
  
    3. 按一下 [**使用者帳戶**] 圖示。  
  
    4. 在 [或選擇控制台圖示] 底下, 按一下 [**使用者帳戶**]。  
  
    5. 在 [**使用者帳戶**] 對話方塊中, 按一下 [ **Advanced** ] 索引標籤。  
  
    6. 按一下 [ **進階**]。  
  
    7. 在 [**本機使用者和群組**] 對話方塊中, 按一下以展開 [**使用者**] 資料夾。  
  
    8. 在右窗格中, 按兩下 [**網際網路來賓帳戶**]。  
  
    9. 在 [內容] 對話方塊中, 複製用來做為網際網路來賓帳戶的名稱。 根據預設，該名稱開頭為 "USR_"，後面會加上電腦的名稱。  
  
    10. 關閉 [內容] 對話方塊。  
  
    11. 關閉 [**本機使用者和群組**] 對話方塊。  
  
    12. 關閉 [**使用者帳戶**] 對話方塊。  
  
    13. 關閉 [其他**使用者帳戶**] 對話方塊。  
  
    14. 在 [ **Servicemodelsamples 屬性**] 對話方塊的 [**安全性**] 索引標籤上, 按一下 [**新增**]。  
  
    15. 輸入電腦名稱稱, 後面加上反斜線, 然後貼上網際網路使用者帳戶的名稱, 例如 myMachineName\\% InternetGuestAccountName%  
  
    16. 按一下 [**檢查名稱**] 以確認新增。 如果有效，該名稱會是全部大寫字母並加上底線。  
  
5. 針對 IIS 6.0, 也請檢查 [**群組或使用者名稱**] 方塊中是否列出 [網路服務]。  
  
     如果未列示 NETWORK SERVICE：  
  
    1. 按一下 [新增]。  
  
    2. 在 [**選取使用者或群組**] 對話方塊中, 輸入電腦名稱稱, 後面加上反斜線。  
  
    3. 在反斜線後面輸入**服務**(沒有空格)。  
  
    4. 按一下 [**檢查名稱**]。  
  
    5. 如果找到多個名稱, 請選取 [**網路服務**], 然後按一下 **[確定]** 。  
  
    6. 按一下 **[確定]** 以關閉 [**選取使用者或群組**] 對話方塊。  
  
6. 如果您使用 Windows XP SP2 搭配 IIS 5.1, 請檢查 [**群組或使用者名稱**] 方塊中是否列出 [網際網路來賓帳戶] 和 [ASPNET]。  
  
     請注意, ASPNET 使用者可能是內建 [**使用者**] 安全性群組的成員。 若是如此, 則如果 [**使用者**] 群組列在對話方塊中, 您就不需要將它當做個別專案新增至允許的使用者清單。  
  
     若要檢查 ASPNET 是否為**Users**安全性群組的一部分:  
  
    1. 在 [**開始**] 功能表上, 按一下 [**控制台**]。  
  
    2. 按一下 [**使用者帳戶**] 圖示。  
  
    3. 在 [**群組**] 資料行中, 檢查**ASPNET**的值是否為「使用者」。  
  
## <a name="see-also"></a>另請參閱

- [Internet Information Service 裝載指示](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)
