---
title: 使用者入門教學課程疑難排解
ms.date: 03/30/2017
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 43128743ba16aefc8669ace85070a16d80145a71
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519417"
---
# <a name="troubleshooting-the-getting-started-tutorial"></a>使用者入門教學課程疑難排解
本主題列出在進行使用者入門教學課程時遇到的最常見問題，以及如何解決這些問題的方式。  
  
**我找不到我的硬碟機上的專案檔。**

 Visual Studio 將專案檔儲存在 c:\users\\<user name>\Documents\\< Visual Studio 版本\>\Projects。  
  
**嘗試執行服務應用程式： HTTP 無法登錄 URL `http://+:8000/ServiceModelSamples/Service/`。**
**您的程序並沒有此命名空間的存取權限。** 

 裝載 WCF 服務的處理序必須以系統管理權限執行。 如果您正在執行的服務從在 Visual Studio 中，您必須執行 Visual Studio 系統管理員身分。 若要這樣做，因此按一下**開始**，以滑鼠右鍵按一下**Visual Studio \<*版本*>**  ，然後選取**系統管理員身分執行**. 如果您從命令列提示字元主控台視窗中執行服務，您必須以系統管理員身分啟動主控台視窗，類似的方式。 按一下 **開始**，以滑鼠右鍵按一下**命令提示字元**，然後選取**系統管理員身分執行**。  
  
**嘗試使用 Svcutil.exe 工具: 'svcutil' 不視為內部或外部命令、 可執行程式或批次檔。**

 Svcutil.exe 必須位於系統路徑。 最簡單的解決方式是使用命令提示字元。 按一下 **開始**，選取**所有程式**， **Visual Studio \<*版本*>**， **Visual Studio Tools**，並**Visual Studio 的開發人員命令提示字元**。 這個命令提示字元設定的系統路徑設為正確的位置，隨附於 Visual Studio 的所有工具。  

**找不到 Svcutil.exe 所產生的 App.config 檔案。**

 **加入現有項目**對話方塊預設只顯示具有下列副檔名的檔案：.cs、.resx、.settings、.xsd、.wsdl。 您可以指定您想要檢視選取的所有檔案類型**的所有檔案 (\*。\*)** 中的下拉式清單方塊中的右下角**加入現有項目** 對話方塊。  


**編譯用戶端應用程式: 'CalculatorClient' 不包含的定義 '\<方法名稱 >' 並不到擴充方法'\<方法名稱 >' 接受型別 'CalculatorClient' 的第一個引數。 找不到 （嗎是否遺漏 using 指示詞或組件參考？)**  

只有已使用 `ServiceOperationAttribute` 標示的方法才會向外界公開。 如果您省略`ServiceOperationAttribute`屬性中的方法的其中一個`ICalculator`介面，您收到這個錯誤訊息會遺漏屬性的作業呼叫用戶端應用程式在編譯時。  

**編譯用戶端應用程式： 找不到 'CalculatorClient' 的類型或命名空間名稱 (您是否遺漏 using 指示詞或組件參考？)**

 如果您未將 Proxy.cs 或 Proxy.vb 檔案加入至用戶端專案，就會發生這個錯誤。  

**執行用戶端： 未處理例外狀況： System.ServiceModel.EndpointNotFoundException： 無法連接到`http://localhost:8000/ServiceModelSamples/Service/CalculatorService`。TCP 錯誤碼 10061： 無法建立任何連線，因為目標電腦主動拒絕它。**

如果執行用戶端應用程式但未執行服務，就會發生這個錯誤。  
  
**未處理的例外狀況： System.ServiceModel.Security.SecurityNegotiationException： 與 SOAP 安全性交涉`http://localhost:8000/ServiceModelSamples/Service/CalculatorService`目標`http://localhost:8000/ServiceModelSamples/Service/CalculatorService`失敗**  

如果電腦已加入網域卻沒有網路連接，就會發生這個錯誤。 請將您的電腦連接至網路，或是關閉用戶端與服務兩者的安全性。 在服務方面，找出建立 WSHttpBinding 的程式碼並修改為以下內容。  
  
```csharp
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
```

用戶端中，變更**\<安全性 >** 項目底下**\<繫結 >** 如下的項目：  
  
```xml
<security mode="Node" />  
```  

## <a name="see-also"></a>另請參閱  
 [快速入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [WCF 疑難排解快速入門](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)  
 [疑難排解安裝問題](../../../docs/framework/wcf/troubleshooting-setup-issues.md)
