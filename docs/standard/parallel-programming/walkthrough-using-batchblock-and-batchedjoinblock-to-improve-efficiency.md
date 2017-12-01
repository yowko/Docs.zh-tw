---
title: "逐步解說：使用 BatchBlock 和 BatchedJoinBlock 以改善效率"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc74b4acc5b29395c05e7c8302caefeb51718282
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>逐步解說：使用 BatchBlock 和 BatchedJoinBlock 以改善效率
TPL 資料流程式庫提供<xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType>和<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType>類別，讓您可以接收與緩衝一或多個來源的資料，然後散佈該緩衝的資料，做為一個集合。 當您從一個或多個來源收集資料，然後以批次中處理多個資料元素，此批次處理機制是很有用。 例如，請考慮將記錄插入資料庫中使用資料流程的應用程式。 這項作業可以更有效率，如果多個項目會以循序方式插入在同一時間而非一次。 本文件說明如何使用<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>類別來改善效率的這類資料庫插入作業。 它也說明如何使用<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>類別來擷取結果和在程式讀取資料庫時，會發生任何例外狀況。  
  
> [!TIP]
>  TPL 資料流程程式庫 (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 命名空間) 並未隨附於 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]。 若要安裝<xref:System.Threading.Tasks.Dataflow>命名空間中，開啟您的專案中[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]，選擇**管理 NuGet 封裝**從 [專案] 功能表中，並在搜尋線上`Microsoft.Tpl.Dataflow`封裝。  
  
## <a name="prerequisites"></a>必要條件  
  
1.  讀取的聯結區塊 」 一節中[資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)開始這個逐步解說之前，先記錄。  
  
2.  確定您有一份 Northwind 資料庫，Northwind.sdf，在電腦上。 這個檔案通常位於資料夾 %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\。  
  
    > [!IMPORTANT]
    >  在某些版本的 Windows 中，您無法連接至 Northwind.sdf 如果[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]以非系統管理員模式執行。 若要連接到 Northwind.sdf，啟動[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]或[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]命令提示字元中**系統管理員身分執行**模式。  
  
 本逐步解說包含下列各節：  
  
-   [建立主控台應用程式](#creating)  
  
-   [定義 「 員工 」 類別](#employeeClass)  
  
-   [定義員工資料庫作業](#operations)  
  
-   [加入資料庫中的員工資料，而不需使用緩衝處理](#nonBuffering)  
  
-   [使用緩衝將員工資料加入至資料庫](#buffering)  
  
-   [若要從資料庫讀取的員工資料使用緩衝的聯結](#bufferedJoin)  
  
-   [完整範例](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a>建立主控台應用程式  
  
<a name="consoleApp"></a>   
1.  在[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]，建立 Visual C# 或 Visual Basic**主控台應用程式**專案。 在本文件中，專案命名為 `DataflowBatchDatabase`。  
  
2.  在您的專案，加入的參考 System.Data.SqlServerCe.dll 和 System.Threading.Tasks.Dataflow.dll 的參考。  
  
3.  確定 Form1.cs (為 Form1.vb [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) 包含下列`using`(`Imports`中[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) 陳述式。  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  將下列資料成員新增至 `Program` 類別。  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a>定義 「 員工 」 類別  
 若要新增`Program`類別`Employee`類別。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 `Employee`類別包含三個屬性， `EmployeeID`， `LastName`，和`FirstName`。 這些屬性對應於`Employee ID`， `Last Name`，和`First Name`中的資料行`Employees`Northwind 資料庫中的資料表。 此示範中，`Employee`類別也會定義`Random`方法，建立`Employee`有其內容的隨機值的物件。  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a>定義員工資料庫作業  
 若要新增`Program`類別`InsertEmployees`， `GetEmployeeCount`，和`GetEmployeeID`方法。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 `InsertEmployees`方法會將新員工記錄加入到資料庫。 `GetEmployeeCount`方法會擷取中的項目數`Employees`資料表。 `GetEmployeeID`方法會擷取具有所提供的名稱的第一個員工的識別碼。 每一種方法採用 Northwind 資料庫的連接字串，並使用中的功能`System.Data.SqlServerCe`命名空間與資料庫通訊。  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>加入資料庫中的員工資料，而不需使用緩衝處理  
 若要新增`Program`類別`AddEmployees`和`PostRandomEmployees`方法。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 `AddEmployees`方法使用資料流程會隨機員工資料加入至資料庫。 它會建立<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>物件呼叫`InsertEmployees`方法，將員工項目加入至資料庫。 `AddEmployees`方法接著呼叫`PostRandomEmployees`張貼多個方法`Employee`物件加入至<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>物件。 `AddEmployees`方法然後等候所有插入作業完成。  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a>使用緩衝將員工資料加入至資料庫  
 若要新增`Program`類別`AddEmployeesBatched`方法。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 這個方法類似於`AddEmployees`，不同之處在於它也會使用<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>要緩衝處理多個類別`Employee`物件傳送至這些物件之前<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>物件。 因為<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>類別散佈多個項目集合，做<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>物件遭到修改，在陣列上執行`Employee`物件。 在`AddEmployees`方法，`AddEmployeesBatched`呼叫`PostRandomEmployees`張貼多個方法`Employee`物件; 不過，`AddEmployeesBatched`張貼至這些物件<xref:System.Threading.Tasks.Dataflow.BatchBlock%601>物件。 `AddEmployeesBatched`方法也等候所有插入作業完成。  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>若要從資料庫讀取的員工資料使用緩衝的聯結  
 若要新增`Program`類別`GetRandomEmployees`方法。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 這個方法會列印到主控台的隨機員工的相關資訊。 它會建立數個隨機`Employee`物件並呼叫`GetEmployeeID`方法來擷取每個物件的唯一識別碼。 因為`GetEmployeeID`方法擲回例外狀況，如果沒有指定第一個和最後一個名稱，不符合員工`GetRandomEmployees`方法會使用<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>類別來儲存`Employee`成功呼叫的物件`GetEmployeeID`和<xref:System.Exception?displayProperty=nameWithType>失敗的呼叫的物件。 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>在此範例中的物件充當<xref:System.Tuple%602>保存一份物件`Employee`物件和一份<xref:System.Exception>物件。 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602>物件會散佈此資料時收到的總和`Employee`和<xref:System.Exception>物件計數等於批次大小。  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>完整範例  
 下列範例顯示完整程式碼。 `Main`方法會比較所需執行批次的資料庫插入執行非批次的資料庫插入的時間與時間。 它也會示範使用緩衝的聯結，可從資料庫讀取的員工資料，及也報告錯誤。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a>另請參閱  
 [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
