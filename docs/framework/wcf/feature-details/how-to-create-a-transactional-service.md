---
title: "HOW TO：建立異動式服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 647b551e9b78d89cee3ddaf8f47ba8174a23fc5a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-transactional-service"></a>HOW TO：建立異動式服務
這個範例示範建立異動式服務的各層面，以及使用用戶端初始化的異動以協調服務作業。  
  
### <a name="creating-a-transactional-service"></a>建立交易式服務  
  
1.  建立服務合約並使用 <xref:System.ServiceModel.TransactionFlowOption> 列舉的所需設定來標註作業，以指定傳入交易的需求。 請注意，您也可以將 <xref:System.ServiceModel.TransactionFlowAttribute> 置於已實作的服務類別上。 這可以讓介面的單一實作 (而不是每個實作) 使用這些交易設定。  
  
    ```  
    [ServiceContract]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // Use this to require an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Mandatory)]  
        double Add(double n1, double n2);  
        [OperationContract]  
        // Use this to permit an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        double Subtract(double n1, double n2);  
    }  
    ```  
  
2.  建立實作類別，然後使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 選擇性地指定 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> 和 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>。 您應該注意到在許多案例中，<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> 預設 60 秒以及 <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> 預設 `Unspecified` 是適當的。 針對每個作業，您可以使用 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性指定在方法內執行的工作，是否應該發生在根據 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 屬性值定義的交易範圍內。 在此例中，`Add` 方法使用的交易與從用戶端流入的強制傳入交易相同，而且 `Subtract` 方法使用的交易會與傳入交易相同 (如果交易從用戶端流入)，或是與本機建立的新隱含交易相同。  
  
    ```  
    [ServiceBehavior(  
        TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
        TransactionTimeout = "00:00:45")]  
    public class CalculatorService : ICalculator  
    {  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Adding {0} to {1}", n1, n2));  
            return n1 + n2;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Subtracting {0} from {1}", n2, n1));  
            return n1 - n2;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
            // This is where the transaction provides specific benefit  
            // - changes to the database will be committed only when  
            // the transaction completes.  
        }  
    }  
    ```  
  
3.  在組態檔中設定繫結、指定應該流動的交易內容，以及要用來執行這些動作的通訊協定。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ServiceModel 異動組態](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)。 明確地說，在端點項目的 `binding` 屬性中會指定繫結類型。 [\<端點 >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017)元素包含`bindingConfiguration`屬性必須參考名為繫結組態`transactionalOleTransactionsTcpBinding`，如下列範例組態所示。  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     藉由使用 `transactionFlow` 屬性能夠在組態層級啟用交易流程，而使用 `transactionProtocol` 屬性可以指定交易通訊協定，如同下列組態所示。  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a>支援多個交易通訊協定  
  
1.  如需最佳效能，對於與使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 撰寫用戶端與服務有關的案例，您應該使用 OleTransactions 通訊協定。 但是，WS-AtomicTransaction (WS-AT) 通訊協定在需要協力廠商堆疊之互通性的案例中很有用。 您可以使用適當的通訊協定特定繫結提供多重端點，以設定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務同時接受兩種通訊協定，如同下列範例組態所示。  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="http://localhost:8000/CalcService"  
        binding="wsHttpBinding"  
        bindingConfiguration="transactionalWsatHttpBinding"  
        contract="ICalculator"  
        name="WSAtomicTransaction_endpoint" />  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     使用 `transactionProtocol` 屬性可以指定交易通訊協定。 但是，系統提供的 `wsHttpBinding` 並沒有這個屬性，因為這個繫結只能夠使用 WS-AT 通訊協定。  
  
    ```xml  
    <bindings>  
      <wsHttpBinding>  
        <binding name="transactionalWsatHttpBinding"  
          transactionFlow="true" />  
      </wsHttpBinding>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="controlling-the-completion-of-a-transaction"></a>控制交易完成  
  
1.  根據預設，如果並未發生未處理的例外狀況，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 作業會自動完成交易。 您可以藉由使用 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> 屬性和 <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> 方法修改這個行為。 當作業需要發生在與其他作業相同的交易中 (例如，借貸作業) 時，您可以將 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> 屬性設定為 `false` 以停用自動完成行為，如同下列 `Debit` 作業範例所示。 在呼叫 `Debit` 屬性設定為 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> 的方法 (如同作業 `true` 中所示)，或是呼叫 `Credit1` 方法以明確標記交易完成 (如同作業 <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> 中所示) 後，`Credit2` 作業使用的交易才完成。 請注意，這兩個貸款作業是為了示範目的，而單一貸款作業會更單純。  
  
    ```  
    [ServiceBehavior]  
    public class CalculatorService : IAccount  
    {  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Debit(double n)  
        {  
            // Perform debit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = true)]  
        public void Credit1(double n)  
        {  
            // Perform credit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Credit2(double n)  
        {  
            // Perform alternate credit operation  
  
            OperationContext.Current.SetTransactionComplete();  
            return;  
        }  
    }  
    ```  
  
2.  為了交易相互關聯目的，將 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> 屬性設定為 `false` 需要使用工作階段繫結。 `SessionMode` 的 <xref:System.ServiceModel.ServiceContractAttribute> 屬性會指定這項需求。  
  
    ```  
    [ServiceContract(SessionMode = SessionMode.Required)]  
    public interface IAccount  
    {  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Debit(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit1(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit2(double n);  
    }  
    ```  
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a>控制交易式服務執行個體的存留時間  
  
1.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> 屬性指定當交易完成時是否要釋放基礎服務執行個體。 因為這個預設值為 `true`，除非另外設定，不然 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會顯示有效率與可預測的 "just-in-time" 啟動行為。 呼叫後續交易的服務，可以確保新服務執行個體不會有之前交易狀態的殘餘資料。 雖然這方法通常很有用，但是有時候您可能會想要在交易完成之外維護服務執行個體中的狀態。 這種情況的範例是，當必要的狀態或資源控制代碼很難擷取或重組時。 藉由將 <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> 屬性設定為 `false`，您可以達到這個目的。 使用這項設定時，後續呼叫就可以使用執行個體與任何關聯的狀態。 當使用這項功能時，請特別考量清除與完成狀態及交易的時機與方式。 下列範例示範如何使用 `runningTotal` 變數來維護執行個體以進行這項作業。  
  
    ```  
    [ServiceBehavior(TransactionIsolationLevel = [ServiceBehavior(  
        ReleaseServiceInstanceOnTransactionComplete = false)]  
    public class CalculatorService : ICalculator  
    {  
        double runningTotal = 0;  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Adding {0} to {1}", n, runningTotal));  
            runningTotal = runningTotal + n;  
            return runningTotal;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n)  
        {  
            // Perform transactional operation  
            RecordToLog(String.Format("Subtracting {0} from {1}", n, runningTotal));  
            runningTotal = runningTotal - n;  
            return runningTotal;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  因為執行個體的存留時間是服務的內部行為，並且透過 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性控制，所以不需要修改服務組態或服務合約來設定執行個體行為。 此外，網路中不會包含任何表示法。
