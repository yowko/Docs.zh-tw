---
title: 疑難排解 Get 開始使用 Windows Communication Foundation 教學課程
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 8089e0fee262d07be591069982b1aacfbeae2521
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791465"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>疑難排解 Get 開始使用 Windows Communication Foundation 教學課程

本文提供解決方案的最常見的問題和錯誤，當您遵循的步驟中，您可能會面臨[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。 
  
## <a name="common-problems"></a>常見問題

**我找不到我的硬碟機上的專案檔。**

 Visual Studio 會儲存在專案檔*C:\Users\\&lt;使用者名稱&gt;\source\repos*。  

**我找不到*App.config*所產生的檔案*Svcutil.exe*。**

 在 Visual Studio 中，**加入現有項目**視窗只有預設會顯示具有下列副檔名的檔案： 
- *.cs* 
- *.resx* 
- *.settings*
- *.xsd* 
- *.wsdl*

若要顯示所有檔案類型，請選取 **的所有檔案 (\*。\*)** 右下角的下拉式清單中**加入現有項目**視窗。  
  
## <a name="common-errors"></a>常見的錯誤

### <a name="compile-the-service-application"></a>編譯服務應用程式 

**錯誤 BC30420 'GettingStartedHost.Module1' 中找不到 ' Sub Main'。**

進入點是不正確的 Visual Basic 應用程式。 進行下列變更：

   1. 在 [**方案總管**視窗中，選取**GettingStartedHost**資料夾，然後再選取**屬性**從捷徑功能表。
    a. 在 [ **GettingStartedHost** ] 視窗中，如**啟始物件**，選取**Service.Program** （或特定應用程式的進入點） 從清單。 
    b. 從主功能表中，選取**檔案** > **全部儲存**。

### <a name="run-the-service-application"></a>執行服務應用程式 

**HTTP 無法登錄 URL ' http:\// +: 8000/GettingStarted/CalculatorService '。您的處理程序沒有足夠的存取權可存取此命名空間。** 

 適當的存取，如啟動裝載 Windows Communication Foundation (WCF) 服務，以系統管理權限的處理序：
- Visual studio:選取 [Visual Studio 方案中的**開始**] 功能表，然後選取**詳細** > **系統管理員身分執行**從捷徑功能表。
- 主控台視窗：選取**命令提示字元**中**開始**功能表，然後再選取**詳細** > **系統管理員執行身分**從快顯功能表。
- Windows 檔案總管：選取的可執行檔，然後選取**系統管理員身分執行**從捷徑功能表。

### <a name="compile-the-client-application"></a>編譯用戶端應用程式

**'CalculatorClient'，不會包含定義 '\<方法名稱 >' 並不到擴充方法'\<方法名稱 >' 接受型別找不到 'CalculatorClient' 的第一個引數 (是否遺漏 using 指示詞或組件參考？）**  

只有在您使用標示的方法`ServiceOperationAttribute`公開公開屬性。 如果您省略`ServiceOperationAttribute`屬性中的方法從`ICalculator`介面，您在編譯期間收到此錯誤訊息。  

**找不到 'CalculatorClient' 的類型或命名空間名稱 (您是否遺漏 using 指示詞或組件參考？)**

 您會收到這個錯誤，如果您未新增*generatedProxy.cs* (或*generatedProxy.vb*) 檔案，以用戶端專案，當您產生以*Svcutil.exe*工具.  

### <a name="run-the-client-application"></a>執行用戶端應用程式

**未處理的例外狀況：System.ServiceModel.EndpointNotFoundException:無法連接到 ' http:\//localhost:8000/GettingStarted/CalculatorService '。TCP 錯誤碼 10061:沒有連接，因為目標電腦主動拒絕連線。**

如果您不需要第一個啟動的服務執行用戶端應用程式，就會發生此錯誤。 首先，執行主應用程式啟動服務，然後再執行 [用戶端應用程式。

### <a name="use-the-svcutilexe-tool"></a>使用 Svcutil.exe 工具
   
**'Svcutil' 不視為內部或外部命令、 可執行程式或批次檔。**

 *Svcutil.exe*必須位於系統路徑中。 最簡單的解決方案是使用 Visual Studio 命令提示字元。 從**開始**功能表上，選取**Visual Studio\<版本 >** 目錄，然後選取**VS 開發人員命令提示字元\<版本 >**. 這個命令提示字元設定的系統路徑設為正確的位置，隨附於 Visual Studio 的所有工具。  
  
### <a name="run-the-service-and-client-applications"></a>執行服務和用戶端應用程式

**System.ServiceModel.Security.SecurityNegotiationException:與 SOAP 安全性交涉 'http:\//localhost:8000/GettingStarted/CalculatorService' 的目標 'http:\//localhost:8000/GettingStarted/CalculatorService' 失敗**  

沒有網路連線能力的已加入網域的電腦上，就會發生此錯誤。 將電腦連線到網路，或關閉 [服務和用戶端的安全性。 

若要關閉安全性：

- 對於服務，取代建立的程式碼`WSHttpBinding`為下列程式碼：  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- 用戶端組態檔中，更新 **\<安全性>** 項目底下 **\<繫結>** 項目，如下所示：  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator" security mode="None" />
    ```  

## <a name="see-also"></a>另請參閱  
 [開始使用 WCF 應用程式](getting-started-tutorial.md)  
 [WCF 疑難排解快速入門](wcf-troubleshooting-quickstart.md)  
 [疑難排解安裝問題](troubleshooting-setup-issues.md)
