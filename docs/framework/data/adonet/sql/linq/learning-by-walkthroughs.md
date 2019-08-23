---
title: 依逐步解說學習
ms.date: 03/30/2017
ms.assetid: a8ae2965-6a49-4155-89b0-7fab2c488ab1
ms.openlocfilehash: f1061842343d7a700d3af5da5fdc6aec2f79396d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929217"
---
# <a name="learning-by-walkthroughs"></a>依逐步解說學習
本[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]檔提供數個逐步解說。 本主題會處理某些一般逐步解說問題 (包含疑難排解)，並提供數個入門級逐步解說的連結，供您學習 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]。  
  
> [!NOTE]
> 這節「使用者入門」中的逐步解說提供了支援 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技術的基本程式碼。 在實際的作法中, 您通常會使用物件關聯式設計工具和 Windows Forms 專案來執行[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]您的應用程式。 O/R 設計工具檔提供此用途的範例和逐步解說。  
  
## <a name="getting-started-walkthroughs"></a>使用者入門逐步解說  
 本節有數個逐步解說可供使用。 這些逐步解說是以 Northwind 範例資料庫為基礎，而且會以緩和的步調簡單呈現 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 功能。  
  
 標準使用順序如下：  
  
|目標|Visual Basic|C#|  
|---------------|------------------|---------|  
|建立實體類別及執行簡單的查詢。|[逐步解說：簡單的物件模型和查詢 (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md)|[逐步解說：簡單的物件模型和查詢C#()](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md)|  
|加入第二個類別並執行更複雜的查詢<br /><br /> (必須完成上一個逐步解說)。|[逐步解說：跨關聯性查詢 (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md)|[逐步解說：跨關聯性查詢C#()](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md)|  
|在資料庫中加入、變更和刪除項目。|[逐步解說：運算元據 (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)|[逐步解說：運算元據 (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)|  
|使用預存程序。|[逐步解說：僅使用預存程式 (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)|[逐步解說：僅使用預存程式C#()](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)|  
  
## <a name="general"></a>一般  
 下列是有關於這些逐步解說的一般資訊：  
  
- 環境: 每[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]個逐步解說都會使用 Visual Studio 做為其整合式開發環境 (IDE)。  
  
- SQL 引擎:這些逐步解說會撰寫成使用 SQL Server Express 來執行。 如果您沒有 SQL Server Express，可以免費進行下載。 如需詳細資訊, 請參閱[下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
    > [!NOTE]
    > [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 逐步解說會使用檔名做為連接字串 (Connection String)。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 為了方便起見，讓 SQL Server Express 使用者只需指定檔名即可。 請時時注意安全性問題。 如需詳細資訊, 請參閱[LINQ to SQL 中的安全性](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)。  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]逐步解說通常需要 Northwind 範例資料庫。 如需詳細資訊, 請參閱[下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
- 您在逐步解說中看到的對話方塊和功能表命令可能會與 [說明] 中所述不同, 視您的使用中設定或 Visual Studio 版本而定。 若要變更設定，請在 [工具] 功能表上按一下 [匯入和匯出設定] 。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
- 在專門處理多層式案例的逐步解說中，伺服器必須位於與開發電腦不同的電腦上，而且您必須具有存取該伺服器的適當權限。  
  
- 用來表示 Northwind 範例資料庫中之 Orders 資料表的類別名稱通常為 `[Order]`。 需要進行轉義, 因為`Order`在 Visual Basic 中是關鍵字。  
  
## <a name="troubleshooting"></a>疑難排解  
 發生執行階段錯誤的原因之一是您沒有足夠的權限可存取這些逐步解說中所用的資料庫。 請參閱下列步驟，以解決這類最常見的問題。  
  
### <a name="log-on-issues"></a>登入問題  
 您的應用程式可能正嘗試用不被接受的資料庫登入來存取資料庫。  
  
##### <a name="to-verify-or-change-the-database-log-on"></a>若要驗證或變更資料庫登入  
  
1. 在 Windows [**開始**] 功能表上, 依序指向 [**所有程式**]、[ **Microsoft SQL Server 2005**] 和 [**組態工具**], 然後按一下 [ **SQL Server 組態管理員**]。  
  
2. 在**SQL Server 組態管理員**的左窗格中, 按一下 [ **SQL Server 2005 服務**]。  
  
3. 在右窗格中, 以滑鼠右鍵按一下 [ **SQL Server (SQLEXPRESS)** ], 然後按一下 [**屬性**]。  
  
4. 按一下 [**登**入] 索引標籤, 並確認您嘗試登入伺服器的方式。  
  
     在大部分的情況下,**本機系統**會運作。  
  
     如果您進行變更, 請按一下 [**重新開機**] 以重新開機服務。  
  
### <a name="protocols"></a>通訊協定  
 有時候，通訊協定可能設定不正確，導致您的應用程式無法存取資料庫。 例如, 在中[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]逐步解說所需的**具名管道**通訊協定, 預設不會啟用。  
  
##### <a name="to-enable-the-named-pipes-protocol"></a>若要啟用具名管道通訊協定  
  
1. 在**SQL Server 組態管理員**的左窗格中, 展開 [ **SQL Server 2005 網路**設定], 然後按一下 [ **SQLEXPRESS 的通訊協定**]。  
  
2. 在右窗格中, 確認已啟用**具名管道**通訊協定。 如果不是, 請以滑鼠右鍵按一下 [**具名管道]** , 然後按一下 [**啟用**]。  
  
     您將必須停止並重新啟動服務。 步驟如下一小節所述。  
  
### <a name="stopping-and-restarting-the-service"></a>停止並重新啟動服務  
 您必須先停止並重新啟動服務，您所做的變更才能生效。  
  
##### <a name="to-stop-and-restart-the-service"></a>若要停止並重新啟動服務  
  
1. 在**SQL Server 組態管理員**的左窗格中, 按一下 [ **SQL Server 2005 服務**]。  
  
2. 在右窗格中, 以滑鼠右鍵按一下 [ **SQL Server (SQLEXPRESS)** ], 然後按一下 [**停止**]。  
  
3. 以滑鼠右鍵按一下 **[SQL Server (SQLEXPRESS)** ], 然後按一下 [**重新開機**]。  
  
## <a name="see-also"></a>另請參閱

- [快速入門](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
