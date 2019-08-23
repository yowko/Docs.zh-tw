---
title: WS 交易流程
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: e6fd84d9cc1f7df397e26e41c55f51d45406228d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942160"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="a1c61-102">WS 交易流程</span><span class="sxs-lookup"><span data-stu-id="a1c61-102">WS Transaction Flow</span></span>
<span data-ttu-id="a1c61-103">這個範例會示範用戶端協調異動的用法，以及使用 WS-Atomic 異動或 OleTransactions 通訊協定之異動流程的用戶端和伺服器選項。</span><span class="sxs-lookup"><span data-stu-id="a1c61-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="a1c61-104">這個範例是以實作為計算機服務的[消費者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎, 但是作業的屬性是為了示範如何使用`TransactionFlowAttribute` **TransactionFlowOption**列舉來判斷何種程度已啟用交易流程。</span><span class="sxs-lookup"><span data-stu-id="a1c61-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="a1c61-105">在流動的異動範圍內，會將所要求作業的記錄檔寫入資料庫，並在完成用戶端協調異動之前都會保存該記錄檔。如果用戶端異動未完成，Web 服務異動一定不會認可對資料庫進行適當的更新。</span><span class="sxs-lookup"><span data-stu-id="a1c61-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1c61-106">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="a1c61-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a1c61-107">初始服務和異動的連線之後，用戶端會存取一些服務作業。</span><span class="sxs-lookup"><span data-stu-id="a1c61-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="a1c61-108">將使用示範 `TransactionFlowOption` 之不同設定的每項作業，以下列方式定義服務的合約。</span><span class="sxs-lookup"><span data-stu-id="a1c61-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

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

 <span data-ttu-id="a1c61-109">將以處理作業的順序定義這些作業：</span><span class="sxs-lookup"><span data-stu-id="a1c61-109">This defines the operations in the order they are to be processed:</span></span>  
  
- <span data-ttu-id="a1c61-110">`Add` 作業要求必須包括流動的交易。</span><span class="sxs-lookup"><span data-stu-id="a1c61-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
- <span data-ttu-id="a1c61-111">`Subtract` 作業要求可能包括流動的交易。</span><span class="sxs-lookup"><span data-stu-id="a1c61-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
- <span data-ttu-id="a1c61-112">`Multiply` 作業要求不可在明確的 NotAllowed 設定中包含流動的異動。</span><span class="sxs-lookup"><span data-stu-id="a1c61-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
- <span data-ttu-id="a1c61-113">`Divide` 作業要求在省略 `TransactionFlow` 屬性時不可包含流動的異動。</span><span class="sxs-lookup"><span data-stu-id="a1c61-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="a1c61-114">若要啟用交易流程, 除了適當[ \<](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)的作業屬性之外, 還必須使用已啟用 transactionFlow > 屬性的系結。</span><span class="sxs-lookup"><span data-stu-id="a1c61-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="a1c61-115">在此範例中，除了中繼資料交換端點以外，服務組態也會公開 TCP 端點和 HTTP 端點。</span><span class="sxs-lookup"><span data-stu-id="a1c61-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="a1c61-116">TCP 端點和 HTTP 端點會使用下列系結, 兩者都已[ \<啟用 transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md)屬性。</span><span class="sxs-lookup"><span data-stu-id="a1c61-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
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
> <span data-ttu-id="a1c61-117">系統提供的 netTcpBinding 允許使用 transactionProtocol 規格，而系統提供的 wsHttpBinding 僅使用更具互通性的 WSAtomicTransactionOctober2004 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a1c61-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="a1c61-118">OleTransactions 通訊協定僅供 Windows Communication Foundation (WCF) 用戶端使用。</span><span class="sxs-lookup"><span data-stu-id="a1c61-118">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="a1c61-119">針對實作 `ICalculator` 介面的類別，將會以設定為 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 的 `true` 屬性 (Property)，屬性化 (Attributed) 所有方法。</span><span class="sxs-lookup"><span data-stu-id="a1c61-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="a1c61-120">這個設定的宣告為，將會在交易範圍內發生方法內採用的所有動作。</span><span class="sxs-lookup"><span data-stu-id="a1c61-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="a1c61-121">在此情況下，採取的動作包含記錄資料庫的記錄。</span><span class="sxs-lookup"><span data-stu-id="a1c61-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="a1c61-122">如果作業要求中包含流動的異動，則會在傳入異動範圍內發生動作，或者自動產生新的異動範圍。</span><span class="sxs-lookup"><span data-stu-id="a1c61-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1c61-123"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 屬性會定義服務方法實作的本機行為，而不會定義用戶端的能力或流動交易的需求。</span><span class="sxs-lookup"><span data-stu-id="a1c61-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

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

 <span data-ttu-id="a1c61-124">在用戶端上，作業之服務的 `TransactionFlowOption` 設定會反映在 `ICalculator` 介面之用戶端產生的定義中。</span><span class="sxs-lookup"><span data-stu-id="a1c61-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="a1c61-125">同時，服務的 `transactionFlow` 屬性設定則反映在用戶端的應用程式組態中。</span><span class="sxs-lookup"><span data-stu-id="a1c61-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="a1c61-126">透過選擇適當的 `endpointConfigurationName`，用戶端便可選取傳輸和通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a1c61-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> <span data-ttu-id="a1c61-127">不管選擇哪個通訊協定或傳輸，此範例所觀察的行為都一樣。</span><span class="sxs-lookup"><span data-stu-id="a1c61-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="a1c61-128">初始服務連線時，用戶端會在呼叫服務作業時建立新的 `TransactionScope`。</span><span class="sxs-lookup"><span data-stu-id="a1c61-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

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

 <span data-ttu-id="a1c61-129">作業的呼叫如下所示：</span><span class="sxs-lookup"><span data-stu-id="a1c61-129">The calls to the operations are as follows:</span></span>  
  
- <span data-ttu-id="a1c61-130">`Add` 要求會將必要的異動流動至服務，而服務的動作則是在用戶端的異動範圍內發生。</span><span class="sxs-lookup"><span data-stu-id="a1c61-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="a1c61-131">第一個 `Subtract` 要求也會將允許的交易流動至服務，而服務的動作再次是在用戶端的交易範圍內發生。</span><span class="sxs-lookup"><span data-stu-id="a1c61-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="a1c61-132">第二個 `Subtract` 要求會在以 `TransactionScopeOption.Suppress` 選項宣告的新交易範圍內執行。</span><span class="sxs-lookup"><span data-stu-id="a1c61-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="a1c61-133">這樣做會隱藏用戶端的初始外部異動，而且要求不會將異動流動至服務。</span><span class="sxs-lookup"><span data-stu-id="a1c61-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="a1c61-134">這個方法可讓用戶端明確地不參與，並在不需要將交易流動至服務時，防止進行此動作。</span><span class="sxs-lookup"><span data-stu-id="a1c61-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="a1c61-135">會在新的和未連接的異動範圍內發生服務動作。</span><span class="sxs-lookup"><span data-stu-id="a1c61-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
- <span data-ttu-id="a1c61-136">`Multiply` 要求不會將異動流動至服務，因為用戶端產生之 `ICalculator` 介面的定義包含設定為 <xref:System.ServiceModel.TransactionFlowAttribute><xref:System.ServiceModel.TransactionFlowOption> 的 `NotAllowed`。</span><span class="sxs-lookup"><span data-stu-id="a1c61-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
- <span data-ttu-id="a1c61-137">`Divide` 要求不會將交易流動至服務，因為用戶端產生之 `ICalculator` 介面的定義再次不包含 `TransactionFlowAttribute`。</span><span class="sxs-lookup"><span data-stu-id="a1c61-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="a1c61-138">再次會在其他新的和未連接的異動範圍內發生服務動作。</span><span class="sxs-lookup"><span data-stu-id="a1c61-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="a1c61-139">當您執行範例時，作業要求和回應會顯示在用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="a1c61-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a1c61-140">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="a1c61-140">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
 <span data-ttu-id="a1c61-141">服務作業要求的記錄會顯示在服務的主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="a1c61-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="a1c61-142">在用戶端視窗中按下 ENTER 鍵，即可關閉用戶端。</span><span class="sxs-lookup"><span data-stu-id="a1c61-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="a1c61-143">成功執行之後，會完成用戶端交易範圍，並且認可該範圍內採取的所有動作。</span><span class="sxs-lookup"><span data-stu-id="a1c61-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="a1c61-144">特別來說，記下的 5 筆記錄會保存在服務的資料庫中。</span><span class="sxs-lookup"><span data-stu-id="a1c61-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="a1c61-145">前兩項則是在用戶端的交易範圍內發生。</span><span class="sxs-lookup"><span data-stu-id="a1c61-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="a1c61-146">如果在用戶端的 `TransactionScope` 任意處發生例外狀況，則無法完成異動。</span><span class="sxs-lookup"><span data-stu-id="a1c61-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="a1c61-147">這會導致在該範圍內記載的記錄，不會對資料庫認可。</span><span class="sxs-lookup"><span data-stu-id="a1c61-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="a1c61-148">在取消註解呼叫以完成外部 `TransactionScope` 之後，重複執行範例即可觀察這個影響。</span><span class="sxs-lookup"><span data-stu-id="a1c61-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="a1c61-149">在這種執行中，只會記錄後三個動作 (第二個 `Subtract`、`Multiply` 和 `Divide` 要求)，這是因為用戶端交易並沒有流動至這三項。</span><span class="sxs-lookup"><span data-stu-id="a1c61-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a1c61-150">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="a1c61-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a1c61-151">若要建立C#或 Visual Basic .net 版本的解決方案, 請遵循[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示</span><span class="sxs-lookup"><span data-stu-id="a1c61-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2. <span data-ttu-id="a1c61-152">確定您已安裝 SQL Server Express Edition 或 SQL Server，而且已在服務的應用程式組態檔中正確設定連接字串。</span><span class="sxs-lookup"><span data-stu-id="a1c61-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="a1c61-153">若要在不使用資料庫的情況下執行範例，請將服務之應用程式組態檔中的 `usingSql` 值設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="a1c61-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3. <span data-ttu-id="a1c61-154">若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="a1c61-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a1c61-155">若為跨電腦組態，請使用下列指示來啟用分散式異動協調器，然後使用 Windows SDK 中的 WsatConfig.exe 工具來啟用 WCF 異動網路支援。</span><span class="sxs-lookup"><span data-stu-id="a1c61-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="a1c61-156">如需設定 Wsatconfig.exe 的相關資訊, 請參閱設定 WS-不可部分完成[交易支援](https://go.microsoft.com/fwlink/?LinkId=190370)。</span><span class="sxs-lookup"><span data-stu-id="a1c61-156">See [Configuring WS-Atomic Transaction Support](https://go.microsoft.com/fwlink/?LinkId=190370) for information on setting up WsatConfig.exe.</span></span>  
  
 <span data-ttu-id="a1c61-157">無論您是在同一部電腦或不同電腦上執行範例, 都必須設定 Microsoft 分散式交易協調器 (MSDTC) 以啟用網路交易流程, 並使用 Wsatconfig.exe 工具來啟用 WCF 交易網路支援。</span><span class="sxs-lookup"><span data-stu-id="a1c61-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="a1c61-158">若要設定 Microsoft Distributed Transaction Coordinator (MSDTC) 以支援執行範例</span><span class="sxs-lookup"><span data-stu-id="a1c61-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1. <span data-ttu-id="a1c61-159">在執行 Windows Server 2003 或 Windows XP 的服務電腦上，請遵循下列指示設定 MSDTC 以允許傳入網路異動。</span><span class="sxs-lookup"><span data-stu-id="a1c61-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="a1c61-160">在 [**開始**] 功能表中, 依序流覽至 [**控制台**]、[系統**管理工具**] 和 [**元件服務**]。</span><span class="sxs-lookup"><span data-stu-id="a1c61-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="a1c61-161">展開 [**元件服務**]。</span><span class="sxs-lookup"><span data-stu-id="a1c61-161">Expand **Component Services**.</span></span> <span data-ttu-id="a1c61-162">開啟 [**電腦**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="a1c61-162">Open the **Computers** folder.</span></span>  
  
    3. <span data-ttu-id="a1c61-163">以滑鼠右鍵按一下**我的電腦**, 然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="a1c61-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="a1c61-164">在 [ **MSDTC** ] 索引標籤上, 按一下 [**安全性**設定]。</span><span class="sxs-lookup"><span data-stu-id="a1c61-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5. <span data-ttu-id="a1c61-165">檢查**網路 DTC 存取**並**允許輸入**。</span><span class="sxs-lookup"><span data-stu-id="a1c61-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6. <span data-ttu-id="a1c61-166">按一下 **[確定]** , 然後按一下 [**是**] 重新開機 MSDTC 服務。</span><span class="sxs-lookup"><span data-stu-id="a1c61-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7. <span data-ttu-id="a1c61-167">按一下 [確定] 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a1c61-167">Click **OK** to close the dialog box.</span></span>  
  
2. <span data-ttu-id="a1c61-168">在執行 Windows Server 2008 或 Windows Vista 的服務電腦上，請遵循下列指示設定 MSDTC 以允許傳入網路異動。</span><span class="sxs-lookup"><span data-stu-id="a1c61-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="a1c61-169">在 [**開始**] 功能表中, 依序流覽至 [**控制台**]、[系統**管理工具**] 和 [**元件服務**]。</span><span class="sxs-lookup"><span data-stu-id="a1c61-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="a1c61-170">展開 [**元件服務**]。</span><span class="sxs-lookup"><span data-stu-id="a1c61-170">Expand **Component Services**.</span></span> <span data-ttu-id="a1c61-171">開啟 [**電腦**] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="a1c61-171">Open the **Computers** folder.</span></span> <span data-ttu-id="a1c61-172">選取 [**分散式交易協調器**]。</span><span class="sxs-lookup"><span data-stu-id="a1c61-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3. <span data-ttu-id="a1c61-173">以滑鼠右鍵按一下 [ **DTC 協調器**], 然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="a1c61-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="a1c61-174">在 [**安全性**] 索引標籤上, 檢查 [**網路 DTC 存取**] 和 [**允許輸入**]。</span><span class="sxs-lookup"><span data-stu-id="a1c61-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5. <span data-ttu-id="a1c61-175">按一下 **[確定]** , 然後按一下 [**是**] 重新開機 MSDTC 服務。</span><span class="sxs-lookup"><span data-stu-id="a1c61-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="a1c61-176">按一下 [確定] 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a1c61-176">Click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="a1c61-177">在用戶端電腦上，設定 MSDTC 以允許傳出網路交易：</span><span class="sxs-lookup"><span data-stu-id="a1c61-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1. <span data-ttu-id="a1c61-178">在 [**開始**] 功能表中, `Control Panel`依序流覽至 [系統**管理工具**] 和 [**元件服務**]。</span><span class="sxs-lookup"><span data-stu-id="a1c61-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="a1c61-179">以滑鼠右鍵按一下**我的電腦**, 然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="a1c61-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3. <span data-ttu-id="a1c61-180">在 [ **MSDTC** ] 索引標籤上, 按一下 [**安全性**設定]。</span><span class="sxs-lookup"><span data-stu-id="a1c61-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4. <span data-ttu-id="a1c61-181">檢查 [**網路 DTC 存取**] 和 [**允許輸出**]。</span><span class="sxs-lookup"><span data-stu-id="a1c61-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5. <span data-ttu-id="a1c61-182">按一下 **[確定]** , 然後按一下 [**是**] 重新開機 MSDTC 服務。</span><span class="sxs-lookup"><span data-stu-id="a1c61-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="a1c61-183">按一下 [確定] 關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a1c61-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a1c61-184">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="a1c61-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a1c61-185">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="a1c61-185">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a1c61-186">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="a1c61-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a1c61-187">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="a1c61-187">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
