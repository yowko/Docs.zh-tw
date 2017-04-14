---
title: "使用者入門教學課程疑難排解 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 使用者入門教學課程疑難排解
本主題列出在進行使用者入門教學課程時遇到的最常見問題，以及如何解決這些問題的方式。  
  
1.  [我在硬碟上找不到專案檔。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q1)  
  
2.  [嘗試執行服務應用程式時，發生下列錯誤：HTTP 無法登錄 URL http://+:8000/ServiceModelSamples/Service/。您的處理程序沒有足夠的存取權可存取此命名空間。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q2)  
  
3.  [當嘗試使用 Svcutil.exe 工具時，發生下列錯誤：'svcutil' 不是內部或外部命令、可執行的程式或批次檔。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q3)  
  
4.  [找不到 Svcutil.exe 產生的 App.config 檔案。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q4)  
  
5.  [在編譯用戶端應用程式時，發生下列錯誤：'CalculatorClient' 不包含 '&lt;method name&gt;' 的定義，也找不到擴充方法 '&lt;method name&gt;' 來接受型別 'CalculatorClient' 的第一個引數 (您是否遺漏 using 指示詞或組件參考?)](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q5)  
  
6.  [在編譯用戶端應用程式時，發生下列錯誤：找不到型別或命名空間名稱 'CalculatorClient' (您是否遺漏 using 指示詞或組件參考?)](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q6)  
  
7.  [執行用戶端時，出現下列訊息：未處理的例外狀況: System.ServiceModel.EndpointNotFoundException: 無法連接到 http://localhost:8000/ServiceModelSamples/Service/CalculatorService。TCP 錯誤碼 10061: 無法連線，因為目標電腦主動拒絕連線。](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md#BKMK_q7)  
  
<a name="BKMK_q1"></a>   
## 我在硬碟上找不到專案檔。  
 在 [!INCLUDE[wv](../../../includes/wv-md.md)] 和 [!INCLUDE[win7_client_secondref](../../../includes/win7-client-secondref-md.md)] 中，[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] 會將專案檔儲存在 c:\\使用者\\\<使用者名稱\\Documents\\\<Visual Studio 版本\>\\Projects，而在舊版 Windows 中則是儲存在 c:\\Documents and Settings\\\<使用者名稱\>\\My Documents\\\<Visual Studio 版本\>\\Projects。  
  
<a name="BKMK_q2"></a>   
## 嘗試執行服務應用程式時，發生下列錯誤：HTTP 無法登錄 URL http:\/\/\+:8000\/ServiceModelSamples\/Service\/。您的處理程序沒有足夠的存取權可存取此命名空間。  
 裝載 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務的處理序必須以系統管理權限執行。如果您是從 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 內部執行此服務，則必須以系統管理員身分執行 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]。如果要執行這項操作，請按一下 \[**開始**\]，再以滑鼠右鍵按一下 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]，然後選取 \[**以系統管理員身分執行**\]。如果您是從命令提示字元執行此服務，同樣必須以系統管理員身分啟動命令提示字元。請按一下 \[**開始**\]，再以滑鼠右鍵按一下 \[**命令提示字元**\]，然後選取 \[**以系統管理員身分執行**\]。  
  
<a name="BKMK_q3"></a>   
## 當嘗試使用 Svcutil.exe 工具時，發生下列錯誤：'svcutil' 不是內部或外部命令、可執行的程式或批次檔。  
 Svcutil.exe 必須位於系統路徑。最簡單的解決方式是使用命令提示字元。請按一下 \[**開始**\]，然後依序選取 \[**所有程式**\]、\[[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]\]、\[**Visual Studio 工具**\] 和 \[[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]**命令提示字元**\]。針對 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 隨附的所有工具，這個命令提示字元會將系統路徑設為正確位置。  
  
<a name="BKMK_q4"></a>   
## 找不到 Svcutil.exe 產生的 App.config 檔案。  
 \[**加入現有項目**\] 對話方塊預設只會顯示具有下列副檔名的檔案：.cs、.resx、.settings、.xsd、.wsdl。您可以從 \[**加入現有項目**\] 對話方塊右下角的下拉式清單方塊中選取 \[**所有檔案 \(\*.\*\)**\]，指定要檢視所有檔案類型。  
  
<a name="BKMK_q5"></a>   
## 在編譯用戶端應用程式時，發生下列錯誤：'CalculatorClient' 不包含 '\<method name\>' 的定義，也找不到擴充方法 '\<method name\>' 來接受型別 'CalculatorClient' 的第一個引數 \(您是否遺漏 using 指示詞或組件參考?\)  
 只有已使用 `ServiceOperationAttribute` 標示的方法才會向外界公開。如果 `ICalculator` 介面的任一個方法省略了 `ServiceOperationAttribute` 屬性，在編譯呼叫此作業的用戶端應用程式時，就會因為遺漏屬性而發生這個錯誤。  
  
<a name="BKMK_q6"></a>   
## 在編譯用戶端應用程式時，發生下列錯誤：找不到型別或命名空間名稱 'CalculatorClient' \(您是否遺漏 using 指示詞或組件參考?\)  
 如果您未將 Proxy.cs 或 Proxy.vb 檔案加入至用戶端專案，就會發生這個錯誤。  
  
<a name="BKMK_q7"></a>   
## 執行用戶端時，出現下列訊息：未處理的例外狀況: System.ServiceModel.EndpointNotFoundException: 無法連接到 http:\/\/localhost:8000\/ServiceModelSamples\/Service\/CalculatorService。TCP 錯誤碼 10061: 無法連線，因為目標電腦主動拒絕連線。  
 如果執行用戶端應用程式但未執行服務，就會發生這個錯誤。  
  
<a name="BKMK_q8"></a>   
## 出現下列訊息：未處理的例外狀況: System.ServiceModel.Security.SecurityNegotiationException: 與目標 'http:\/\/localhost:8000\/ServiceModelSamples\/Service\/CalculatorService' 的 'http:\/\/localhost:8000\/ServiceModelSamples\/Service\/CalculatorService' 進行 SOAP 安全性交涉失敗。  
 如果電腦已加入網域卻沒有網路連接，就會發生這個錯誤。請將您的電腦連接至網路，或是關閉用戶端與服務兩者的安全性。在服務方面，找出建立 WSHttpBinding 的程式碼並修改為以下內容。  
  
```  
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
  
```  
  
 在用戶端方面，將 **\<binding\>** 項目底下的 **\<security\>** 項目變更為以下內容：  
  
```  
<security mode="Node" />  
```  
  
## 請參閱  
 [快速入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)   
 [WCF 疑難排解快速入門](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)   
 [疑難排解安裝問題](../../../docs/framework/wcf/troubleshooting-setup-issues.md)