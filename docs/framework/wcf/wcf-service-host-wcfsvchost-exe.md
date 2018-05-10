---
title: WCF 服務主機 (WcfSvcHost.exe)
ms.date: 03/30/2017
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
ms.openlocfilehash: e1e258015adc34edd4a109f3bc5a32b4bf6f0296
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-service-host-wcfsvchostexe"></a>WCF 服務主機 (WcfSvcHost.exe)
Windows Communication Foundation (WCF) 服務主機 (WcfSvcHost.exe) 可讓您啟動 Visual Studio 偵錯工具 (F5) 來自動裝載並測試您已實作的服務。 然後，您可以測試服務使用 WCF 測試用戶端 (WcfTestClient.exe) 或您自己的用戶端中，尋找並修正任何可能的錯誤。  
  
## <a name="wcf-service-host"></a>WCF 服務主機  
 WCF 服務主機會列舉 WCF 服務專案中的服務、 載入專案的設定，並具現化每個服務所找到的主機。 此工具透過 WCF 服務範本整合至 Visual Studio，並在開始偵錯您的專案時叫用。  
  
 使用 WCF 服務主機，您可以不需要撰寫額外的程式碼或認可特定主機在開發期間裝載 WCF 服務 （在 WCF 服務程式庫專案中）。  
  
> [!NOTE]
>  WCF 服務主機不支援部分信任。 如果您想要在部分信任中使用 WCF 服務，請勿 WCF 服務程式庫專案範本在 Visual Studio 中建置您的服務。 選擇 WCF 服務網站範本，其可裝載的 web 伺服器支援 WCF 部分信任中的服務，相反地，在 Visual Studio 中建立新的網站。  
  
## <a name="project-types-hosted-by-wcf-service-host"></a>WCF 服務主機裝載的專案類型  
 WCF 服務主機可以裝載 WCF 服務程式庫專案類型： WCF 服務程式庫、 循序工作流程服務程式庫、 狀態機器工作流程服務程式庫和新聞訂閱服務程式庫。 WCF 服務主機也可以裝載這些服務，可以加入至服務程式庫的專案使用**加入項目**功能。 這包括 WCF 服務、 WF 狀態機器服務、 WF 循序服務、 XAML WF 狀態機器服務和 XAML WF 循序服務。  
  
 但是，您應該注意到，此工具無法協助您設定主機。 對於這項工作，您必須手動編輯 App.config 檔案。 此工具也不會驗證使用者定義的組態檔。  
  
> [!CAUTION]
>  您不應該使用在實際執行環境中，裝載服務的 WCF 服務主機，因為它不工程針對此目的。  WCF 服務主機不支援可靠性、 安全性和管理便利性需求，這類環境。 請改用 IIS，因為它提供比較好的可靠性和監視功能，而且是一般慣用於裝載服務的解決方案。 開發您的服務完成之後，您應該將服務移轉至 IIS 的 WCF 服務主機。  
  
## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>在 Visual Studio 內使用 WCF 服務主機的案例  
 下表列出中的所有參數**命令列引數**對話方塊中，以滑鼠右鍵按一下您的專案中可以找到**方案總管 中**在 Visual Studio 中，選取**屬性**，然後選取**偵錯** 索引標籤，然後按一下**起始專案**。 這些參數可用於設定 WCF 服務主機。  
  
|參數|意義|  
|---------------|-------------|  
|`/client`|選擇性參數，會指定要在裝載服務後執行之可執行檔的路徑。 這會啟動 WCF 測試用戶端裝載之後。|  
|`/clientArg`|會指定字串做為傳遞給自訂用戶端應用程式的引數。|  
|`/?`|顯示說明文字。|  
  
#### <a name="using-wcf-test-client"></a>使用 WCF 測試用戶端  
 建立新的 WCF 服務專案後，當您按 f5 鍵啟動偵錯工具時，WCF 服務主機就會啟動裝載在您的專案中找到的所有服務。 WCF 測試用戶端會自動開啟，並顯示組態檔中定義的服務端點的清單。 您可以從主視窗中測試參數並叫用服務。  
  
 若要確定使用 WCF 測試用戶端，以滑鼠右鍵按一下您的專案中**方案總管 中**在 Visual Studio 中，選取**屬性**，然後選取**偵錯** 索引標籤。按一下**起始專案**，並確定下列項目出現在**命令列引數** 對話方塊。  
  
 `/client:WcfTestClient.exe`  
  
#### <a name="using-a-custom-client"></a>使用自訂用戶端  
 若要使用自訂用戶端，以滑鼠右鍵按一下您的專案中**方案總管 中**在 Visual Studio 中，選取**屬性**，然後選取**偵錯** 索引標籤。按一下**起始專案**和編輯`/client`中的參數**命令列引數**對話方塊中，以指向自訂的用戶端，如下列範例所示。  
  
 `/client:"path/CustomClient.exe"`  
  
 當您按 F5 以重新啟動該服務時，WCF 服務主機在您啟動偵錯工具時自動啟動自訂用戶端。  
  
 您也可以使用 `/clientArg:` 參數，指定字串做為傳遞給自訂用戶端應用程式的引數，如下列範例所示。  
  
 `/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`  
  
 例如，如果您使用新聞訂閱服務程式庫範本，就可以使用下列命令列引數：  
  
 `/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`  
  
#### <a name="specifying-no-client"></a>不指定任何用戶端  
 若要指定裝載 WCF 服務之後，會使用任何用戶端，以滑鼠右鍵按一下您的專案中**方案總管 中**在 Visual Studio 中，選取**屬性**，然後選取**偵錯**  索引標籤。按一下**起始專案**留下**命令列引數**對話方塊保留空白。  
  
#### <a name="using-a-custom-host"></a>使用自訂主機  
 若要使用自訂主機，以滑鼠右鍵按一下您的專案中**方案總管 中**在 Visual Studio 中，選取**屬性**，然後選取**偵錯** 索引標籤。按一下**起始外部程式**和輸入自訂主應用程式的完整路徑。 您也可以使用**命令列引數**對話方塊來指定要傳遞給主機的引數。  
  
## <a name="wcf-service-host-user-interface"></a>WCF 服務主機使用者介面  
 當您初次叫用 WCF 服務主機 （藉由按下 F5，在 Visual Studio 內，） **WCF 服務主機**視窗會自動開啟。 當執行 WCF 服務主機時，程式的圖示會出現在通知區域中。 按兩下圖示以開啟**WCF 服務主機**視窗  
  
 在服務裝載期間發生錯誤，就會開啟 WCF 服務主控件 對話方塊，以顯示相關資訊。  
  
 **WCF 服務主機**主視窗包含兩個功能表：  
  
-   **檔案**： 包含**關閉**和**結束**命令。 當您按一下**關閉**、 **WCF 服務主機**對話框會關閉，但會繼續裝載服務。 當您按一下**結束**，WCF 服務主機也會關閉。 這還會停止所有裝載的服務。  
  
-   **協助**： 包含**有關**命令，以包含版本資訊。 它也包含**協助**可以開啟說明檔案的命令。  
  
 主要**WCF 服務主機**視窗包含兩個區域：  
  
-   第一個區域是**服務**。 其中包含一份顯示所有服務基本資訊的清單。 這些資訊包括：  
  
    -   **服務**： 列出所有服務。  
  
    -   **狀態**： 列出服務的狀態。 有效值為 「 已啟動 」、 「 已停止 」 和 「 錯誤 」。  
  
    -   **中繼資料位址**： 顯示服務的中繼資料位址。  
  
-   第二個區域是**更多資訊**。 它會顯示服務狀態的詳細的說明 中選取特定服務行時**服務**區域。 如果狀態為「錯誤」，您就可以在螢幕上檢視完整的錯誤訊息。  
  
## <a name="stopping-wcf-service-host"></a>停止 WCF 服務主機  
 您可以關閉 WCF 服務主機，以下列四種方式：  
  
-   停止 Visual Studio 中的偵錯工作階段。  
  
-   選取**結束**從**檔案**功能表**WCF 服務主機**視窗。  
  
-   選取**結束**從系統通知區域中的 WCF 服務主機匣圖示的操作功能表。  
  
-   如果正在使用它，請結束 WCF 測試用戶端。  
  
## <a name="using-service-host-without-administrator-privilege"></a>在沒有系統管理員權限的情況下使用服務主機  
 若要啟用開發 WCF 服務的使用者沒有系統管理員權限，建立命名空間的 ACL （存取控制清單） 」http://+:8731/Design_Time_Addresses"Visual Studio 安裝期間。 ACL 會設定為 (UI)，其中包含已登入電腦的所有互動使用者。 系統管理員可以新增或移除使用者，從這個 ACL 中，或開啟其他連接埠。這個 ACL 可讓使用者使用 WCF 服務自動主機 (wcfSvcHost.exe)，但不授與這些系統管理員權限。  
  
 您可以在有更高權限的系統管理員帳戶下，使用 [!INCLUDE[wv](../../../includes/wv-md.md)] 中的 netsh.exe 工具來修改存取權。 下列是使用 netsh.exe 的範例。  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 如需有關 netsh.exe 的詳細資訊，請參閱 「[如何使用 Netsh.exe 工具和命令列參數](http://go.microsoft.com/fwlink/?LinkId=97877)"。  
  
## <a name="see-also"></a>另請參閱  
 [WCF 測試用戶端 (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
