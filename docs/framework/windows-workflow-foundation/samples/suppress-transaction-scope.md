---
title: 隱藏異動範圍
ms.date: 03/30/2017
ms.assetid: 49fb6dd4-30d4-4067-925c-c5de44c8c740
ms.openlocfilehash: b38d168e7da4510b75ebeda7f4984c26fb68898d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="suppress-transaction-scope"></a>隱藏異動範圍
此範例示範如何撰寫自訂 `SuppressTransactionScope` 活動，以隱藏環境執行階段交易 (如果有的話)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`  
  
## <a name="sample-details"></a>範例詳細資料  
 如果特定狀況不需要交易流程，此自訂活動可用來防止交易流出至另一個服務。 工作流程執行階段的 <xref:System.Activities.NativeActivity> 類別中有隱藏環境交易的內建支援，但若要使用此支援，必須撰寫自訂 <xref:System.Activities.NativeActivity>，例如此範例所示範。  
  
 此狀況包含三個部分。 首先，<xref:System.Activities.Statements.TransactionScope> 建立可成為環境交易的執行階段交易。 列印交易本機和分散式識別碼的自訂活動會予以驗證。 在第二部分開始之前，交易接著流向遠端服務。 在第二部分期間，工作流程進入 `SuppressTransactionScope`，然後再度重複列印交易識別碼及流送交易的處理序。 不過，自訂活動找不到環境交易，而且流向服務的訊息不包含交易。 因此，服務會建立交易，表示用戶端和服務上列印的分散式識別碼不相符。 在 `SuppressTransactionScope` 結束後發生最後一個部分，此時執行階段交易再度成為環境交易，另一個流向服務且其分散式識別碼符合第一個訊息之識別碼的訊息會予以驗證。  
  
 活動本身衍生自 <xref:System.Activities.NativeActivity>，因為它必須排定子活動以及加入執行屬性。 `SuppressTransactionScope` 有 <xref:System.Activities.Variable> 類型的 <xref:System.Activities.RuntimeTransactionHandle>，因為控制代碼必須初始化，必須使用它，而不是 <xref:System.Activities.RuntimeTransactionHandle> 類型的執行個體欄位。 `Variable<RuntimeTransactionHandle>` 由於僅供內部使用，因此會加入至活動的中繼資料做為實作變數。  
  
 當活動執行時，它會先檢查是否已指定主體，如果有的話，則會在 `SuppressTransaction` 上設定 <xref:System.Activities.RuntimeTransactionHandle> 屬性。 一旦設定屬性，它會加入至執行屬性並成為環境屬性。 這表示做為 `SuppressTransactionScope` 之子系的任何活動都可以看到此屬性，因此強制隱藏執行階段交易並導致巢狀 <xref:System.Activities.Statements.TransactionScope> 擲回例外狀況。 一旦控制代碼加入至執行屬性，主體就會排定執行。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 SuppressTransactionScope.sln 方案。  
  
2.  若要建置此方案，請按 CTRL + SHIFT + B 或選取**建置方案**從**建置**功能表。  
  
3.  已成功建置，以滑鼠右鍵按一下方案，並選取**設定啟始專案**。 從對話方塊中，選取**多個啟始專案**，並確定這兩個專案的動作是**啟動**。  
  
4.  按 F5 或選取**開始偵錯**從**偵錯**功能表。 或者，您可以按 CTRL + F5 或選取**啟動但不偵錯**從**偵錯**執行，而不偵錯 功能表。  
  
    > [!NOTE]
    >  啟動用戶端之前，伺服器必須在執行中。 主控服務的主控台視窗中會顯示輸出，表示已啟動服務的時間。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`