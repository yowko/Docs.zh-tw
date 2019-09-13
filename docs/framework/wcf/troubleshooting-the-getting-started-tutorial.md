---
title: Windows Communication Foundation 教學課程入門疑難排解
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 10a2f8f718d802a7aab067b882f0d5cf3dc28dca
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928571"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>Windows Communication Foundation 教學課程入門疑難排解

本文提供您在遵循[教學課程中的步驟時可能面臨的最常見問題和錯誤的解決方案：Windows Communication Foundation 應用程式](getting-started-tutorial.md)入門。 
  
## <a name="common-problems"></a>常見問題

**我在硬碟上找不到專案檔。**

 Visual Studio 會將專案檔儲存在 *\\C:\Users&gt; &lt;使用者名稱 \source\repos*中。  

**我找不到*Svcutil* *產生的 app.config*檔案。**

 在 Visual Studio 中，[**加入現有專案**] 視窗預設只會顯示具有下列副檔名的檔案： 

- *.cs* 
- *.resx* 
- *.settings*
- *.xsd* 
- *.wsdl*

若要顯示所有檔案類型，請選取 **的所有檔案 (\*。\*)** 右下角的下拉式清單中**加入現有項目**視窗。  
  
## <a name="common-errors"></a>常見的錯誤

### <a name="compile-the-service-application"></a>編譯服務應用程式 

**在 ' GettingStartedHost ' 中找不到錯誤 BC30420 ' Sub Main '。**

Visual Basic 應用程式的進入點不正確。 進行下列變更：

   1. 在 [**方案總管**] 視窗中，選取 [ **GettingStartedHost** ] 資料夾，然後從快捷方式功能表選取 [**屬性**]。
    a. 在 [ **GettingStartedHost** ] 視窗中，針對 [**啟始物件**]，從清單中選取 [**服務**] （或特定應用程式的進入點）。 
    b. 從主功能表中 **，選取** > [檔案] [**全部儲存**]。

### <a name="run-the-service-application"></a>執行服務應用程式 

**Http 無法註冊 URL ' HTTP：\//+： 8000/GettingStarted/CalculatorService '。您的處理程序沒有足夠的存取權可存取此命名空間。** 

 如需適當的存取權，請使用系統管理許可權啟動主控 Windows Communication Foundation （WCF）服務的進程：

- 針對 Visual Studio：在 [**開始**] 功能表中選取 [Visual Studio] 程式，然後從快捷方式功能表選取 [**更多** > **以系統管理員身分執行**]。
- 主控台視窗：在 [**開始**] 功能表中選取 [**命令提示**字元]，然後從快捷方式功能表選取 [**更多** > 以**系統管理員身分執行**]。
- 若為 Windows Explorer：選取可執行檔，然後從快捷方式功能表選取 [**以系統管理員身分執行**]。

### <a name="compile-the-client-application"></a>編譯用戶端應用程式

**' CalculatorClient ' 未包含 '\<method name > ' 的定義，而且找不到擴充\<方法的方法名稱 > ' 接受 ' CalculatorClient ' 類型的第一個引數（您是否遺漏 using 指示詞或元件參考？）**  

只有使用`ServiceOperationAttribute`屬性標記的方法才會公開。 如果您從`ICalculator`介面`ServiceOperationAttribute`中的方法省略屬性，在編譯期間就會收到這個錯誤訊息。  

**找不到類型或命名空間名稱 ' CalculatorClient ' （您是否遺漏 using 指示詞或元件參考？）**

 如果您在使用*Svcutil*來產生用戶端專案時，未將*GeneratedProxy.cs* （或*generatedProxy*）檔案新增至該檔案，就會收到這個錯誤。  

### <a name="run-the-client-application"></a>執行用戶端應用程式

**未處理的例外狀況：System.ServiceModel.EndpointNotFoundException:無法連接到 ' HTTP：\//localhost： 8000/GettingStarted/CalculatorService '。TCP 錯誤碼10061：無法連線，因為目的電腦主動拒絕該連接。**

如果您在未先啟動服務的情況下執行用戶端應用程式，就會發生這個錯誤。 首先，執行主應用程式以啟動服務，然後執行用戶端應用程式。

### <a name="use-the-svcutilexe-tool"></a>使用 Svcutil 工具
   
**' Svcutil ' 未辨識為內部或外部命令、可運作的程式或批次檔。**

 *Svcutil*必須位於系統路徑中。 最簡單的解決方案是使用 Visual Studio 命令提示字元。 從 [**開始**] 功能表中，**選取\<Visual Studio 版本 >** 目錄，然後選取 [**開發人員命令提示字元\<以取得 VS 版本 >** ]。 此命令提示字元會將系統路徑設為 Visual Studio 中隨附之所有工具的正確位置。  
  
### <a name="run-the-service-and-client-applications"></a>執行服務和用戶端應用程式

**System.ServiceModel.Security.SecurityNegotiationException:目標 ' HTTP：\/ \//localhost： 8000/GettingStarted/CalculatorService ' 的 SOAP 安全性協調與 ' HTTP：/localhost： 8000/GettingStarted/CalculatorService ' 失敗**  

如果加入網域的電腦沒有網路連線，就會發生此錯誤。 將您的電腦連線到網路，或關閉服務和用戶端的安全性。 

若要關閉安全性：

- 針對服務，請將建立的`WSHttpBinding`程式碼取代為下列程式碼：  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- 用戶端組態檔中，更新 **\<安全性>** 項目底下 **\<繫結>** 項目，如下所示：  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator" security mode="None" />
    ```  

## <a name="see-also"></a>另請參閱  
 [WCF 應用程式入門](getting-started-tutorial.md)  
 [WCF 疑難排解快速入門](wcf-troubleshooting-quickstart.md)  
 [疑難排解安裝程式問題](troubleshooting-setup-issues.md)
