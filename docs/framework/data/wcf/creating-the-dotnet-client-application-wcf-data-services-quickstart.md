---
title: "建立 .NET Framework 用戶端應用程式 ((WCF Data Services 快速入門) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 建立 .NET Framework 用戶端應用程式 ((WCF Data Services 快速入門)
這是 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 快速入門的最後一項工作。  在此工作中，您會在方案中加入主控台應用程式、在這個新的用戶端應用程式中加入 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 摘要的參考，並從用戶端應用程式中利用已產生的用戶端資料服務類別和用戶端程式庫來存取 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要。  
  
> [!NOTE]
>  不需要 .NET Framework 架構的用戶端應用程式也可存取資料摘要。  此資料服務可由取用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要的任何應用程式元件所存取。  如需詳細資訊，請參閱[使用用戶端應用程式中的資料服務](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md)。  
  
### 若要使用 Visual Studio 建立用戶端應用程式  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下方案，然後依序按一下 \[**加入**\] 和 \[**新增專案**\]。  
  
2.  在 \[**專案類型**\] 中，按一下 \[**視窗**\]，然後在 \[**範本**\] 窗格中選取 \[**WPF 應用程式**\]。  
  
3.  針對專案名稱輸入 `NorthwindClient`，然後按一下 \[**確定**\]。  
  
4.  開啟 MainWindow.xaml 檔案，並以下列程式碼取代 XAML 程式碼：  
  
     [!code-xml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]  
  
### 若要將資料服務參考加入至專案  
  
1.  以滑鼠右鍵按一下 NorthwindClient 專案，依序按一下 \[**加入服務參考**\] 和 \[**探索**\]。  
  
     這會顯示您在第一個工作中建立的 Northwind 資料服務。  
  
2.  在 \[**命名空間**\] 文字方塊中，輸入 `Northwind`，然後按一下 \[**確定**\]。  
  
     這會將新的程式碼檔案加入至專案中，此專案包含的資料類別可用來存取做為物件的資料服務資源，並與之進行互動。  在命名空間 `NorthwindClient.Northwind` 中建立資料類別。  
  
### 在 WPF 應用程式中存取資料服務的資料  
  
1.  在 \[**NorthwindClient**\] 下的 \[**方案總管**\] 中，以滑鼠右鍵按一下專案，然後按一下 \[**加入參考**\]。  
  
2.  在 \[加入參考\] 對話方塊中，按一下 \[**.NET** \] 索引標籤，然後選取 System.Data.Services.Client.dll 組件，再按一下 \[**確定**\]。  在 \[**NorthwindClient**\] 下的 \[**方案總管**\] 中，開啟 MainWindow.xaml 檔案的字碼頁，並加入下列 `using` 陳述式 \(在 Visual Basic 中為 `Imports`\)。  
  
     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]  
  
3.  插入下列查詢資料服務的程式碼，並將 <xref:System.Data.Services.Client.DataServiceCollection%601> 的結果繫結到 `MainWindow` 類別裡：  
  
    > [!NOTE]
    >  您必須用裝載 Northwind 資料服務之執行個體的伺服器及連接埠來取代主機名稱 `localhost:12345`。  
  
     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]  
  
4.  將下列儲存變更的程式碼插入 `MainWindow` 類別中：  
  
     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]  
  
### 建置和執行 NorthwindClient 應用程式  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 NorthwindClient 專案，然後選取 \[**設定為啟始專案**\]。  
  
2.  請按 F5 啟動應用程式。  
  
     如此會建置方案，並啟動用戶端應用程式。  從服務要求資料，並顯示在主控台中。  
  
3.  編輯資料格的 \[**數量**\] 欄，然後按一下 \[**儲存**\]。  
  
     資料服務的變更會被儲存。  
  
    > [!NOTE]
    >  此版本的 NorthwindClient 應用程式不支援新增及刪除實體。  
  
## 後續步驟  
 您已成功建立存取範例 Northwind [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要的用戶端應用程式。  您也已經完成 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 快速入門。  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 從 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 應用程式存取 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要的詳細資訊，請參閱[WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)。  
  
## 請參閱  
 [使用者入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)   
 [資源](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)