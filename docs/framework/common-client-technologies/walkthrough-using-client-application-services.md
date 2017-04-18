---
title: "逐步解說：使用用戶端應用程式服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "應用程式服務主機 [用戶端應用程式服務]"
  - "用戶端應用程式服務, 逐步解說"
ms.assetid: bb7c8950-4517-4dae-b705-b74a14059b26
caps.latest.revision: 47
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 47
---
# 逐步解說：使用用戶端應用程式服務
本主題說明如何建立使用用戶端應用程式服務驗證使用者，以及擷取使用者角色和設定的 Windows 應用程式。  
  
 在這個逐步解說中，您將執行下列工作：  
  
-   建立 Windows Form 應用程式，並使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 專案設計工具啟用及設定用戶端應用程式服務。  
  
-   建立簡單的 ASP.NET Web 服務應用程式，以裝載應用程式服務並測試用戶端組態。  
  
-   將表單驗證加入應用程式。 一開始會使用硬式編碼的使用者名稱和密碼測試服務。 然後將登入表單指定為應用程式組態中的認證提供者予以加入。  
  
-   加入以角色為基礎的功能，並且只針對 "manager" 角色的使用者啟用和顯示按鈕。  
  
-   存取 Web 設定。 一開始會在專案設計工具的 \[設定\] 頁面上載入已驗證 \(測試\) 使用者的 Web 設定。 然後使用 Windows Form 設計工具將文字方塊繫結至 Web 設定。 最後再將已修改的值儲存回伺服器。  
  
-   實作登出。 您會將登出選項加入表單，然後呼叫登出方法。  
  
-   啟用離線模式。 您會提供核取方塊，讓使用者指定其連接狀態。 然後使用這個值指定用戶端應用程式服務提供者，是否使用本機快取資料而不是存取其 Web 服務。 最後當應用程式返回線上模式時，再重新驗證目前的使用者。  
  
## 必要條件  
 您需要下列元件才能完成這個逐步解說：  
  
-   [!INCLUDE[vs_orcas_long](../../../includes/vs-orcas-long-md.md)].  
  
## 建立用戶端應用程式  
 首先您必須建立 Windows Form 專案。 本逐步解說使用 Windows Form，因為很多人已熟悉這項功能，而且其程序類似 Windows Presentation Foundation \(WPF\) 專案。  
  
#### 建立用戶端應用程式並啟用用戶端應用程式服務  
  
1.  在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中，選取 \[檔案 &#124;新增 &#124; 專案\] 功能表選項。  
  
2.  在 \[新增專案\] 對話方塊中，展開 \[專案類型\] 窗格中的 \[Visual Basic\] 或 \[Visual C\#\] 節點，然後選取 \[Windows\] 專案類型。  
  
3.  確定已選取 \[.NET Framework 3.5\]，然後選取 \[Windows Form 應用程式\] 範本。  
  
4.  將專案的 \[名稱\] 變更為 `ClientAppServicesDemo`，然後按一下 \[確定\]。  
  
     在 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 中隨即開啟新的 Windows Form 專案。  
  
5.  在 \[專案\] 功能表上，選取 \[ClientAppServicesDemo 屬性\]。  
  
     \[專案設計工具\] 隨即出現。  
  
6.  在 \[服務\] 索引標籤上，選取 \[啟用用戶端應用程式服務\]。  
  
7.  確定選取了 \[使用表單驗證\]，然後將 \[驗證服務位置\]、\[角色服務位置\] 及 \[Web 設定服務位置\] 設定為 `http://localhost:55555/AppServices`。  
  
8.  在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 的 \[應用程式\] 索引標籤上，將 \[驗證模式\] 設定為 \[由應用程式定義\]。  
  
 設計工具會將指定的設定儲存在應用程式的 app.config 檔中。  
  
 此時，應用程式會設定為從相同的主機存取這三種服務。 在下一節中，您將建立以簡單 Web 服務應用程式呈現的主機，以便您測試用戶端組態。  
  
## 建立應用程式服務主機  
 在本節中，您將建立簡單的 Web 服務應用程式，以便從本機 SQL Server Compact 資料庫檔案存取使用者資料。 接下來，您將會使用 [ASP.NET Web Site Administration Tool](../Topic/ASP.NET%20Web%20Site%20Administration%20Tool.md) 植入資料庫。 這個簡單的組態可讓您快速地測試用戶端應用程式。 除此之外，您還可以設定 Web 服務主機，以便從完整的 SQL Server 資料庫存取使用者資料，或透過自訂 <xref:System.Web.Security.MembershipProvider> 和 <xref:System.Web.Security.RoleProvider> 類別來存取使用者資料。 如需詳細資訊，請參閱[Creating and Configuring the Application Services Database for SQL Server](../Topic/Creating%20and%20Configuring%20the%20Application%20Services%20Database%20for%20SQL%20Server.md)。  
  
 在下列程序中，您將建立並設定 AppServices Web 服務。  
  
#### 建立並設定應用程式服務主機  
  
1.  在 \[方案總管\] 中，選取 ClientAppServicesDemo 方案，然後在 \[檔案\] 功能表上，選取 \[加入 &#124; 新增專案\]。  
  
2.  在 \[加入新的專案\] 對話方塊中，展開 \[專案類型\] 窗格中的 \[Visual Basic\] 或 \[Visual C\#\] 節點，然後選取 \[Web\] 專案類型。  
  
3.  確定已選取 \[.NET Framework 3.5\]，然後選取 \[ASP.NET Web 服務應用程式\] 範本。  
  
4.  將專案的 \[名稱\] 變更為 `AppServices`，然後按一下 \[確定\]。  
  
     新的 ASP.NET Web 服務應用程式專案隨即加入方案，並在編輯器中顯示 Service1.asmx.vb 或 Service1.asmx.cs 檔案。  
  
    > [!NOTE]
    >  這個範例中不會使用 Service1.asmx.vb 或 Service1.asmx.cs 檔案。 如果您想要保持工作環境的整齊，可以將其關閉，並將其從 \[方案總管\]中刪除。  
  
5.  在 \[方案總管\] 中，選取 AppServices 專案，然後在 \[專案\] 功能表上，選取 \[AppServices 屬性\]。  
  
     \[專案設計工具\] 隨即出現。  
  
6.  在 \[Web\] 索引標籤上，確定已選取 \[使用 Visual Studio 程式開發伺服器\]。  
  
7.  選取 \[指定通訊埠\]，再將值指定為 `55555`，然後將 \[虛擬路徑\] 設定為 `/AppServices`。  
  
8.  儲存所有檔案。  
  
9. 在 \[方案總管\] 中，開啟 Web.config，然後尋找 `<system.web>` 開頭標記。  
  
10. 在 `<system.web>` 標記 \(Tag\) 之前加入下列標記 \(Markup\)。  
  
     在這個標記中的 `authenticationService`、`profileService` 和 `roleService` 項目會啟用及設定應用程式服務。 基於測試目的，`authenticationService` 項目的 `requireSSL` 屬性會設定為 "false"。`profileService` 項目的 `readAccessProperties` 和 `writeAccessProperties` 屬性 \(Attribute\) 表示 `WebSettingsTestText` 屬性 \(Property\) 是讀取\/寫入。  
  
    > [!NOTE]
    >  在實際執行的程式碼中，一定要透過 Secure Sockets Layer \(SSL，使用 HTTPS 通訊協定\) 存取驗證服務。 如需如何設定 SSL 的資訊，請參閱 [Configuring Secure Sockets Layer \(IIS 6.0 Operations Guide\)](http://go.microsoft.com/fwlink/?LinkId=91844) \(設定安全通訊端層 \(IIS 6.0 操作指南\)\)。  
  
    ```  
    <system.web.extensions>  
      <scripting>  
        <webServices>  
          <authenticationService enabled="true" requireSSL = "false"/>  
          <profileService enabled="true"  
            readAccessProperties="WebSettingsTestText"  
            writeAccessProperties="WebSettingsTestText" />  
          <roleService enabled="true"/>  
        </webServices>  
      </scripting>  
    </system.web.extensions>  
    ```  
  
11. 在 `<system.web>` 開頭標記 \(Tag\) 之後加入下列標記 \(Markup\)，將其包含在 `<system.web>` 項目中。  
  
     `profile` 項目會設定名為 `WebSettingsTestText` 的單一 Web 設定。  
  
    ```  
    <profile enabled="true" >  
      <properties>  
        <add name="WebSettingsTestText" type="string"   
          readOnly="false" defaultValue="DefaultText"   
          serializeAs="String" allowAnonymous="false" />  
      </properties>  
    </profile>  
  
    ```  
  
 在下列程序中，您將使用 \[ASP.NET 網站管理工具\] 來完成服務組態，並填入本機資料庫檔案。 您將加入兩位使用者，並將其命名為 `employee` 及 `manager`。兩者會分屬兩個同名的角色。 使用者密碼各為 `employee!` 及 `manager!`。  
  
#### 設定成員資格和角色  
  
1.  在 \[方案總管\] 中，選取 AppServices 專案，然後在 \[專案\] 功能表上，選取 \[ASP.NET 組態\]。  
  
     \[ASP.NET 網站管理工具\] 隨即出現。  
  
2.  在 \[安全性\] 索引標籤上，按一下 \[使用安全性設定精靈，逐步設定安全性\]。  
  
     \[安全性設定精靈\] 隨即出現，並顯示 \[歡迎使用\] 步驟。  
  
3.  按 \[**下一步**\]。  
  
     \[選取存取方法\] 步驟隨即出現。  
  
4.  選取 \[從網際網路\]。 這會將服務設定為使用表單驗證，而不是 Windows 驗證。  
  
5.  按 \[**下一步**\] 兩次。  
  
     \[定義角色\] 步驟隨即出現。  
  
6.  選取 \[啟用這個網站的角色\]。  
  
7.  按 \[**下一步**\]。 \[建立新角色\] 表單隨即出現。  
  
8.  在 \[新角色名稱\] 文字方塊中輸入 `manager`，然後按一下 \[加入角色\]。  
  
     具有指定值的 \[現有角色\] 資料表隨即出現。  
  
9. 將 \[新角色名稱\] 文字方塊中的 `manager` 置換成 `employee`，然後按一下 \[加入角色\]。  
  
     \[現有角色\] 資料表中隨即出現新的值。  
  
10. 按 \[**下一步**\]。  
  
     \[加入新的使用者\] 步驟隨即出現。  
  
11. 在 \[建立使用者\] 表單中，指定下列值。  
  
    |||  
    |-|-|  
    |**使用者名稱**|`manager`|  
    |**密碼**|`manager!`|  
    |**確認密碼**|`manager!`|  
    |**電子郵件**|`manager@contoso.com`|  
    |**安全性問題**|`manager`|  
    |**安全性解答**|`manager`|  
  
12. 按一下 \[建立使用者\]。  
  
     成功訊息隨即出現。  
  
    > [!NOTE]
    >  \[電子郵件\]、\[安全性問題\] 和 \[安全性解答\] 是表單的必要值，但這個範例中並未使用。  
  
13. 按一下 \[**繼續**\]。  
  
     \[建立使用者\] 表單隨即再度出現。  
  
14. 在 \[建立使用者\] 表單中，指定下列值。  
  
    |||  
    |-|-|  
    |**使用者名稱**|`employee`|  
    |**密碼**|`employee!`|  
    |**確認密碼**|`employee!`|  
    |**電子郵件**|`employee@contoso.com`|  
    |**安全性問題**|`Employee`|  
    |**安全性解答**|`employee`|  
  
15. 按一下 \[建立使用者\]。  
  
     成功訊息隨即出現。  
  
16. 按一下 \[**完成**\]。  
  
     \[網站管理工具\] 隨即再度出現。  
  
17. 按一下 \[Manager 使用者\]。  
  
     使用者清單隨即出現。  
  
18. 針對 \[employee\] 使用者按一下 \[編輯角色\]，然後選取 \[employee\] 角色。  
  
19. 針對 \[manager\] 使用者按一下 \[編輯角色\]，然後選取 \[manager\] 角色。  
  
20. 關閉裝載 \[網站管理工具\] 的瀏覽器視窗。  
  
21. 如果出現訊息方塊，詢問您是否要重新載入已修改的 Web.config 檔案，按一下 \[是\]。  
  
 如此即完成 Web 服務設定。 此時，您可以按 F5 鍵執行用戶端應用程式，\[ASP.NET 程式開發伺服器\] 將會自動與用戶端應用程式一起啟動。 在您結束應用程式之後，伺服器會繼續執行，但是會在重新啟動應用程式時重新啟動。 如此可讓它偵測對 Web.config 所做的任何變更。  
  
 若要手動停止伺服器，請以滑鼠右鍵按一下工作列上通知區域中的 ASP.NET 程式開發伺服器圖示，然後按一下 \[停止\]。 有時候在確定是否完全重新啟動時會很有用。  
  
## 加入表單驗證  
 在下列程序中，您會將程式碼加入主要表單，以嘗試驗證使用者，並在使用者提供無效的認證時拒絕存取。 您會使用硬式編碼的使用者名稱和密碼測試服務。  
  
#### 在應用程式程式碼中驗證使用者  
  
1.  在 \[方案總管\] 中，於 ClientAppServicesDemo 專案中加入 System.Web 組件的參考。  
  
2.  選取 Form1 檔案，然後從 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 主功能表選取 \[檢視 &#124; 程式碼\]。  
  
3.  在程式碼編輯器中，將下列陳述式加入 Form1 檔案的頂端。  
  
     [!code-csharp[ClientApplicationServices#001](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#001)]
     [!code-vb[ClientApplicationServices#001](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#001)]  
  
4.  在 \[方案總管\] 中，按兩下 Form1 以顯示設計工具。  
  
5.  在設計工具中，按兩下表單介面以產生名為 `Form1_Load` 的 <xref:System.Windows.Forms.Form.Load?displayProperty=fullName> 事件處理常式。  
  
     程式碼編輯器隨即出現，並將游標置於 `Form1_Load` 方法中。  
  
6.  將下列程式碼加入至 `Form1_Load` 方法。  
  
     這段程式碼會以結束應用程式的方式，來拒絕未經驗證之使用者的存取。 或者，您可以允許未經驗證的使用者存取表單，但拒絕其存取特定功能。 您通常不會以這種方式硬式編碼使用者名稱和密碼，但是基於測試目的就很有用。 在下一節中，您將會使用更強固的程式碼來取代這段程式碼，以顯示 \[登入\] 對話方塊並包含例外狀況處理。  
  
     請注意，`static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> 方法是在 [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)] 中。 這個方法會將其工作委派給已設定的驗證提供者，然後在驗證成功時傳回 `true`。 您的應用程式不需要直接參考用戶端驗證提供者。  
  
     [!code-csharp[ClientApplicationServices#300](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#300)]
     [!code-vb[ClientApplicationServices#300](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#300)]  
  
 您現在可以按 F5 鍵執行應用程式，由於提供了正確的使用者名稱和密碼，您將會看到表單。  
  
> [!NOTE]
>  如果您無法執行應用程式，請嘗試停止 ASP.NET 程式開發伺服器。 當伺服器重新啟動時，請確認通訊埠設定為 55555。  
  
 若要改為查看錯誤訊息，請變更 <xref:System.Web.Security.Membership.ValidateUser%2A> 參數。 例如，以不正確的密碼 \(像是 `"MANAGER"`\) 取代第二個 `"manager!"` 參數。  
  
## 加入登入表單當做認證提供者  
 您可以在應用程式程式碼中取得使用者認證，並將其傳遞給 <xref:System.Web.Security.Membership.ValidateUser%2A> 方法。 不過，如果您稍後想要進行變更，將取得認證的程式碼與應用程式程式碼分開通常會很有用。  
  
 在下列程序中，您會將應用程式設定為使用認證提供者，然後變更您的 <xref:System.Web.Security.Membership.ValidateUser%2A> 方法呼叫，同時針對兩個參數傳遞 <xref:System.String.Empty>。 空字串會對 <xref:System.Web.Security.Membership.ValidateUser%2A> 方法發出訊號，使其呼叫已設定之認證提供者的 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> 方法。  
  
#### 將應用程式設定為使用認證提供者  
  
1.  在 \[方案總管\] 中，選取 ClientAppServicesDemo 專案，然後在 \[專案\] 功能表上，選取 \[ClientAppServicesDemo 屬性\]。  
  
     \[專案設計工具\] 隨即出現。  
  
2.  在 \[服務\] 索引標籤上，將 \[選擇性：認證提供者\] 設定為下列值。 這個值表示組件限定類型名稱。  
  
    ```  
    ClientAppServicesDemo.Login, ClientAppServicesDemo  
    ```  
  
3.  在 Form1 程式碼檔案中，將 `Form1_Load` 方法中的程式碼以下列程式碼取代。  
  
     這段程式碼會顯示歡迎訊息，然後呼叫在下一個步驟中加入的 `ValidateUsingCredentialsProvider` 方法。 如果使用者未經過驗證，`ValidateUsingCredentialsProvider` 方法會傳回 `false`，且 `Form1_Load` 方法會傳回。 這可以避免在應用程式結束之前執行任何其他的程式碼。 歡迎訊息可以清楚表示應用程式重新啟動的時間。 當您在本逐步解說稍後實作登出時，將會加入程式碼以重新啟動應用程式。  
  
     [!code-csharp[ClientApplicationServices#011](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#011)]
     [!code-vb[ClientApplicationServices#011](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#011)]  
  
4.  將下列方法加入 `Form1_Load` 方法之後。  
  
     這個方法會將空字串傳遞給 `static`<xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> 方法，而出現 \[登入\] 對話方塊。 如果驗證服務無法使用，<xref:System.Web.Security.Membership.ValidateUser%2A> 方法會擲回 <xref:System.Net.WebException>。 在這種情況下，`ValidateUsingCredentialsProvider` 方法會顯示警告訊息，並詢問使用者是否要在離線模式中再試一次。 此功能需要**將密碼雜湊儲存在本機，以便能使用離線登入功能**，如[如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)所述。 新專案預設會啟用這項功能。  
  
     如果使用者未經過驗證，`ValidateUsingCredentialsProvider` 方法會顯示錯誤訊息並結束應用程式。 最後，這個方法會傳回驗證嘗試的結果。  
  
     [!code-csharp[ClientApplicationServices#020](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#020)]
     [!code-vb[ClientApplicationServices#020](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#020)]  
  
### 建立登入表單  
 認證提供者是實作 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> 介面的類別。 這個介面具有名為 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> 的單一方法，可傳回 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> 物件。 下列程序說明如何建立實作 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> 的 \[登入\] 對話方塊，以顯示本身並傳回使用者指定的認證。  
  
 針對 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 和 C\# 所提供的程序不同，因為 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 提供 \[登入表單\] 範本。 這可以節省一些時間和撰寫程式碼的工作。  
  
##### 建立 \[登入\] 對話方塊當做 Visual Basic 中的認證提供者  
  
1.  在 \[方案總管\] 中，選取 ClientAppServicesDemo 專案，然後在 \[專案\] 功能表上，選取 \[加入新項目\]。  
  
2.  在 \[加入新項目\] 對話方塊中，選取 \[登入表單\] 範本，再將項目的 \[名稱\] 變更為 `Login.vb`，然後按一下 \[加入\]。  
  
     \[登入\] 對話方塊隨即在 \[Windows Form 設計工具\] 中出現。  
  
3.  在設計工具中，選取 \[確定\] 按鈕，然後在 \[屬性\] 視窗中，將 `DialogResult` 設定為 `OK`。  
  
4.  在設計工具中，將 `CheckBox` 控制項加入 \[密碼\] 文字方塊下的表單中。  
  
5.  在 \[屬性\] 視窗中，將 \[\(名稱\)\] 值指定為 `rememberMeCheckBox`，並將 \[文字\] 值指定為 `&Remember me`。  
  
6.  從 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 主功能表選取 \[檢視 &#124; 程式碼\]。  
  
7.  在程式碼編輯器中，將下列程式碼加入檔案的頂端。  
  
     [!code-vb[ClientApplicationServices#101](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#101)]  
  
8.  修改類別簽章，使類別實作 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> 介面。  
  
     [!code-vb[ClientApplicationServices#110](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#110)]  
  
9. 確定游標在 `IClientformsAuthenticationCredentialsProvider` 之後，然後按 Enter 鍵產生 `GetCredentials` 方法。  
  
10. 找出 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> 實作，然後以下列程式碼取代。  
  
     [!code-vb[ClientApplicationServices#120](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#120)]  
  
 下列 C\# 程序提供簡單 \[登入\] 對話方塊的完整程式碼清單。 這個對話方塊的配置有一點粗糙，但是重點是 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> 實作。  
  
##### 建立 \[登入\] 對話方塊當做 C\# 中的認證提供者  
  
1.  在 \[方案總管\] 中，選取 ClientAppServicesDemo 專案，然後在 \[專案\] 功能表上，選取 \[加入類別\]。  
  
2.  在 \[加入新項目\] 對話方塊中，將 \[名稱\] 變更為 `Login.cs`，然後按一下 \[加入\]。  
  
     Login.cs 檔案隨即在程式碼編輯器中開啟。  
  
3.  使用下列程式碼取代預設程式碼。  
  
     [!code-csharp[ClientApplicationServices#200](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#200)]  
  
 您現在可以執行應用程式，然後會看到 \[登入\] 對話方塊出現。 若要測試這段程式碼，請同時嘗試有效和無效的不同認證，然後確認您只能夠以有效認證存取表單。 有效的使用者名稱為 `employee` 及 `manager`； 密碼則分別為 `employee!` 及 `manager!`。  
  
> [!NOTE]
>  請勿在此時選取 \[記住我\]，否則在本逐步解說稍後實作登出之前，您都無法以其他使用者身分登入。  
  
## 加入以角色為基礎的功能  
 在下列程序中，您會加入一個按鈕到表單，並只針對 manager 角色的使用者顯示該按鈕。  
  
#### 根據使用者角色變更使用者介面  
  
1.  在 \[方案總管\] 中，選取 ClientAppServicesDemo 專案中的 Form1，然後從 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 主功能表選取 \[檢視 &#124; 設計工具\]。  
  
2.  在設計工具中，從 \[工具箱\] 將 <xref:System.Windows.Forms.Button> 控制項加入表單。  
  
3.  在 \[屬性\] 視窗中，設定按鈕的下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**\(名稱\)**|managerOnlyButton|  
    |**Text**|&Manager task|  
    |**可見**|`False`|  
  
4.  在 Form1 的程式碼編輯器中，將下列程式碼加入 `Form1_Load` 方法的結尾。  
  
     這段程式碼會呼叫在下一個步驟中加入的 `DisplayButtonForManagerRole` 方法。  
  
     [!code-csharp[ClientApplicationServices#012](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#012)]
     [!code-vb[ClientApplicationServices#012](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#012)]  
  
5.  將下列方法加入 Form1 類別的結尾。  
  
     這個方法會呼叫 `static`<xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=fullName> 屬性所傳回之 <xref:System.Security.Principal.IPrincipal> 的 <xref:System.Security.Principal.IPrincipal.IsInRole%2A> 方法。 針對設定為使用用戶端應用程式服務的應用程式，這個屬性會傳回 <xref:System.Web.ClientServices.ClientRolePrincipal>。 因為這個類別會實作 <xref:System.Security.Principal.IPrincipal> 介面，所以您不需要明確地參考它。  
  
     如果使用者的角色為 "manager"，`DisplayButtonForManagerRole` 方法會將 `managerOnlyButton` 的 <xref:System.Windows.Forms.Control.Visible%2A> 屬性設定為 `true`。 如果擲回 <xref:System.Net.WebException> 表示角色服務無法使用，這個方法也會顯示錯誤訊息。  
  
    > [!NOTE]
    >  如果使用者登入已過期，<xref:System.Web.ClientServices.ClientRolePrincipal.IsInRole%2A> 方法一律會傳回 `false`。 如果應用程式在驗證後很短的時間內呼叫一次 <xref:System.Security.Principal.IPrincipal.IsInRole%2A> 方法 \(如本逐步解說的範例程式碼所示\)，則不會發生這種情況。 如果應用程式必須在其他時間點擷取使用者角色，您可能會想要加入程式碼，以重新驗證登入已過期的使用者。 如果所有有效的使用者都獲派角色，您可以呼叫 <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A?displayProperty=fullName> 方法以判斷登入是否過期。 如果沒有角色傳回，則表示登入已過期。 如需這項功能的範例，請參閱 <xref:System.Web.ClientServices.Providers.ClientRoleProvider.GetRolesForUser%2A> 方法。 只有在應用程式組態中已選取 \[要求使用者在伺服器 Cookie 過期時必須再次登入\] 時，才需要這項功能。 如需詳細資訊，請參閱[如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)。  
  
     [!code-csharp[ClientApplicationServices#030](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#030)]
     [!code-vb[ClientApplicationServices#030](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#030)]  
  
 如果驗證成功，用戶端驗證提供者會將 <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=fullName> 屬性設定為 <xref:System.Web.ClientServices.ClientRolePrincipal> 類別的執行個體。 這個類別會實作 <xref:System.Security.Principal.IPrincipal.IsInRole%2A> 方法，以便將工作委派給已設定的角色提供者。 如前所述，應用程式程式碼不需要直接參考服務提供者。  
  
 您現在可以執行應用程式並以 employee 身分登入，您會發現按鈕並未顯示；然後再以 manager 身分登入，則會看到按鈕。  
  
## 存取 Web 設定  
 在下列程序中，您會將文字方塊加入表單並繫結至 Web 設定。 如同先前使用驗證和角色的程式碼，您的設定程式碼不會直接存取設定提供者， 而是會使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 針對專案所產生的強類型 `Settings` 類別 \(在 C\# 中是當做 `Properties.Settings.Default` 存取，而在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中則是當做 `My.Settings` 存取\)。  
  
#### 在使用者介面中使用 Web 設定  
  
1.  檢查工作列的通知區域，確定 \[ASP.NET Web 程式開發伺服器\] 仍在執行中。 如果您已停止伺服器，請重新啟動應用程式 \(這會自動啟動伺服器\)，然後關閉 \[登入\] 對話方塊。  
  
2.  在 \[方案總管\] 中，選取 ClientAppServicesDemo 專案，然後在 \[專案\] 功能表上，選取 \[ClientAppServicesDemo 屬性\]。  
  
     \[專案設計工具\] 隨即出現。  
  
3.  在 \[設定\] 索引標籤上，按一下 \[載入 Web 設定\]。  
  
     \[登入\] 對話方塊隨即出現。  
  
4.  輸入 employee 或 manager 的認證，然後按一下 \[登入\]。 您將使用的 Web 設定已設定為只有經過驗證的使用者才能存取，因此按一下 \[略過登入\] 將不會載入任何設定。  
  
     `WebSettingsTestText` 設定會以 `DefaultText` 的預設值出現在設計工具中。 此外，也會為專案產生包含 `WebSettingsTestText` 屬性的 `Settings` 類別。  
  
5.  在 \[方案總管\] 中，選取 ClientAppServicesDemo 專案中的 Form1，然後從 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 主功能表選取 \[檢視 &#124; 設計工具\]。  
  
6.  在設計工具中，將 <xref:System.Windows.Forms.TextBox> 控制項加入表單。  
  
7.  在 \[屬性\] 視窗中，指定 `webSettingsTestTextBox` 的 \[\(名稱\)\] 值 。  
  
8.  在程式碼編輯器中，將下列程式碼加入 `Form1_Load` 方法的結尾。  
  
     這段程式碼會呼叫在下一個步驟中加入的 `BindWebSettingsTestTextBox` 方法。  
  
     [!code-csharp[ClientApplicationServices#013](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#013)]
     [!code-vb[ClientApplicationServices#013](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#013)]  
  
9. 將下列方法加入 Form1 類別的結尾。  
  
     這個方法會將 `webSettingsTestTextBox` 的 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性，繫結至本程序稍早所產生之 `Settings` 類別的 `WebSettingsTestText` 屬性。 如果擲回 <xref:System.Net.WebException> 表示 Web 設定無法使用，這個方法也會顯示錯誤訊息。  
  
     [!code-csharp[ClientApplicationServices#040](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#040)]
     [!code-vb[ClientApplicationServices#040](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#040)]  
  
    > [!NOTE]
    >  您通常會使用資料繫結啟用控制項與 Web 設定之間的自動雙向通訊。 不過，您也可以直接存取 Web 設定，如同下列範例所示：  
  
     [!code-csharp[ClientApplicationServices#322](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#322)]
     [!code-vb[ClientApplicationServices#322](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#322)]  
  
10. 在設計工具中選取表單，然後在 \[屬性\] 視窗中按一下 \[事件\] 按鈕。  
  
11. 選取 <xref:System.Windows.Forms.Form.FormClosing> 事件，然後按 ENTER 鍵產生事件處理常式。  
  
12. 以下列程式碼取代所產生的方法。  
  
     <xref:System.Windows.Forms.Form.FormClosing> 事件處理常式會呼叫 `SaveSettings` 方法，下一節將加入的登出功能也會使用這個方法。`SaveSettings` 方法會先確認使用者尚未登出， 作法是檢查目前主體所傳回之 <xref:System.Security.Principal.IIdentity> 的 <xref:System.Security.Principal.IIdentity.AuthenticationType%2A> 屬性。 目前的主體是透過 `static`<xref:System.Threading.Thread.CurrentPrincipal%2A> 屬性所擷取。 如果使用者已經過驗證可使用用戶端應用程式服務，驗證類型將會是 "ClientForms"。`SaveSettings` 方法不能只檢查 <xref:System.Security.Principal.IIdentity.IsAuthenticated%2A?displayProperty=fullName> 屬性，因為使用者在登出後可能仍擁有有效的 Windows 識別。  
  
     如果使用者尚未登出，`SaveSettings` 方法會呼叫在這個程序稍早所產生之 `Settings` 類別的 <xref:System.Configuration.ApplicationSettingsBase.Save%2A> 方法。 如果驗證 Cookie 已過期，這個方法會擲回 <xref:System.Net.WebException>。 只有在應用程式組態中已選取 \[要求使用者在伺服器 Cookie 過期時必須再次登入\] 時，才會發生這種情況。 如需詳細資訊，請參閱[如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)。`SaveSettings` 方法會透過呼叫 <xref:System.Web.Security.Membership.ValidateUser%2A> 顯示 \[登入\] 對話方塊的方式，處理 Cookie 過期。 如果使用者成功登入，`SaveSettings` 方法會呼叫本身以嘗試再次儲存設定。  
  
     如同先前的程式碼，如果遠端服務無法使用，`SaveSettings` 方法會顯示錯誤訊息。 如果設定提供者無法存取遠端服務，則設定仍然會儲存在本機快取中，然後在應用程式重新啟動時重新載入。  
  
     [!code-csharp[ClientApplicationServices#050](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#050)]
     [!code-vb[ClientApplicationServices#050](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#050)]  
  
13. 將下列方法加入 Form1 類別的結尾。  
  
     這段程式碼會處理 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved?displayProperty=fullName> 事件，並在無法儲存任何設定時顯示警告。 如果設定服務無法使用或驗證 Cookie 已過期，則不會發生 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> 事件。<xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> 事件發生時機的其中一個範例是如果使用者已經登出。 您可以在呼叫 <xref:System.Configuration.ApplicationSettingsBase.Save%2A> 方法之前，將登出程式碼直接加入 `SaveSettings` 方法以測試這個事件處理常式。 下一節將說明您可以使用的登出程式碼。  
  
     [!code-csharp[ClientApplicationServices#090](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#090)]
     [!code-vb[ClientApplicationServices#090](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#090)]  
  
14. 如果是使用 C\#，請將下列程式碼加入 `Form1_Load` 方法的結尾。 這段程式碼會將在上一個步驟中加入的方法與 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider.SettingsSaved> 事件產生關聯。  
  
     [!code-csharp[ClientApplicationServices#015](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#015)]  
  
 此時若要測試應用程式，請同時使用 employee 和 manager 身分執行數次，並在文字方塊中輸入不同的值。 這些值會保存在每個使用者的工作階段中。  
  
## 實作登出  
 如果使用者在登入時選取 \[記住我\] 核取方塊，應用程式在後續執行時會自動驗證使用者。 當應用程式在離線模式時，自動驗證仍然會繼續執行直到驗證 Cookie 過期為止。 不過，有時候多個使用者會需要同時存取應用程式，或是單一使用者可能會偶爾使用不同的認證登入。 若要實現這類案例，您必須實作登出功能，如同下列程序所述。  
  
#### 實作登出功能  
  
1.  在 Form1 設計工具中，從 \[工具箱\] 將 <xref:System.Windows.Forms.Button> 控制項加入表單。  
  
2.  在 \[屬性\] 視窗中，將 \[\(名稱\)\] 值指定為 `logoutButton`，並將 \[文字\] 值指定為 **登出\(&L\)**。  
  
3.  按兩下 `logoutButton`，以產生 <xref:System.Windows.Forms.Control.Click> 事件處理常式。  
  
     程式碼編輯器隨即出現，並將游標置於 `logoutButton_Click` 方法中。  
  
4.  以下列程式碼取代所產生的 `logoutButton_Click` 方法。  
  
     這個事件處理常式會先呼叫在上一節中加入的 `SaveSettings` 方法。 接著，事件處理常式會呼叫 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A?displayProperty=fullName> 方法。 如果驗證服務無法使用，<xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider.Logout%2A> 方法會擲回 <xref:System.Net.WebException>。 在這種情況下，`logoutButton_Click` 方法會顯示警告訊息，並暫時切換至離線模式將使用者登出。 下一節將說明離線模式。  
  
     登出會刪除本機驗證 Cookie，因此當重新啟動應用程式時就需要登入。 在登出後，事件處理常式會重新啟動應用程式。 應用程式重新啟動時，會在歡迎訊息後顯示 \[登入\] 對話方塊。 歡迎訊息清楚表示應用程式已重新啟動。 如果使用者必須登入才能儲存設定，而且之後由於應用程式重新啟動又必須再登入一次，歡迎訊息可避免可能發生的混淆情況。  
  
     [!code-csharp[ClientApplicationServices#070](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#070)]
     [!code-vb[ClientApplicationServices#070](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#070)]  
  
 若要測試登出功能，請執行應用程式，然後在 \[登入\] 對話方塊中選取 \[記住我\]。 接著，關閉再重新啟動應用程式以確認不再需要登入。 最後，按一下 \[登出\] 重新啟動應用程式。  
  
## 啟用離線模式  
 在下列程序中，您會將核取方塊加入表單，讓使用者能夠進入離線模式。 您的應用程式可透過將 `static`<xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A?displayProperty=fullName> 屬性設定為 `true` 來進入離線模式。 離線狀態會儲存在 <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=fullName> 屬性所表示的本機硬碟位置。 這表示離線狀態是以個別使用者和個別應用程式為基礎來儲存。  
  
 在離線模式中，所有用戶端應用程式服務要求會從本機快取擷取資料，而不是嘗試存取服務。 在預設組態中，本機資料包含以加密格式儲存的使用者密碼。 這可讓使用者在應用程式處於離線模式時仍能登入。 如需詳細資訊，請參閱[如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)。  
  
#### 在應用程式中啟用離線模式  
  
1.  在 \[方案總管\] 中，選取 ClientAppServicesDemo 專案中的 Form1，然後從 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 主功能表選取 \[檢視 &#124; 設計工具\]。  
  
2.  在設計工具中，將 <xref:System.Windows.Forms.CheckBox> 控制項加入表單。  
  
3.  在 \[屬性\] 視窗中，將 \[\(名稱\)\] 值指定為 `workOfflineCheckBox`，並將 \[文字\] 值指定為 **離線工作\(&W\)**。  
  
4.  在 \[屬性\] 視窗中，按一下 \[事件\] 按鈕。  
  
5.  選取 <xref:System.Windows.Forms.CheckBox.CheckedChanged> 事件，然後按 ENTER 鍵產生事件處理常式。  
  
6.  以下列程式碼取代所產生的方法。  
  
     這段程式碼會更新 <xref:System.Web.ClientServices.ConnectivityStatus.IsOffline%2A> 值，然後在返回線上模式時以無訊息模式重新驗證使用者。<xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A?displayProperty=fullName> 方法會使用快取認證，因此使用者不需要明確地登入。 如果驗證服務無法使用，就會出現警告訊息，而應用程式仍然保持離線狀態。  
  
    > [!NOTE]
    >  <xref:System.Web.ClientServices.ClientFormsIdentity.RevalidateUser%2A> 方法只是為了方便而使用。 因為它沒有傳回值，所以無法表示重新驗證是否失敗。 例如，如果在伺服器上的使用者認證已變更，重新驗證就可能會失敗。 在這種情況下，您可能想要加入在服務呼叫失敗之後能夠明確驗證使用者的程式碼。 如需詳細資訊，請參閱本逐步解說稍早的＜存取 Web 設定＞一節。  
  
     重新驗證後，這段程式碼會呼叫先前加入的 `SaveSettings` 方法，以儲存對本機 Web 設定所做的任何變更。 然後呼叫專案 `Settings` 類別 \(在 C\# 中當做 `Properties.Settings.Default` 存取，而在 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 中則當做 `My.Settings` 存取\) 的 <xref:System.Configuration.ApplicationSettingsBase.Reload%2A> 方法，擷取伺服器上任何新增的值。  
  
     [!code-csharp[ClientApplicationServices#080](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#080)]
     [!code-vb[ClientApplicationServices#080](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#080)]  
  
7.  將下列程式碼加入 `Form1_Load` 方法的結尾，以確定核取方塊會顯示目前的連接狀態。  
  
     [!code-csharp[ClientApplicationServices#014](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Form1.cs#014)]
     [!code-vb[ClientApplicationServices#014](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Form1.vb#014)]  
  
 如此即完成範例應用程式。 若要測試離線功能，請執行應用程式，以 employee 或 manager 的身分登入，然後選取 \[離線工作\]。 修改文字方塊中的值，然後關閉應用程式。 重新啟動應用程式。 登入前，以滑鼠右鍵按一下工作列上通知區域中的 ASP.NET 程式開發伺服器圖示，然後按一下 \[停止\]。 接著以正常的方式登入。 即使伺服器不在執行中，您仍然可以登入。 修改文字方塊的值、結束，然後再重新啟動，以查看修改過的值。  
  
## 摘要  
 在本逐步解說中，您已了解如何在 Windows Form 應用程式中啟用及使用用戶端應用程式服務。 設定測試伺服器之後，您可以將程式碼加入應用程式以驗證使用者，並從伺服器擷取使用者角色和應用程式設定。 您也了解如何啟用離線模式，以便讓應用程式在無法連接時，使用本機資料快取而不是遠端服務。  
  
## 後續步驟  
 在真實世界應用程式中，您會從遠端伺服器存取許多使用者的資料，而遠端伺服器並非隨時都能使用，或是可能會在未告知的情況下離線。 為了讓應用程式更強固，您必須能夠適當地回應服務無法使用的各種情況。 本逐步解說包含 try\/catch 區塊，可攔截 <xref:System.Net.WebException>，並在服務無法使用時顯示錯誤訊息。 在實際執行的程式碼中，您可能想要藉由切換至離線模式、結束應用程式，或拒絕存取特定功能的方式處理這種情況。  
  
 為了加強應用程式的安全性，請務必在部署前徹底測試應用程式和伺服器。  
  
## 請參閱  
 [用戶端應用程式服務](../../../docs/framework/common-client-technologies/client-application-services.md)   
 [用戶端應用程式服務概觀](../../../docs/framework/common-client-technologies/client-application-services-overview.md)   
 [如何：設定用戶端應用程式服務](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)   
 [ASP.NET Web Site Administration Tool](../Topic/ASP.NET%20Web%20Site%20Administration%20Tool.md)   
 [Creating and Configuring the Application Services Database for SQL Server](../Topic/Creating%20and%20Configuring%20the%20Application%20Services%20Database%20for%20SQL%20Server.md)   
 [Walkthrough: Using ASP.NET Application Services](../Topic/Walkthrough:%20Using%20ASP.NET%20Application%20Services.md)