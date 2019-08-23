---
title: Internet Information Service 裝載指示
ms.date: 03/30/2017
ms.assetid: 959a21c8-9d9d-4757-b255-4e57793ae9d6
ms.openlocfilehash: 226b47bfd90dc4cffb0a364a804016043cc25d02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929116"
---
# <a name="internet-information-service-hosting-instructions"></a>Internet Information Service 裝載指示
若要執行由網際網路資訊服務 (IIS) 裝載的範例，您必須確定 IIS 已正確安裝並正在執行中。  
  
### <a name="to-install-iis-version-75-on-windows-server-2008-r2"></a>若要在 Windows Server 2008 R2 上安裝 IIS 7.5  
  
1. 從**伺服器管理員**選取 [**角色]。** 在 [**角色摘要**] 底下, 按一下 [**新增角色**]。  
  
2. 按 **[下一步**] 以顯示 [**選取伺服器角色**] 對話方塊。  
  
3. 從 [**角色**] 清單中選取 [**應用程式伺服器**], 然後按兩次 **[下一步]** , 顯示應用程式伺服器角色的 [**選取角色服務**] 對話方塊。  
  
4. 選取 [**網頁伺服器 (IIS)** ] 核取方塊。 如果系統提示您安裝其他角色服務和功能, 請按一下 [**新增所需的功能**]。 按兩次 [**下一步**], 顯示網頁伺服器 (IIS) 角色的 [**選取角色服務**] 對話方塊。  
  
5. 展開 [**管理工具**], 然後展開 [ **IIS 6 管理相容性**]。 選取 [ **IIS 6 腳本工具**]。 如果系統提示您安裝其他角色服務和功能, 請按一下 [**新增所需的角色服務**]。 按一下 [下一步]。  
  
6. 如果選取專案的摘要正確, 請按一下 [**安裝**]。  
  
7. 當安裝完成時, 按一下 [**關閉**]。  
  
### <a name="to-install-iis-version-75-on-windows-7"></a>若要在 Windows 7 上安裝 IIS 7.5 版  
  
1. 按一下 [**開始**], 然後按一下 [**控制台**]。  
  
2. 開啟 [**程式**] 群組。  
  
3. 在 [**程式和功能**] 底下, 按一下 [**開啟或關閉 Windows 功能**]。  
  
4. [**使用者帳戶控制**] 對話方塊隨即顯示。 按一下 [ **繼續**]。  
  
5. [ **Windows 功能**] 對話方塊隨即顯示。 展開標示為 [ **Internet Information Services**] 的專案。  
  
6. 展開標示為 [ **World Wide Web 服務**] 的專案。  
  
7. 展開標記為 [**應用程式開發功能**] 的專案。  
  
8. 請確定已選取下列項目：  
  
    1. **.NET 擴充性**  
  
    2. **ASP.NET**  
  
    3. **ISAPI 擴充程式**  
  
    4. **ISAPI 篩選器**  
  
9. 在標示為 [ **World Wide Web 服務**] 的專案下, 展開 [**一般 Http 功能**]。  
  
10. 請確定已選取 [**靜態內容**]。  
  
11. 在標示為 [ **World Wide Web 服務**] 的專案下, 展開 [**安全性**]。  
  
12. 請確定已選取 [ **Windows 驗證**]。  
  
13. 在 [ **Internet Information Services** ] 目錄底下, 展開標示為 [ **Web 管理工具**] 的專案, 然後選取 [ **IIS 管理主控台**]。  
  
14. 展開標記為 [ **iis 6 管理相容性**] 的專案, 然後選取 [ **Iis 6 腳本工具**]。  
  
15. 在 [ **Internet Information Services** ] 目錄底下, 展開標記為 [ **Microsoft .NET Framework 3.5.1**] 的專案, 然後選取 [ **Windows Communication Foundation Http 啟用**]。  
  
16. 按一下 [確定]。  
  
### <a name="to-install-iis-version-70-on-windows-server-2008"></a>在 Windows Server 2008 上安裝 IIS 7.0 版  
  
1. 從**伺服器管理員**選取 [**角色**]。 在 [**角色摘要**] 底下, 按一下 [**新增角色**]。  
  
2. 按 **[下一步**] 以顯示 [**選取伺服器角色**] 對話方塊。  
  
3. 從 [**角色**] 清單中選取 [**應用程式伺服器**], 然後按兩次 **[下一步]** , 顯示應用程式伺服器角色的 [**選取角色服務**] 對話方塊。  
  
4. 選取 **[網頁伺服器 (IIS)** ] 核取方塊。 如果系統提示您安裝其他角色服務和功能, 請按一下 [**新增所需的功能**]。 按兩次 [**下一步**], 顯示網頁伺服器 (IIS) 角色的 [**選取角色服務**] 對話方塊。  
  
5. 展開 [**管理工具**], 然後展開 [ **IIS 6 管理相容性**]。 選取 [ **IIS 6 腳本工具**]。 如果系統提示您安裝其他角色服務和功能, 請按一下 [**新增所需的角色服務**]。 按一下 [下一步]。  
  
6. 如果選取專案的摘要正確, 請按一下 [**安裝**]。  
  
7. 當安裝完成時, 按一下 [**關閉**]。  
  
### <a name="to-install-iis-version-70-on-windows-vista"></a>在 Windows Vista 上安裝 IIS 7.0 版  
  
1. 按一下 [開始]，然後按一下 [控制台]。  
  
2. 選取 [**程式**] 群組。  
  
3. 在 [**程式和功能**] 底下, 按一下 [**開啟或關閉 Windows 功能**]。  
  
4. [**使用者帳戶控制**] 對話方塊隨即顯示。 按一下 [ **繼續**]。  
  
5. [ **Windows 功能**] 對話方塊隨即顯示。 展開標示為 [ **Internet Information Services**] 的專案。  
  
6. 展開標示為 [ **World Wide Web 服務**] 的專案。  
  
7. 展開標記為 [**應用程式開發功能**] 的專案。  
  
8. 請確定已選取下列項目：  
  
    1. **.NET 擴充性**  
  
    2. **ASP.NET**  
  
    3. **ISAPI 擴充程式**  
  
    4. **ISAPI 篩選器**  
  
9. 展開標記為 [ **Web 管理工具**] 的專案, 然後選取 [ **IIS 管理主控台**]。  
  
10. 在標示為 [ **World Wide Web 服務**] 的專案下, 展開 [**一般 Http 功能**]。  
  
11. 請確定已選取 [**靜態內容**]。  
  
12. 在標示為 [ **World Wide Web 服務**] 的專案下, 展開 [**安全性**]。  
  
13. 請確定已選取 [ **Windows 驗證**]。  
  
14. 展開標記為 [ **iis 6 管理相容性**] 的專案, 然後選取 [ **Iis 6 腳本工具**]。  
  
15. 展開標記為 [ **Microsoft .NET Framework 3.0**] 的專案, 然後選取 [ **Windows Communication Foundation Http 啟用**]。  
  
16. 按一下 [確定 **Deploying Office Solutions**]。  
  
### <a name="to-install-iis-version-60-on-windows-server-2003"></a>在 Windows Server 2003 上安裝 IIS 6.0 版  
  
1. 從 [**管理您的伺服器**], 按一下 [**新增或移除角色**], 然後按 **[下一步]** 。  
  
2. 從 [**伺服器角色**] 清單中選取 [**應用程式伺服器 (IIS, ASP.NET)** ], 然後按 **[下一步]** 。  
  
3. 選取 [**啟用 ASP.NET** ] 核取方塊, 然後按 **[下一步]** 。  
  
4. 如果選項的摘要正確，請按一下 [下一步]。  
  
### <a name="to-install-iis-version-51-on-windows-xp-with-service-pack-2-and-service-pack-3-installed"></a>若要在已安裝 Service Pack 2 和 Service Pack 3 的 Windows XP 上安裝 IIS 5.1 版  
  
1. 在 [控制台] 中, 按一下 [**新增或移除程式**]。  
  
2. 在 [**新增或移除程式**] 對話方塊中, 按一下 [**新增/移除 Windows 元件**]。  
  
3. 在 [ **Windows 元件]** 中, 選取 [ **Internet Information Services (IIS)** ] 核取方塊, 然後按 **[下一步]** 。  
  
4. 如果顯示 [**需要**檔案] 對話方塊, 請插入作業系統安裝光碟, 流覽至 [i386] 資料夾, 然後按一下 **[確定]** 。  
  
5. 當安裝完成時, 按一下 **[完成]** 。  
  
6. 關閉 [**新增或移除程式**] 對話方塊, 然後關閉 [**控制台**]。  
  
### <a name="to-verify-the-installation-of-iis-and-aspnet"></a>確認 IIS 和 ASP.NET 安裝  
  
1. 將本主題結尾處的 HTML 檔儲存在根 \InetPub\wwwroot 目錄，並重新命名為 Default.aspx。  
  
2. 開啟瀏覽器視窗。  
  
3. 在`http://localhost/Default.aspx` [位址] 方塊中輸入, 然後按 enter。  
  
4. 這時應該會出現包含文字 "Hello World" 的網頁。  
  
> [!NOTE]
> 每次您安裝新版的 .NET Framework 時, 都必須重新註冊 aspnet_isapi 做為 IIS 的 Web 服務延伸模組。 若要這樣做，請發出 `aspnet_regiis –I –enable` 命令。  
  
## <a name="sample-code"></a>程式碼範例  
  
```xml  
<html>  
   <body>  
       <form >  
           <h3> Hello World  
           </h3>  
       </form>  
   </body>  
</html>  
```
