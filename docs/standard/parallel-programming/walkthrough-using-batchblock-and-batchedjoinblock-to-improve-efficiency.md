---
title: 逐步解說：使用 BatchBlock 和 BatchedJoinBlock 以改善效率
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79bbf33ff1b1e843836aa1b93188970b6a1c8ede
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302971"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a>逐步解說：使用 BatchBlock 和 BatchedJoinBlock 以改善效率
TPL 資料流程程式庫提供 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> 類別，如此您可以接收來自一或多個來源的資料並緩衝，然後將該已緩衝的資料作為集合散佈。 這個批次機制在您從一或多個來源收集資料時非常實用，而且可接著批次處理多個資料元素。 例如，以使用資料流程將記錄插入資料庫的應用程式為例。 如果多個項目可以同時插入，而不是以循序方式逐一插入，這項作業就會更有效率。 本文件描述如何使用 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 類別來改善這類資料庫插入作業的效率。 文中也描述如何使用 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 類別，在程式從資料庫進行讀取時擷取結果以及所發生的任何例外狀況。

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a>必要條件  
  
1. 開始此逐步解說之前，請先閱讀[資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)文件中的＜聯結區塊＞一節。  
  
2. 確定您電腦上有可用的 Northwind 資料庫複本 (Northwind.sdf)。 這個檔案通常位於資料夾：%Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\。  
  
    > [!IMPORTANT]
    >  在某些 Windows 版本中，如果 Visual Studio 是以非系統管理員模式執行，就無法連線到 Northwind.sdf。 若要連線到 Northwind.sdf，請使用 [以系統管理員身分執行] 模式來啟動 Visual Studio 或 Visual Studio 開發人員命令提示字元。  
  
 本逐步解說包含下列各節：  
  
-   [建立主控台應用程式](#creating)  
  
-   [定義員工類別](#employeeClass)  
  
-   [定義員工資料庫作業](#operations)  
  
-   [不使用緩衝將員工資料新增至資料庫](#nonBuffering)  
  
-   [使用緩衝將員工資料新增至資料庫](#buffering)  
  
-   [使用緩衝聯結從資料庫讀取員工資料](#bufferedJoin)  
  
-   [完整範例](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a>建立主控台應用程式  
  
<a name="consoleApp"></a>   
1. 在 Visual Studio 中，建立 Visual C# 或 Visual Basic **主控台應用程式**專案。 在本文件中，專案命名為 `DataflowBatchDatabase`。  
  
2. 在您的專案中，加入 System.Data.SqlServerCe.dll 的參考，和 System.Threading.Tasks.Dataflow.dll 的參考。  
  
3. 確定 Form1.cs (在 Visual Basic 中為 Form1.vb) 包含下列 `using` (在 Visual Basic 中為 `Imports`) 陳述式。  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4. 將下列資料成員新增至 `Program` 類別。  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a>定義員工類別  
 將 `Employee` 類別加入至 `Program` 類別。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 `Employee` 類別包含三個屬性：`EmployeeID`、`LastName` 和 `FirstName`。 這些屬性對應至 Northwind 資料庫中 `Employees` 資料表的 `Employee ID`、`Last Name` 和 `First Name` 資料行。 在此示範中，`Employee` 類別也會定義 `Random` 方法，此方法會建立具有隨機屬性值的 `Employee` 物件。  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a>定義員工資料庫作業  
 將 `InsertEmployees`、`GetEmployeeCount` 和 `GetEmployeeID` 方法加入到 `Program` 類別。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 `InsertEmployees` 方法會將新的員工記錄新增到資料庫。 `GetEmployeeCount` 方法會擷取 `Employees` 資料表中的項目數量。 `GetEmployeeID` 方法會擷取具有所提供之名稱的第一位員工識別碼。 這些方法都採用針對 Northwind 資料庫的連接字串，並且使用 `System.Data.SqlServerCe` 命名空間中的功能與資料庫通訊。  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a>不使用緩衝將員工資料新增至資料庫  
 將 `AddEmployees` 和 `PostRandomEmployees` 方法加入到 `Program` 類別。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 `AddEmployees` 方法會使用資料流程，將隨機的員工資料新增到資料庫。 它會建立呼叫 `InsertEmployees` 方法的 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件，以將員工項目新增到資料庫。 然後，`AddEmployees` 方法會呼叫 `PostRandomEmployees` 方法，將多個 `Employee` 物件張貼到 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件。 `AddEmployees` 方法接著等候所有插入作業完成。  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a>使用緩衝將員工資料新增至資料庫  
 將 `AddEmployeesBatched` 方法加入至 `Program` 類別。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 這個方法類似於 `AddEmployees`，不同之處在於它也會使用 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 類別來緩衝多個 `Employee` 物件，然後才將那些物件傳送到 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件。 因為 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 類別將多個元素以集合方式散佈，因此要修改 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件以在 `Employee` 物件陣列上運作。 如同在 `AddEmployees` 方法中，`AddEmployeesBatched` 會呼叫 `PostRandomEmployees` 方法以張貼多個 `Employee` 物件。不過，`AddEmployeesBatched` 會將這些物件張貼到 <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> 物件。 `AddEmployeesBatched` 方法也會等候所有插入作業完成。  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a>使用緩衝聯結從資料庫讀取員工資料  
 將 `GetRandomEmployees` 方法加入至 `Program` 類別。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 此方法會將有關隨機員工的資訊列印至主控台。 它會建立數個隨機的 `Employee` 物件，並呼叫 `GetEmployeeID` 方法以擷取每個物件的唯一識別碼。 因為 `GetEmployeeID` 方法會在沒有符合指定之姓名的員工時擲回例外狀況，`GetRandomEmployees` 方法會使用 <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 類別來儲存呼叫 `GetEmployeeID` 成功時的 `Employee` 物件，以及呼叫失敗時的 <xref:System.Exception?displayProperty=nameWithType> 物件。 本範例中的 <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> 物件會作為保存 `Employee` 物件清單和 <xref:System.Exception> 物件清單的 <xref:System.Tuple%602> 物件。 當接收的 `Employee` 總和和 <xref:System.Exception> 物件計數與批次大小相等時，<xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> 物件會散佈此資料。  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a>完整範例  
 下列範例顯示完整程式碼。 `Main` 方法會比較執行批次資料庫插入作業所需的時間，與執行非批次資料庫插入作業所需的時間。 它也會示範緩衝聯結的使用方式，以從資料庫讀取員工資料，而且也會回報錯誤。  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a>另請參閱

- [資料流程](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
