---
title: WS 異動流程
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 35af3090c0f898578a5f8dfb81d02d22a0074ad2
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097265"
---
# <a name="ws-transaction-flow"></a>WS 異動流程
這個範例會示範用戶端協調異動的用法，以及使用 WS-Atomic 異動或 OleTransactions 通訊協定之異動流程的用戶端和伺服器選項。 此樣本根據[快速入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)以實作計算機服務，但作業屬於示範如何使用`TransactionFlowAttribute`具有**TransactionFlowOption**若要判斷何種程度的交易流程已啟用的列舉型別。 在流動的交易範圍內，會將所要求作業的記錄檔寫入資料庫，並在完成用戶端協調交易之前都會保存該記錄檔。如果用戶端交易未完成，Web 服務交易一定不會認可對資料庫進行適當的更新。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 初始服務和交易的連線之後，用戶端會存取一些服務作業。 將使用示範 `TransactionFlowOption` 之不同設定的每項作業，以下列方式定義服務的合約。  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Allowed)]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.NotAllowed)]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);   
}  
```

 將以處理作業的順序定義這些作業：  
  
-   `Add` 作業要求必須包括流動的交易。  
  
-   `Subtract` 作業要求可能包括流動的交易。  
  
-   `Multiply` 作業要求不可在明確的 NotAllowed 設定中包含流動的交易。  
  
-   `Divide` 作業要求在省略 `TransactionFlow` 屬性時不可包含流動的交易。  
  
 若要啟用交易流程，使用的繫結[ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)必須使用啟用的屬性，以及適當的作業屬性。 在此範例中，除了中繼資料交換端點以外，服務組態也會公開 TCP 端點和 HTTP 端點。 TCP 端點和 HTTP 端點會使用下列的繫結，這兩者都有[ \<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)啟用的屬性。  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding name="transactionalOleTransactionsTcpBinding"  
             transactionFlow="true"  
             transactionProtocol="OleTransactions"/>  
  </netTcpBinding>  
  <wsHttpBinding>  
    <binding name="transactionalWsatHttpBinding"  
             transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
> [!NOTE]
>  系統提供的 netTcpBinding 允許使用 transactionProtocol 規格，而系統提供的 wsHttpBinding 僅使用更具互通性的 WSAtomicTransactionOctober2004 通訊協定。 OleTransactions 通訊協定僅適用於使用 Windows Communication Foundation (WCF) 用戶端。  
  
 針對實作 `ICalculator` 介面的類別，將會以設定為 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 的 `true` 屬性 (Property)，屬性化 (Attributed) 所有方法。 這個設定的宣告為，將會在交易範圍內發生方法內採用的所有動作。 在此情況下，採取的動作包含記錄資料庫的記錄。 如果作業要求中包含流動的交易，則會在傳入交易範圍內發生動作，或者自動產生新的交易範圍。  
  
> [!NOTE]
>  <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 屬性會定義服務方法實作的本機行為，而不會定義用戶端的能力或流動交易的需求。  

```csharp
// Service class that implements the service contract.  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Add(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Subtract(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n2, n1));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Multiply(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Divide(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
    // Logging method omitted for brevity  
}  
```

 在用戶端上，作業之服務的 `TransactionFlowOption` 設定會反映在 `ICalculator` 介面之用戶端產生的定義中。 同時，服務的 `transactionFlow` 屬性設定則反映在用戶端的應用程式組態中。 透過選擇適當的 `endpointConfigurationName`，用戶端便可選取傳輸和通訊協定。  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
>  不管選擇哪個通訊協定或傳輸，此範例所觀察的行為都一樣。  
  
 初始服務連線時，用戶端會在呼叫服務作業時建立新的 `TransactionScope`。  

```csharp
// Start a transaction scope  
using (TransactionScope tx =  
            new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation  
    //  - generatedClient will flow the required active transaction  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("  Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation  
    //  - generatedClient will flow the allowed active transaction  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Start a transaction scope that suppresses the current transaction  
    using (TransactionScope txSuppress =  
                new TransactionScope(TransactionScopeOption.Suppress))  
    {  
        // Call the Subtract service operation  
        //  - the active transaction is suppressed from the generatedClient  
        //    and no transaction will flow  
        value1 = 21.05D;  
        value2 = 42.16D;  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
        // Complete the suppressed scope  
        txSuppress.Complete();  
    }  
  
    // Call the Multiply service operation  
    // - generatedClient will not flow the active transaction  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("  Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    // - generatedClient will not flow the active transaction  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("  Divide({0},{1}) = {2}", value1, value2, result);  
  
    // Complete the transaction scope  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
```

 作業的呼叫如下所示：  
  
-   `Add` 要求會將必要的交易流動至服務，而服務的動作則是在用戶端的交易範圍內發生。  
  
-   第一個 `Subtract` 要求也會將允許的交易流動至服務，而服務的動作再次是在用戶端的交易範圍內發生。  
  
-   第二個 `Subtract` 要求會在以 `TransactionScopeOption.Suppress` 選項宣告的新交易範圍內執行。 這樣做會隱藏用戶端的初始外部交易，而且要求不會將交易流動至服務。 這個方法可讓用戶端明確地不參與，並在不需要將交易流動至服務時，防止進行此動作。 會在新的和未連接的異動範圍內發生服務動作。  
  
-   `Multiply`要求不會流動至服務的交易，因為用戶端產生的定義`ICalculator`介面包括<xref:System.ServiceModel.TransactionFlowAttribute>設定為<xref:System.ServiceModel.TransactionFlowOption> `NotAllowed`。  
  
-   `Divide` 要求不會將交易流動至服務，因為用戶端產生之 `ICalculator` 介面的定義再次不包含 `TransactionFlowAttribute`。 再次會在其他新的和未連接的交易範圍內發生服務動作。  
  
 當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```  
Starting transaction  
  Add(100,15.99) = 115.99  
  Subtract(145,76.54) = 68.46  
  Subtract(21.05,42.16) = -21.11  
  Multiply(9,81.25) = 731.25  
  Divide(22,7) = 3.14285714285714  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 服務作業要求的記錄會顯示在服務的主控台視窗中。 在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 成功執行之後，會完成用戶端交易範圍，並且認可該範圍內採取的所有動作。 特別來說，記下的 5 筆記錄會保存在服務的資料庫中。 前兩項則是在用戶端的交易範圍內發生。  
  
 如果在用戶端的 `TransactionScope` 任意處發生例外狀況，則無法完成交易。 這會導致在該範圍內記載的記錄，不會對資料庫認可。 在取消註解呼叫以完成外部 `TransactionScope` 之後，重複執行範例即可觀察這個影響。 在這種執行中，只會記錄後三個動作 (第二個 `Subtract`、`Multiply` 和 `Divide` 要求)，這是因為用戶端交易並沒有流動至這三項。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  若要建置方案的 C# 或 Visual Basic.NET 版本，請依照下列中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)  
  
2.  確定您已安裝 SQL Server Express Edition 或 SQL Server，而且已在服務的應用程式組態檔中正確設定連接字串。 若要在不使用資料庫的情況下執行範例，請將服務之應用程式組態檔中的 `usingSql` 值設定為 `false`。  
  
3.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
    > [!NOTE]
    >  若為跨電腦組態，請使用下列指示來啟用分散式異動協調器，然後使用 Windows SDK 中的 WsatConfig.exe 工具來啟用 WCF 異動網路支援。 請參閱[設定 Ws-atomic 交易支援](https://go.microsoft.com/fwlink/?LinkId=190370)如需設定 WsatConfig.exe 的詳細資訊。  
  
 是否在同一部電腦或不同的電腦上，您可以執行範例，您必須設定 Microsoft Distributed Transaction Coordinator (MSDTC) 以啟用網路交易流程，並使用 WsatConfig.exe 工具來啟用 WCF 異動網路支援。  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a>若要設定 Microsoft Distributed Transaction Coordinator (MSDTC) 以支援執行範例  
  
1.  在執行 Windows Server 2003 或 Windows XP 的服務電腦上，請遵循下列指示設定 MSDTC 以允許傳入網路異動。  
  
    1.  從**開始** 功能表中，瀏覽至**控制台**，然後**系統管理工具**，然後**元件服務**。  
  
    2.  依序展開**元件服務**。 開啟**電腦**資料夾。  
  
    3.  以滑鼠右鍵按一下**我的電腦**，然後選取**屬性**。  
  
    4.  在  **MSDTC**索引標籤上，按一下**安全性設定**。  
  
    5.  請檢查**網路 DTC 存取**並**允許輸入**。  
  
    6.  按一下  **確定**，然後按一下**是**重新啟動 MSDTC 服務。  
  
    7.  按一下 [確定]  關閉對話方塊。  
  
2.  在執行 Windows Server 2008 或 Windows Vista 的服務電腦上，請遵循下列指示設定 MSDTC 以允許傳入網路異動。  
  
    1.  從**開始** 功能表中，瀏覽至**控制台**，然後**系統管理工具**，然後**元件服務**。  
  
    2.  依序展開**元件服務**。 開啟**電腦**資料夾。 選取 **分散式交易協調器**。  
  
    3.  以滑鼠右鍵按一下**DTC 協調器**，然後選取**屬性**。  
  
    4.  在上**安全性**索引標籤上，勾選**網路 DTC 存取**並**允許輸入**。  
  
    5.  按一下  **確定**，然後按一下**是**重新啟動 MSDTC 服務。  
  
    6.  按一下 [確定]  關閉對話方塊。  
  
3.  在用戶端電腦上，設定 MSDTC 以允許傳出網路異動：  
  
    1.  從**開始** 功能表中，瀏覽至`Control Panel`，然後**系統管理工具**，然後**元件服務**。  
  
    2.  以滑鼠右鍵按一下**我的電腦**，然後選取**屬性**。  
  
    3.  在  **MSDTC**索引標籤上，按一下**安全性設定**。  
  
    4.  請檢查**網路 DTC 存取**並**允許輸出**。  
  
    5.  按一下  **確定**，然後按一下**是**重新啟動 MSDTC 服務。  
  
    6.  按一下 [確定]  關閉對話方塊。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
