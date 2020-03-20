---
title: 進出工作流程服務的異動流動
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: fe03047dd931d25ec94bbc5e00c479d1b42397bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185271"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>進出工作流程服務的異動流動
工作流程服務與用戶端都可以參與交易。  若要讓服務作業變成環境交易的一部分，請將 <xref:System.ServiceModel.Activities.Receive> 活動放在 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動內。 <xref:System.ServiceModel.Activities.Send> 或 <xref:System.ServiceModel.Activities.SendReply> 活動在 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 內所進行的任何呼叫也會在環境交易中進行。 工作流程用戶端應用程式可以使用 <xref:System.Activities.Statements.TransactionScope> 活動建立環境異動，然後使用環境異動呼叫服務作業。 本主題逐步帶領您建立參與交易的工作流程服務和工作流程用戶端。  
  
> [!WARNING]
> 如果在事務中載入工作流服務實例，並且工作流包含<xref:System.Activities.Statements.Persist>活動，工作流實例將阻止，直到事務超時。  
  
> [!IMPORTANT]
> 每當您使用 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 時，建議您將工作流程中的所有 Receive 放在 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 活動內。  
  
> [!IMPORTANT]
> 如果使用 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 而且訊息按照錯誤的順序送達，工作流程就會在嘗試傳送第一則順序錯誤的訊息時中止。 當工作流程閒置時，您必須確定工作流程永遠位於一致的停止點。 萬一工作流程已中止，這樣做可讓您從上一個保存點重新啟動工作流程。  
  
### <a name="create-a-shared-library"></a>建立共用程式庫  
  
1. 建立一個新的空白 Visual Studio 方案。  
  
2. 加入稱為 `Common` 的新類別庫專案。 加入下列組件的參考：  
  
    - System.Activities.dll  
  
    - System.ServiceModel.dll  
  
    - System.ServiceModel.Activities.dll  
  
    - System.Transactions.dll  
  
3. 將稱為 `PrintTransactionInfo` 的新類別加入至 `Common` 專案。 此類別衍生自 <xref:System.Activities.NativeActivity>，而且會多載 <xref:System.Activities.NativeActivity.Execute%2A> 方法。  
  
    ```csharp
    using System;  
    using System;  
    using System.Activities;  
    using System.Transactions;  
  
    namespace Common  
    {  
        public class PrintTransactionInfo : NativeActivity  
        {  
            protected override void Execute(NativeActivityContext context)  
            {  
                RuntimeTransactionHandle rth = context.Properties.Find(typeof(RuntimeTransactionHandle).FullName) as RuntimeTransactionHandle;  
  
                if (rth == null)  
                {  
                    Console.WriteLine("There is no ambient RuntimeTransactionHandle");  
                }  
  
                Transaction t = rth.GetCurrentTransaction(context);  
  
                if (t == null)  
                {  
                    Console.WriteLine("There is no ambient transaction");  
                }  
                else  
                {  
                    Console.WriteLine("Transaction: {0} is {1}", t.TransactionInformation.DistributedIdentifier, t.TransactionInformation.Status);  
                }  
            }  
        }  
  
    }  
    ```  
  
     這是一種原生活動，該活動可顯示環境異動的相關資訊，而且可同時用於本主題中所使用的服務和用戶端工作流程。 生成解決方案以使此活動在**工具箱**的 **"通用**"部分可用。  
  
### <a name="implement-the-workflow-service"></a>實作工作流程服務  
  
1. 添加新的 WCF 工作流服務，`WorkflowService`該服務調用`Common`到專案中。 要執行此操作，`Common`請按一下專案，選擇 **"添加**"**新專案..."，"** 在**已安裝範本**下選擇**工作流**"並選擇**WCF 工作流服務**。  
  
     ![加入工作流程服務](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. 刪除預設的 `ReceiveRequest` 和 `SendResponse` 活動。  
  
3. 將 <xref:System.Activities.Statements.WriteLine> 活動拖放到 `Sequential Service` 活動中。 將文字屬性設定為 `"Workflow Service starting ..."`，如下列範例所示。  
  
     !•將 WriteLine 活動添加到順序服務活動（./媒體/流式事務-進入和退出工作流服務/添加-寫入行-順序服務.jpg）  
  
4. 將 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 拖放到 <xref:System.Activities.Statements.WriteLine> 活動後面。 活動<xref:System.ServiceModel.Activities.TransactedReceiveScope>可以在**工具箱**的 **"消息"** 部分中找到。 活動<xref:System.ServiceModel.Activities.TransactedReceiveScope>由**請求**和**正文**兩個部分組成。 "**請求**"部分包含活動<xref:System.ServiceModel.Activities.Receive>。 **"正文"** 部分包含在收到消息後要在事務內執行的活動。  
  
     ![加入 TransactedReceiveScope 活動](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. 選擇活動<xref:System.ServiceModel.Activities.TransactedReceiveScope>並按一下 **"變數"** 按鈕。 加入下列變數。  
  
     ![向交易接收範圍添加變數](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > 根據預設，您可以刪除現有的資料變數。 您也可以使用現有的控制碼變數。  
  
6. 在<xref:System.ServiceModel.Activities.Receive><xref:System.ServiceModel.Activities.TransactedReceiveScope>活動的 **"請求"** 部分中拖放活動。 設定下列屬性：  
  
    |屬性|值|  
    |--------------|-----------|  
    |CanCreateInstance|True (核取此核取方塊)|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     工作流程的外觀應該如下圖所示：  
  
     ![加入 Receive 活動](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. 按一下<xref:System.ServiceModel.Activities.Receive>活動中的 **"定義..."** 連結並設置以下設置：  
  
     ![為"接收"活動設置消息設置](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. 將 <xref:System.Activities.Statements.Sequence> 活動拖放到 <xref:System.ServiceModel.Activities.TransactedReceiveScope> 的 [主體] 區段內。 拖放 <xref:System.Activities.Statements.Sequence> 活動內的兩個 <xref:System.Activities.Statements.WriteLine> 活動，並設定 <xref:System.Activities.Statements.WriteLine.Text%2A> 屬性，如下列範例所示。  
  
    |活動|值|  
    |--------------|-----------|  
    |第一個 WriteLine|"服務：接收已完成"|  
    |第二個 WriteLine|"Service: Received = " + requestMessage|  
  
     工作流程的外觀現在應該如下圖所示：  
  
     ![添加寫入行活動後的序列](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. `PrintTransactionInfo` <xref:System.Activities.Statements.WriteLine>在<xref:System.ServiceModel.Activities.TransactedReceiveScope>**活動中的"正文"** 中的第二個活動之後，拖放活動。  
  
     ![添加列印交易資訊後的順序](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. 將 <xref:System.Activities.Statements.Assign> 活動拖放到 `PrintTransactionInfo` 活動後面，然後根據下表設定其屬性。  
  
    |屬性|值|  
    |--------------|-----------|  
    |至|replyMessage|  
    |值|"Service: Sending reply."|  
  
11. 將 <xref:System.Activities.Statements.WriteLine> 活動拖放到 <xref:System.Activities.Statements.Assign> 活動後面，並將其 <xref:System.Activities.Statements.WriteLine.Text%2A> 屬性設定為 "Service: Begin reply"。  
  
     工作流程的外觀現在應該如下圖所示：  
  
     ![加入 Assign 和 WriteLine 之後](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. 按右鍵<xref:System.ServiceModel.Activities.Receive>活動並選擇 **"創建發送回復"，** 並在上次<xref:System.Activities.Statements.WriteLine>活動後粘貼。 按一下`SendReplyToReceive`活動中的 **"定義..."** 連結，然後進行以下設置。  
  
     ![回覆訊息設定](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. 在<xref:System.Activities.Statements.WriteLine>`SendReplyToReceive`活動後拖放活動並將其<xref:System.Activities.Statements.WriteLine.Text%2A>屬性設置為"服務：已發送回復"。  
  
14. 將 <xref:System.Activities.Statements.WriteLine> 活動拖放到工作流程的底部，然後將其 <xref:System.Activities.Statements.WriteLine.Text%2A> 屬性設定為 "Service: Workflow ends, press ENTER to exit"。  
  
     完成的服務工作流程外觀應該如下圖所示：  
  
     ![完成服務工作流程](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>實作工作流程用戶端  
  
1. 將稱為 `WorkflowClient` 的新 WCF 工作流程應用程式加入至 `Common` 專案。 要執行此操作，`Common`請按一下專案，選擇 **"添加****"新專案..."，"** 在**已安裝範本**下選擇**工作流**並選擇**活動**"。  
  
     ![加入 [活動] 專案](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. 將 <xref:System.Activities.Statements.Sequence> 活動拖放至設計介面上。  
  
3. 拖放 <xref:System.Activities.Statements.Sequence> 活動內的 <xref:System.Activities.Statements.WriteLine> 活動，並將其 <xref:System.Activities.Statements.WriteLine.Text%2A> 屬性設定為 `"Client: Workflow starting"`。 工作流程的外觀現在應該如下圖所示：  
  
     ![加入 WriteLine 活動](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. 將 <xref:System.Activities.Statements.TransactionScope> 活動拖放到 <xref:System.Activities.Statements.WriteLine> 活動後面。  選取 <xref:System.Activities.Statements.TransactionScope> 活動，按一下 [變數] 按鈕，然後加入下列變數。  
  
     ![將變數加入至 TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. 將 <xref:System.Activities.Statements.Sequence> 活動拖放到 <xref:System.Activities.Statements.TransactionScope> 活動的主體內。  
  
6. 將 `PrintTransactionInfo` 活動拖放到 <xref:System.Activities.Statements.Sequence> 內  
  
7. 在<xref:System.Activities.Statements.WriteLine>`PrintTransactionInfo`活動後拖放活動並將其<xref:System.Activities.Statements.WriteLine.Text%2A>屬性設置為"用戶端：開始發送"。 工作流程的外觀現在應該如下圖所示：  
  
     ![添加用戶端：開始發送活動](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. 將 <xref:System.ServiceModel.Activities.Send> 活動拖放到 <xref:System.Activities.Statements.Assign> 活動後面，然後設定下列屬性：  
  
    |屬性|值|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     工作流程的外觀現在應該如下圖所示：  
  
     ![設定 Send 活動屬性](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. 按一下 **"定義..."** 連結並設置以下設置：  
  
     ![傳送活動訊息設定](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. 按右鍵<xref:System.ServiceModel.Activities.Send>活動並選擇 **"創建接收回複**"。 <xref:System.ServiceModel.Activities.ReceiveReply> 活動將會自動放在 <xref:System.ServiceModel.Activities.Send> 活動後面。  
  
11. 按一下 ReceiveReplyForSend 活動中的 [定義] 連結，然後進行下列設定：  
  
     ![設定 ReceiveForSend 訊息設定](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. 將 <xref:System.Activities.Statements.WriteLine> 活動拖放到 <xref:System.ServiceModel.Activities.Send> 和 <xref:System.ServiceModel.Activities.ReceiveReply> 活動之間，然後將其 <xref:System.Activities.Statements.WriteLine.Text%2A> 屬性設定為 "Client: Send complete"。  
  
13. 將 <xref:System.Activities.Statements.WriteLine> 活動拖放到 <xref:System.ServiceModel.Activities.ReceiveReply> 活動後面，並將其 <xref:System.Activities.Statements.WriteLine.Text%2A> 屬性設定為 "Client side: Reply received = " + replyMessage  
  
14. 將 `PrintTransactionInfo` 活動拖放到 <xref:System.Activities.Statements.WriteLine> 活動後面。  
  
15. 將 <xref:System.Activities.Statements.WriteLine> 活動拖放到工作流程的結尾，然後將其 <xref:System.Activities.Statements.WriteLine.Text%2A> 屬性設定為 "Client workflow ends"。 完成的工作流程外觀應該如下圖所示。  
  
     ![已完成的用戶端工作流](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. 建置方案。  
  
### <a name="create-the-service-application"></a>建立服務應用程式  
  
1. 將稱為 `Service` 的新主控台應用程式專案加入至方案。 加入下列組件的參考：  
  
    1. System.Activities.dll  
  
    2. System.ServiceModel.dll  
  
    3. System.ServiceModel.Activities.dll  
  
2. 開啟產生的 Program.cs 檔案以及下列程式碼：  
  
    ```csharp
          static void Main()  
          {  
              Console.WriteLine("Building the server.");  
              using (WorkflowServiceHost host = new WorkflowServiceHost(new DeclarativeServiceWorkflow(), new Uri("net.tcp://localhost:8000/TransactedReceiveService/Declarative")))  
              {
                  //Start the server  
                  host.Open();  
                  Console.WriteLine("Service started.");  
  
                  Console.WriteLine();  
                  Console.ReadLine();  
                  //Shutdown  
                  host.Close();  
              };
          }  
    ```  
  
3. 將下列 app.config 檔案加入至專案。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <!-- Copyright © Microsoft Corporation.  All rights reserved. -->  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding transactionFlow="true" />  
                </netTcpBinding>  
            </bindings>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="create-the-client-application"></a>建立用戶端應用程式  
  
1. 將稱為 `Client` 的新主控台應用程式專案加入至方案。 將參考加入到 System.Activities.dll。  
  
2. 開啟 program.cs 檔案並加入下列程式碼。  
  
    ```csharp
    class Program  
    {  

        private static AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
        static void Main(string[] args)  
        {  
            //Build client  
            Console.WriteLine("Building the client.");  
            WorkflowApplication client = new WorkflowApplication(new DeclarativeClientWorkflow());  
            client.Completed = Program.Completed;  
            client.Aborted = Program.Aborted;  
            client.OnUnhandledException = Program.OnUnhandledException;  
            //Wait for service to start  
            Console.WriteLine("Press ENTER once service is started.");  
            Console.ReadLine();  
  
            //Start the client
            Console.WriteLine("Starting the client.");  
            client.Run();  
            syncEvent.WaitOne();  
  
            //Sample complete  
            Console.WriteLine();  
            Console.WriteLine("Client complete. Press ENTER to exit.");  
            Console.ReadLine();  
        }  
  
        private static void Completed(WorkflowApplicationCompletedEventArgs e)  
        {  
            Program.syncEvent.Set();  
        }  
  
        private static void Aborted(WorkflowApplicationAbortedEventArgs e)  
        {  
            Console.WriteLine("Client Aborted: {0}", e.Reason);  
            Program.syncEvent.Set();  
        }  
  
        private static UnhandledExceptionAction OnUnhandledException(WorkflowApplicationUnhandledExceptionEventArgs e)  
        {  
            Console.WriteLine("Client had an unhandled exception: {0}", e.UnhandledException);  
            return UnhandledExceptionAction.Cancel;  
        }  
    }  
    ```  
  
## <a name="see-also"></a>另請參閱

- [工作流服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Windows Communication Foundation 異動概觀](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
