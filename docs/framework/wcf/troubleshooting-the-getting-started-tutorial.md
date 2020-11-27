---
title: 針對 Windows Communication Foundation 入門教學課程進行疑難排解
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 4d471372419996c5bc490c2d0fdd83927428a41e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281335"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>針對 Windows Communication Foundation 入門教學課程進行疑難排解

本文提供當您遵循教學課程中的步驟 [：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)時，可能會遇到的最常見問題和錯誤的解決方案。
  
## <a name="common-problems"></a>常見問題

**我在硬碟上找不到專案檔案。**

 Visual Studio 會將專案檔案儲存在 *C:\Users \\ &lt; 使用者名稱 &gt; \source\repos* 中。  

**我找不到 *Svcutil.exe* 所產生的 *App.config* 檔案。**

 在 Visual Studio 中，[ **加入現有專案** ] 視窗預設只會顯示具有下列副檔名的檔案：

- *.cs*
- *.resx*
- *。設定*
- *.xsd*
- *.wsdl*

若要顯示所有檔案類型，請在 [**加入現有專案**] 視窗右下角的下拉式清單中，選取 [所有檔案] **(\* . \*) 。**  
  
## <a name="common-errors"></a>常見錯誤

### <a name="compile-the-service-application"></a>編譯服務應用程式

**在 ' GettingStartedHost ' 中找不到 ' Sub Main ' 的錯誤 BC30420。**

Visual Basic 應用程式的進入點不正確。 進行下列變更：

   1. 在 [ **方案總管** ] 視窗中，選取 [ **GettingStartedHost** ] 資料夾，然後從快捷方式功能表選取 [ **屬性** ]。
    a. 在 [ **GettingStartedHost** ] 視窗中，針對 [ **啟始物件**]，從清單中選取 [ **服務** ] (或特定應用程式) 的進入點。
    b. 從主功能表中 **，選取 [**  >  **全部儲存**]。

### <a name="run-the-service-application"></a>執行服務應用程式

**HTTP 無法註冊 URL ' HTTP： \/ /+： 8000/GettingStarted/CalculatorService '。您的進程沒有此命名空間的存取權限。**

 如需適當的存取權，請使用系統管理許可權啟動裝載 Windows Communication Foundation (WCF) 服務的進程：

- 針對 Visual Studio：選取 [**開始**] 功能表中的 [Visual Studio] 程式，然後從快捷方式功能表 **選取 [以**  >  **系統管理員身分執行**]。
- 在主控台視窗中：選取 [**開始**] 功能表中的 [**命令提示** 字元]，然後從快捷方式功能表 **選取 [以**  >  **系統管理員身分執行**]。
- 針對 Windows 檔案總管：選取可執行檔，然後從快捷方式功能表選取 [以 **系統管理員身分執行** ]。

### <a name="compile-the-client-application"></a>編譯用戶端應用程式

**' CalculatorClient ' 不包含 ' ' 的定義， \<method name> 而且找不到任何擴充方法 ' \<method name> ' 接受類型 ' CalculatorClient ' 的第一個引數 (您是否遺漏 using 指示詞或元件參考？ )**  

只有您以屬性標示的方法 `ServiceOperationAttribute` 會公開公開。 如果您 `ServiceOperationAttribute` 從介面中的方法省略屬性 `ICalculator` ，您會在編譯期間收到此錯誤訊息。  

**找不到類型或命名空間名稱 ' CalculatorClient ' (您是否遺漏 using 指示詞或元件參考？ )**

 如果您在使用 *Svcutil.exe* 工具產生 *generatedProxy.cs* (或) *generatedProxy* 檔案至用戶端專案時未將該檔案新增至用戶端專案，就會收到這個錯誤。  

### <a name="run-the-client-application"></a>執行用戶端應用程式

**未處理的例外狀況： System.servicemodel. EndpointNotFoundException：無法連接到 ' HTTP： \/ /localhost： 8000/GettingStarted/CalculatorService '。TCP 錯誤碼10061：無法建立連接，因為目的電腦主動拒絕連線。**

如果您在未先啟動服務的情況下執行用戶端應用程式，就會發生這個錯誤。 首先，執行主機應用程式來啟動服務，然後執行用戶端應用程式。

### <a name="use-the-svcutilexe-tool"></a>使用 Svcutil.exe 工具

**' Svcutil ' 無法辨識為內部或外部命令、可操作的程式或批次檔。**

 *Svcutil.exe* 必須在系統路徑中。 最簡單的解決方案是使用 Visual Studio 命令提示字元。 從 [**開始**] 功能表選取 **\<version> Visual Studio** 目錄，然後選取 [ **VS \<version> ] 開發人員命令提示字元**。 此命令提示字元會將系統路徑設定為 Visual Studio 中隨附之所有工具的正確位置。  
  
### <a name="run-the-service-and-client-applications"></a>執行服務和用戶端應用程式

**System.servicemodel.security.securitynegotiationexception： \/ 對目標 ' HTTP： \/ /localhost： 8000/GettingStarted/CalculatorService ' 使用 ' HTTP：/localhost： 8000/GettingStarted/CalculatorService ' 的 SOAP 安全性協商失敗**  

當加入網域的電腦沒有網路連線時，就會發生此錯誤。 將您的電腦連接到網路，或關閉服務和用戶端的安全性。

若要關閉安全性：

- 針對服務，以下列程式碼取代建立的程式碼 `WSHttpBinding` ：  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- 若為用戶端，請在設定檔中更新元素底下的專案，如下所示 **\<security>** **\<binding>** ：  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator">
      <security mode="None" />
    </binding
    ```  

## <a name="see-also"></a>另請參閱  

 [WCF 應用程式入門](getting-started-tutorial.md)  
 [WCF 疑難排解快速入門](wcf-troubleshooting-quickstart.md)  
 [針對安裝問題進行疑難排解](troubleshooting-setup-issues.md)
