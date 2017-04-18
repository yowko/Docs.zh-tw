---
title: "HOW TO：存取來自工作流程應用程式的服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HOW TO：存取來自工作流程應用程式的服務
本主題描述如何從工作流程主控台應用程式呼叫工作流程服務。進行之前，必須先完成 [HOW TO：說明如何使用訊息活動建立工作流程服務。](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)主題所述內容。雖然本主題描述如何從工作流程應用程式呼叫工作流程服務，但是同樣的方法也可以用來從工作流程應用程式呼叫任何 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務。  
  
### 建立工作流程主控台應用程式專案  
  
1.  啟動 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。  
  
2.  載入您在 [HOW TO：說明如何使用訊息活動建立工作流程服務。](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)主題中建立的 MyWFService 專案。  
  
3.  以滑鼠右鍵按一下 \[**方案總管**\] 中的 \[**MyWFService**\] 方案，並依序選取 \[**加入**\]、\[**新專案**\]。從專案類型清單的 \[**已安裝的範本**\] 和 \[**工作流程主控台應用程式**\] 中，選取 \[**工作流程**\]。將專案命名為 MyWFClient，並且使用預設位置，如下圖所示。  
  
     ![加入新的專案對話方塊](../../../../docs/framework/wcf/feature-details/media/addnewprojectdlg.JPG "AddNewProjectDlg")  
  
     按一下 \[**確定**\] 按鈕以關閉 \[**加入新的專案**\] 對話方塊。  
  
4.  建立專案之後，Workflow1.xaml 檔會在設計工具中開啟。按一下 \[**工具箱**\] 索引標籤開啟工具箱 \(如果尚未開啟的話\)，然後按一下圖釘，讓工具箱視窗保持在開啟狀態。  
  
5.  按下 Ctrl\+F5 以建置並啟動服務。ASP.NET 程式開發伺服器會如往常一般隨即啟動，而且 Internet Explorer 會顯示 WCF 說明網頁。請記下這個網頁的 URI，因為您必須在下一個步驟中使用。  
  
     ![顯示 WCF 說明頁面和 URI 的 IE](../../../../docs/framework/wcf/feature-details/media/iewcfhelppagewuri.JPG "IEWCFHelpPageWURI")  
  
6.  以滑鼠右鍵按一下 \[**方案總管**\] 中的 \[**MyWFClient**\] 專案，並選取 \[**加入服務參考**\]。按一下 \[**探索**\] 按鈕，搜尋目前方案中的任何服務。按一下 \[服務\] 清單中 Service1.xamlx 旁邊的三角形。按一下 Service1 旁邊的三角形，即可列出 Service1 服務實作的合約。展開 \[**服務**\] 清單中的 \[**Service1**\] 節點。\[**作業**\] 清單中會顯示 Echo 作業，如下圖所示。  
  
     ![加入服務參考對話方塊](../../../../docs/framework/wcf/feature-details/media/addservicereference.JPG "AddServiceReference")  
  
     保留預設的命名空間，然後按一下 \[**確定**\]，關閉 \[**加入服務參考**\] 對話方塊。此時會顯示下列對話方塊。  
  
     ![&#91;加入服務參考&#93; 通知對話方塊](../../../../docs/framework/wcf/feature-details/media/asrdlg.JPG "ASRDlg")  
  
     按一下 \[**確定**\] 關閉對話方塊。接著，請按下 CTRL\+SHIFT\+B 建置方案。您會注意到工具箱中已加入名為 \[**MyWFClient.ServiceReference1.Activities**\] 的新區段。展開此區段並注意已加入的 Echo 活動，如下圖所示。  
  
     ![工具箱中的 Echo 活動](../../../../docs/framework/wcf/feature-details/media/echoactivity.JPG "EchoActivity")  
  
7.  將 <xref:System.ServiceModel.Activities.Sequence> 活動拖放至設計工具介面上。它位於工具箱的 \[**控制流程**\] 區段下方。  
  
8.  在 <xref:System.ServiceModel.Activities.Sequence> 活動擁有焦點時，按一下 \[**變數**\] 連結，並且加入名為 `inString` 的字串變數。為變數指定預設值 `“Hello, world”`，以及名為 `outString` 的字串變數，如下圖所示。  
  
     ![加入變數](../../../../docs/framework/wcf/feature-details/media/instringvar.JPG "inStringVar")  
  
9. 將 \[**Echo**\] 活動拖放至 <xref:System.ServiceModel.Activities.Sequence> 中。在 \[屬性\] 視窗中，將 \_string 引數繫結至 `inString` 變數，以及將 `out_string` 引數繫結至 outString 變數，如下圖所示。這樣做會將 `inString` 變數的值傳遞至作業中，然後取得傳回值並放入 `outString` 變數。  
  
     ![將引數繫結至變數](../../../../docs/framework/wcf/feature-details/media/argumentbind.JPG "ArgumentBind")  
  
10. 將 \[**WriteLine**\] 活動拖放至 \[**Echo**\] 活動下方，以顯示服務呼叫傳回的字串。\[**WriteLine**\] 活動會位於工具箱的 \[**Primitives**\] 節點中。在 \[**WriteLine**\] 活動的文字方塊中輸入 `outString`，藉此將 \[**WriteLine**\] 活動的 \[**Text**\] 引數繫結至 `outString` 變數。現在，工作流程的外觀應該如下圖所示。  
  
     ![完整的用戶端工作流程](../../../../docs/framework/wcf/feature-details/media/completeclientwf.JPG "CompleteClientWF")  
  
11. 以滑鼠右鍵按一下 \[MyWFService\] 方案，並選取 \[**設定啟始專案**\]。選取 \[**多個啟始專案**\] 選項按鈕，然後在 \[**動作**\] 欄中針對每個專案選取 \[**啟動**\]，如下圖所示。  
  
     ![啟始專案選項](../../../../docs/framework/wcf/feature-details/media/startupprojects.JPG "StartupProjects")  
  
12. 按下 Ctrl\+F5，同時啟動服務與用戶端。ASP.NET 程式開發伺服器會裝載服務，Internet Explorer 會顯示 WCF 說明網頁，而用戶端工作流程應用程式會在主控台視窗中啟動，並且顯示從服務傳回的字串 \(“Hello, world”\)。  
  
## 請參閱  
 [工作流程服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)   
 [HOW TO：說明如何使用訊息活動建立工作流程服務。](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)   
 [從 Web 專案的工作流程中取用 WCF 服務](http://go.microsoft.com/fwlink/?LinkId=207725)