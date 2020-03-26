---
title: 使用 Windows 通信基礎教程對入門進行故障排除
ms.date: 01/25/2019
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 73aa0f5784784cb788a7532f8e22cbe925429c41
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249613"
---
# <a name="troubleshoot-the-get-started-with-windows-communication-foundation-tutorials"></a>使用 Windows 通信基礎教程對入門進行故障排除

本文提供了解決方案，解決在按照[教程中的步驟：開始使用 Windows 通信基礎應用程式](getting-started-tutorial.md)時可能面臨的最常見問題和錯誤。
  
## <a name="common-problems"></a>常見問題

**我在硬碟上找不到專案檔案。**

 Visual Studio 將專案檔案保存在*C：\使用者\\&lt;使用者名&gt;[源]存儲庫*中。  

**我找不到*Svcutil.exe*生成的*App.config*檔。**

 在 Visual Studio 中，"**添加現有專案"** 視窗預設僅顯示具有以下副檔名的檔：

- *.cs*
- *.resx*
- *.設置*
- *.xsd*
- *.wsdl*

要顯示所有檔案類型，請在 **"添加現有專案**"視窗右下角的下拉清單中選擇 **"所有檔 "（.）。\* \* **  
  
## <a name="common-errors"></a>常見錯誤

### <a name="compile-the-service-application"></a>編譯服務應用程式

**在"入門主機.模組1"中未找到錯誤 BC30420"子主"。**

對於視覺化基本應用程式，進入點不正確。 進行以下更改：

   1. 在 **"解決方案資源管理器"** 視窗中，選擇 **"入門主機"** 資料夾，然後從快顯功能表中選擇 **"屬性**"。
    a. 在 **"入門主機"** 視窗中，對於**啟始物件**，從清單中選擇 **"服務.程式**"（或特定應用程式的進入點）。
    b. 從主功能表中，選擇 **"全部保存檔** > **Save All**"。

### <a name="run-the-service-application"></a>運行服務應用程式

**HTTP 無法註冊 URL "HTTP：\//：8000/入門/計算機服務"。您的進程沒有對此命名空間的存取權限。**

 要獲得適當的存取權限，可以啟動託管具有管理許可權的 Windows 通信基礎 （WCF） 服務的過程：

- 對於視覺化工作室：在 **"開始"** 功能表中選擇"視覺工作室"程式，然後從快顯功能表中選擇 **"以管理員** > **身份運行**更多"。
- 對於主控台視窗：在 **"開始"** 功能表中選擇 **"命令提示"，** 然後從快顯功能表中選擇 **"以** > **管理員身份運行**更多"。
- 對於 Windows 資源管理器：選擇可執行檔，然後從快顯功能表中選擇 **"以管理員身份運行**"。

### <a name="compile-the-client-application"></a>編譯用戶端應用程式

**"計算機用戶端"，不包含"方法名稱>"\<的定義，並且找不到接受類型為"計算機用戶端\<"的第一個參數的擴充方法"方法名稱>"（您是否缺少使用指令或程式集引用？**  

只有使用`ServiceOperationAttribute`屬性標記的方法才會公開。 如果在`ICalculator`介面中的方法省略`ServiceOperationAttribute`該屬性，則會在編譯期間收到此錯誤訊息。  

**找不到類型或命名空間名稱"計算機用戶端"（您是否缺少 using 指令或程式集引用？**

 如果在使用*Svcutil.exe*工具生成*generatedProxy.cs（* 或*生成的Proxy.vb）* 檔時，未將這些檔添加到用戶端專案中，則收到此錯誤。  

### <a name="run-the-client-application"></a>運行用戶端應用程式

**未處理異常：系統.服務模型.終結點未找到異常：無法連接到"HTTP：/\/本地主機：8000/入門/計算機服務"。TCP 錯誤代碼 10061：由於目的電腦主動拒絕，因此無法進行連接。**

如果在未初次開機服務的情況下運行用戶端應用程式，則會發生此錯誤。 首先，運行主機應用程式以啟動服務，然後運行用戶端應用程式。

### <a name="use-the-svcutilexe-tool"></a>使用 Svcutil.exe 工具

**"Svcutil"不被識別為內部或外部命令、可操作程式或批次檔。**

 *Svcutil.exe*必須位於系統路徑中。 最簡單的解決方案是使用 Visual Studio 命令提示符。 在 **"開始"** 功能表中，選擇 **"\<視覺工作室"版本>** 目錄，然後選擇 **"開發人員\<命令提示">。** 此命令提示符將系統路徑設置到作為 Visual Studio 一部分提供的所有工具的正確位置。  
  
### <a name="run-the-service-and-client-applications"></a>運行服務和用戶端應用程式

**系統.服務模型.安全.安全協商例外：SOAP 安全協商與目標的"HTTP：/localhost：8000/\/入門/計算機服務"的目標"HTTP：/localhost：8000/\/入門/計算機服務"失敗**  

此錯誤發生在沒有網路連接的域加入電腦上。 將電腦連接到網路或關閉服務和用戶端的安全性。

要關閉安全性：

- 對於服務，用以下代碼替換創建`WSHttpBinding`的代碼：  
  
    ```csharp
    // Step 3: Add a service endpoint.
    selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
    ```

- 對於用戶端，在設定檔中，在**\<綁定>** 元素下更新**\<安全>** 元素，如下所示：  
  
    ```xml
    <binding name="WSHttpBinding_ICalculator">
      <security mode="None" />
    </binding
    ```  

## <a name="see-also"></a>另請參閱  
 [開始使用 WCF 應用程式](getting-started-tutorial.md)  
 [WCF 故障排除快速入門](wcf-troubleshooting-quickstart.md)  
 [排除設置問題](troubleshooting-setup-issues.md)
