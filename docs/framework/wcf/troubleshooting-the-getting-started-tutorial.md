---
title: 使用者入門教學課程疑難排解
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d8bc077b1ef24ecfcb4d37a9ddb8389dc705f68e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="troubleshooting-the-getting-started-tutorial"></a>使用者入門教學課程疑難排解
本主題列出在進行使用者入門教學課程時遇到的最常見問題，以及如何解決這些問題的方式。  
  
1.  [我找不到我的硬碟上的專案檔。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q1)  
  
2.  [嘗試執行服務應用程式： HTTP 無法登錄 URL http://+:8000/ServiceModelSamples/Service/。您的處理程序沒有足夠的存取權可存取此命名空間。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q2)  
  
3.  [嘗試使用 Svcutil.exe 工具: 'svcutil' 無法辨識為內部或外部命令、 可執行程式或批次檔。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q3)  
  
4.  [找不到 Svcutil.exe 所產生的 App.config 檔案。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q4)  
  
5.  [編譯用戶端應用程式: 'CalculatorClient' 不包含的定義 '&lt;方法名稱&gt;'和不到擴充方法'&lt;方法名稱&gt;' 來接受型別 'CalculatorClient' 的第一個引數找不到 (您是否遺漏 using 指示詞或組件參考？)](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q5)  
  
6.  [編譯用戶端應用程式： 找不到 'CalculatorClient' 的類型或命名空間名稱 (您是否遺漏 using 指示詞或組件參考？)](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q6)  
  
7.  [執行用戶端： 未處理例外狀況： System.ServiceModel.EndpointNotFoundException： 無法連接到http://localhost:8000/ServiceModelSamples/Service/CalculatorService。TCP 錯誤碼 10061： 無法建立沒有連接，因為目標電腦主動拒絕連線。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q7)  
  
<a name="BKMK_q1"></a>   
## <a name="i-am-unable-to-find-the-project-files-on-my-hard-drive"></a>我在硬碟上找不到專案檔。  
 Visual Studio 將專案檔儲存在 c:\users\\< 使用者 name\Documents\\< Visual Studio 版本\>中的 \Projects[!INCLUDE[wv](../../../includes/wv-md.md)]和[!INCLUDE[win7_client_secondref](../../../includes/win7-client-secondref-md.md)]，c:\Documents and 設定\\< 使用者名稱\>\My 文件\\< Visual Studio 版本\>\Projects 較舊版本 Windows 中的。  
  
<a name="BKMK_q2"></a>   
## <a name="attempting-to-run-the-service-application-http-could-not-register-url-http8000servicemodelsamplesservice-your-process-does-not-have-access-rights-to-this-namespace"></a>嘗試執行服務應用程式： HTTP 無法登錄 URL http://+:8000/ServiceModelSamples/Service/。 您的處理程序沒有足夠的存取權可存取此命名空間。  
 裝載 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務的處理序必須以系統管理權限執行。 如果您是從 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 內部執行此服務，則必須以系統管理員身分執行 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]。 若要這樣做，因此按一下**啟動**，以滑鼠右鍵按一下[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]選取**系統管理員身分執行**。 如果您是從命令提示字元執行此服務，同樣必須以系統管理員身分啟動命令提示字元。 按一下**啟動**，以滑鼠右鍵按一下**命令提示字元**選取**系統管理員身分執行**。  
  
<a name="BKMK_q3"></a>   
## <a name="attempting-to-use-the-svcutilexe-tool-svcutil-is-not-recognized-as-an-internal-or-external-command-operable-program-or-batch-file"></a>當嘗試使用 Svcutil.exe 工具時，發生下列錯誤：'svcutil' 不是內部或外部命令、可執行的程式或批次檔。  
 Svcutil.exe 必須位於系統路徑。 最簡單的解決方式是使用命令提示字元。 按一下**啟動**，選取**所有程式**， [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]， **Visual Studio Tools**，和[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]**命令提示字元**。 針對 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 隨附的所有工具，這個命令提示字元會將系統路徑設為正確位置。  
  
<a name="BKMK_q4"></a>   
## <a name="unable-to-find-the-appconfig-file-generated-by-svcutilexe"></a>找不到 Svcutil.exe 產生的 App.config 檔案。  
 **加入現有項目**對話方塊預設只顯示具有下列副檔名的檔案：.cs、.resx、.settings、.xsd、.wsdl。 您可以指定您想要檢視所有檔案類型，藉由選取**所有檔案 (\*。\*)** 下拉式清單方塊中的右下角中**加入現有項目** 對話方塊。  
  
<a name="BKMK_q5"></a>   
## <a name="compiling-the-client-application-calculatorclient-does-not-contain-a-definition-for-method-name-and-no-extension-method-method-name-accepting-a-first-argument-of-type-calculatorclient-could-be-found-are-you-missing-a-using-directive-or-an-assembly-reference"></a>編譯用戶端應用程式: 'CalculatorClient' 不包含的定義 '\<方法名稱 >' 並不到擴充方法'\<方法名稱 >' 接受型別 'CalculatorClient' 的第一個引數。 找不到 （嗎是否遺漏 using 指示詞或組件參考？)  
 只有已使用 `ServiceOperationAttribute` 標示的方法才會向外界公開。 如果您在 `ServiceOperationAttribute` 介面內省略其中一個方法的 `ICalculator` 屬性，在編譯需要呼叫遺失此屬性之作業的用戶端應用程式時，就會發生這個錯誤。  
  
<a name="BKMK_q6"></a>   
## <a name="compiling-the-client-application-the-type-or-namespace-name-calculatorclient-could-not-be-found-are-you-missing-a-using-directive-or-an-assembly-reference"></a>在編譯用戶端應用程式時，發生下列錯誤：找不到型別或命名空間名稱 'CalculatorClient' (您是否遺漏 using 指示詞或組件參考?)  
 如果您未將 Proxy.cs 或 Proxy.vb 檔案加入至用戶端專案，就會發生這個錯誤。  
  
<a name="BKMK_q7"></a>   
## <a name="running-the-client-unhandled-exception-systemservicemodelendpointnotfoundexception-could-not-connect-to-httplocalhost8000servicemodelsamplesservicecalculatorservice-tcp-error-code-10061-no-connection-could-be-made-because-the-target-machine-actively-refused-it"></a>執行用戶端： 未處理例外狀況： System.ServiceModel.EndpointNotFoundException： 無法連接到http://localhost:8000/ServiceModelSamples/Service/CalculatorService。 TCP 錯誤碼 10061: 無法連線，因為目標電腦主動拒絕連線。  
 如果執行用戶端應用程式但未執行服務，就會發生這個錯誤。  
  
<a name="BKMK_q8"></a>   
## <a name="unhandled-exception-systemservicemodelsecuritysecuritynegotiationexception-soap-security-negotiation-with-httplocalhost8000servicemodelsamplesservicecalculatorservice-for-target-httplocalhost8000servicemodelsamplesservicecalculatorservice-failed"></a>未處理的例外狀況： System.ServiceModel.Security.SecurityNegotiationException： 與 SOAP 安全性交涉 'http://localhost:8000/ServiceModelSamples/Service/CalculatorService'的目標'http://localhost:8000/ServiceModelSamples/Service/CalculatorService' 失敗  
 如果電腦已加入網域卻沒有網路連接，就會發生這個錯誤。 請將您的電腦連接至網路，或是關閉用戶端與服務兩者的安全性。 在服務方面，找出建立 WSHttpBinding 的程式碼並修改為以下內容。  
  
```  
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
```  
  
 用戶端，變更**\<安全性 >** 項目底下**\<繫結 >** 為以下項目：  
  
```xml  
<security mode="Node" />  
```  
  
## <a name="see-also"></a>另請參閱  
 [快速入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [WCF 疑難排解快速入門](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)  
 [疑難排解安裝問題](../../../docs/framework/wcf/troubleshooting-setup-issues.md)
