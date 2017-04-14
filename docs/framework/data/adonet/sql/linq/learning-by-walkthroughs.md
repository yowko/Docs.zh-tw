---
title: "從逐步解說學習 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 從逐步解說學習
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 文件提供了數個逐步解說。  本主題會處理某些一般逐步解說問題 \(包含疑難排解\)，並提供數個入門級逐步解說的連結，供您學習 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]。  
  
> [!NOTE]
>  這節「使用者入門」中的逐步解說提供了支援 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技術的基本程式碼。  在實務中，您通常會使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]和 Windows Form 專案來實作 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 應用程式。  [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] 文件提供了針對此目的的範例和逐步解說。  
  
## 使用者入門逐步解說  
 本節有數個逐步解說可供使用。  這些逐步解說是以 Northwind 範例資料庫為基礎，而且會以緩和的步調簡單呈現 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 功能。  
  
 標準使用順序如下：  
  
|目標|Visual Basic|C\#|  
|--------|------------------|---------|  
|建立實體類別及執行簡單的查詢。|[逐步解說：簡單的物件模型和查詢 \(Visual Basic\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md)|[逐步解說：簡單的物件模型和查詢 \(C\#\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md)|  
|加入第二個類別並執行更複雜的查詢<br /><br /> \(必須完成上一個逐步解說\)。|[逐步解說：跨關聯性查詢 \(Visual Basic\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md)|[逐步解說：跨關聯性查詢 \(C\#\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md)|  
|在資料庫中加入、變更和刪除項目。|[逐步解說：操作資料 \(Visual Basic\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)|[逐步解說：操作資料 \(C\#\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)|  
|使用預存程序。|[逐步解說：僅使用預存程序 \(Visual Basic\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)|[逐步解說：僅使用預存程序 \(C\#\)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)|  
  
## 一般  
 下列是有關於這些逐步解說的一般資訊：  
  
-   環境：每個 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 逐步解說都會使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 做為其整合式開發環境 \(IDE\)。  
  
-   SQL 引擎：這些逐步解說是針對 SQL Server Express 撰寫的。  如果您沒有 SQL Server Express，可以免費進行下載。  如需詳細資訊，請參閱[下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
    > [!NOTE]
    >  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 逐步解說會使用檔名做為連接字串 \(Connection String\)。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 為了方便起見，讓 SQL Server Express 使用者只需指定檔名即可。  請時時注意安全性問題。  如需詳細資訊，請參閱 [LINQ to SQL 的安全性](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)。  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 逐步解說通常需要使用 Northwind 範例資料庫。  如需詳細資訊，請參閱[下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
-   您在逐步解說中看到的對話方塊與功能表命令，可能會因您所使用的設定或 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 版本，而與說明中所述不同。  若要變更設定，請在 \[工具\] 功能表上按一下 \[匯入和匯出設定\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
-   在專門處理多層式案例的逐步解說中，伺服器必須位於與開發電腦不同的電腦上，而且您必須具有存取該伺服器的適當權限。  
  
-   用來表示 Northwind 範例資料庫中之 Orders 資料表的類別名稱通常為 `[Order]`。  因為 `Order` 為 [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] 中的關鍵字，所以需要進行逸出。  
  
## 疑難排解  
 發生執行階段錯誤的原因之一是您沒有足夠的權限可存取這些逐步解說中所用的資料庫。  請參閱下列步驟，以解決這類最常見的問題。  
  
### 登入問題  
 您的應用程式可能正嘗試用不被接受的資料庫登入來存取資料庫。  
  
##### 若要驗證或變更資料庫登入  
  
1.  在 Windows 的 \[**開始**\] 功能表上，依序指向 \[**所有程式**\]、\[**Microsoft SQL Server 2005**\]、\[**組態工具**\]，然後按一下 \[**SQL Server 組態管理員**\]。  
  
2.  在 \[**SQL Server 組態管理員**\] 的左窗格中，按一下 \[**SQL Server 2005 服務**\]。  
  
3.  以滑鼠右鍵按一下右窗格中的 \[**SQL Server \(SQLEXPRESS\)**\]，然後按一下 \[**屬性**\]。  
  
4.  按一下 \[**登入**\] 索引標籤，確認您正嘗試用何種方式登入伺服器。  
  
     在大部分情況下，\[**本機系統**\] 會有作用。  
  
     如果您進行了變更，請按一下 \[**重新啟動**\] 重新啟動服務。  
  
### 通訊協定  
 有時候，通訊協定可能設定不正確，導致您的應用程式無法存取資料庫。  例如，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]之逐步解說所需的 \[具名管道\] 通訊協定，預設不會啟用。  
  
##### 若要啟用具名管道通訊協定  
  
1.  在 \[**SQL Server 組態管理員**\] 的左窗格中，展開 \[**SQL Server 2005 網路組態**\]，然後按一下 \[**SQLEXPRESS 的通訊協定**\]。  
  
2.  在右窗格中，確定已啟用 \[**具名管道**\] 通訊協定。  如未啟用，請以滑鼠右鍵按一下 \[**具名管道**\]，然後按一下 \[**啟用**\]。  
  
     您將必須停止並重新啟動服務。  步驟如下一小節所述。  
  
### 停止並重新啟動服務  
 您必須先停止並重新啟動服務，您所做的變更才能生效。  
  
##### 若要停止並重新啟動服務  
  
1.  在 \[**SQL Server 組態管理員**\] 的左窗格中，按一下 \[**SQL Server 2005 服務**\]。  
  
2.  以滑鼠右鍵按一下右窗格中的 \[**SQL Server \(SQLEXPRESS\)**\]，然後按一下 \[**停止**\]。  
  
3.  以滑鼠右鍵按一下 \[**SQL Server \(SQLEXPRESS\)**\]，然後按一下 \[**重新啟動**\]。  
  
## 請參閱  
 [快速入門](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)