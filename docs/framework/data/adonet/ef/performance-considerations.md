---
title: "效能考量 (Entity Framework)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61913f3b-4f42-4d9b-810f-2a13c2388a4a
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0f03a82c2164eac489a568ff4c0f3f9c55cf4326
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="performance-considerations-entity-framework"></a>效能考量 (Entity Framework)
本主題說明 ADO.NET Entity Framework 的效能特性，並提供一些考量因素以協助提升 Entity Framework 應用程式的效能。  
  
## <a name="stages-of-query-execution"></a>查詢執行的階段  
 為進一步了解 Entity Framework 中的查詢效能，了解針對概念模型執行查詢並傳回資料做為物件時發生的作業，對您有所幫助。 以下資料表說明這一系列的作業。  
  
|運算|相對成本|頻率|註解|  
|---------------|-------------------|---------------|--------------|  
|載入中繼資料|一般|在每個應用程式定義域中執行一次。|Entity Framework 使用的模型和對應中繼資料會載入至 <xref:System.Data.Metadata.Edm.MetadataWorkspace>。 這個中繼資料會在全域中作快取，並在相同的應用程式定義域中，提供給其他 <xref:System.Data.Objects.ObjectContext> 執行個體使用。|  
|開啟資料庫連接|Moderate<sup>1</sup>|需要時。|資料庫的開啟連接會消耗寶貴的資源，因為[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]開啟和關閉資料庫連接，只有在必要時。 您也可以明確開啟連接。 如需詳細資訊，請參閱[管理連接與交易](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)。|  
|產生檢視|High|在每個應用程式定義域中執行一次。 (可以預先產生。)|在 Entity Framework 可以針對概念模型執行查詢，或儲存變更至資料來源之前，Entity Framework 必須產生本地查詢檢視集，才能存取資料庫。 由於產生這些檢視的成本很高，您可以預先產生檢視，在設計階段就把這些檢視加入至專案。 如需詳細資訊，請參閱[How to: Pre-Generate 檢視，以改善查詢效能](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579)。|  
|準備查詢|Moderate<sup>2</sup>|針對每個唯一查詢執行一次。|包括組成查詢命令、根據模型和對應的中繼資料產生命令樹，以及定義傳回資料的形式等成本。 由於現在會快取 Entity SQL 查詢命令和 LINQ 查詢，因此後續執行相同查詢時可減少些許時間。 之後執行時您仍可以使用已編譯的 LINQ 查詢減少這種成本，且已編譯查詢可能比自動快取的 LINQ 查詢更有效率。 如需詳細資訊，請參閱[編譯的查詢 (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md)。 如需 LINQ 查詢執行的一般資訊，請參閱[LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)。 **注意：** LINQ to Entities 查詢適用於`Enumerable.Contains`記憶體中集合的運算子不會自動快取。 此外也不允許在已編譯的 LINQ 查詢中參數化記憶體中的集合。|  
|執行查詢|Low<sup>2</sup>|針對每個查詢執行一次。|使用 ADO.NET 資料提供者，針對資料來源執行命令的成本。 由於大部分的資料來源都會對查詢計畫作快取，後續執行相同查詢命令可能會減少些許時間。|  
|載入和使用型別|Low<sup>3</sup>|針對每個 <xref:System.Data.Objects.ObjectContext> 執行個體執行一次。|載入型別，並針對概念模型定義的型別進行驗證。|  
|追蹤|Low<sup>3</sup>|針對每個查詢傳回的物件執行一次。 <sup>4</sup>|如果查詢使用 <xref:System.Data.Objects.MergeOption.NoTracking> 合併選項，這個階段不會影響效能。<br /><br /> 如果查詢使用 <xref:System.Data.Objects.MergeOption.AppendOnly>、<xref:System.Data.Objects.MergeOption.PreserveChanges> 或 <xref:System.Data.Objects.MergeOption.OverwriteChanges> 合併選項，會在 <xref:System.Data.Objects.ObjectStateManager> 中追蹤查詢結果。 針對查詢傳回的每一個已追蹤物件產生 <xref:System.Data.EntityKey>，並用來建立 <xref:System.Data.Objects.ObjectStateEntry> 中的 <xref:System.Data.Objects.ObjectStateManager>。 如果可以針對 <xref:System.Data.Objects.ObjectStateEntry>，找到現有的 <xref:System.Data.EntityKey>，則會回傳現有的物件。 如果使用 <xref:System.Data.Objects.MergeOption.PreserveChanges> 或 <xref:System.Data.Objects.MergeOption.OverwriteChanges> 選項，傳回前會先更新物件。<br /><br /> 如需詳細資訊，請參閱[識別解析、 狀態管理和變更追蹤](http://msdn.microsoft.com/en-us/3bd49311-0e72-4ea4-8355-38fe57036ba0)。|  
|具體化物件|Moderate<sup>3</sup>|針對每個查詢傳回的物件執行一次。 <sup>4</sup>|讀取傳回之 <xref:System.Data.Common.DbDataReader> 物件、建立物件和設定屬性值的程序，是根據 <xref:System.Data.Common.DbDataRecord> 類別之每一個執行個體上的值。 如果物件已於 <xref:System.Data.Objects.ObjectContext> 中存在，且查詢使用 <xref:System.Data.Objects.MergeOption.AppendOnly> 或 <xref:System.Data.Objects.MergeOption.PreserveChanges> 合併選項，則這個階段不會影響效能。 如需詳細資訊，請參閱[識別解析、 狀態管理和變更追蹤](http://msdn.microsoft.com/en-us/3bd49311-0e72-4ea4-8355-38fe57036ba0)。|  
  
 <sup>1</sup>開啟連接的成本，當資料來源提供者實作連接共用時，都會分散到集區。 SQL Server 的 .NET 提供者支援連接共用。  
  
 <sup>2</sup>成本會隨著增加的查詢的複雜性。  
  
 <sup>3</sup>總成本會增加查詢所傳回的物件數目成正比。  
  
 <sup>4</sup>針對 EntityClient 查詢因為 EntityClient 查詢傳回，不需要這項負擔<xref:System.Data.EntityClient.EntityDataReader>而不是物件。 如需詳細資訊，請參閱[Entity Framework 的 EntityClient 提供者](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)。  
  
## <a name="additional-considerations"></a>其他考量  
 下列其他考量可能會影響 Entity Framework 應用程式的效能。  
  
### <a name="query-execution"></a>查詢執行  
 由於查詢可能會耗用資源，請考量查詢在程式碼裡的執行點，以及在哪部電腦上執行。  
  
#### <a name="deferred-versus-immediate-execution"></a>延後執行與立即執行  
 建立 <xref:System.Data.Objects.ObjectQuery%601> 或 LINQ 查詢時，可能不會立即執行查詢。 查詢執行會延後，直到需要結果時才執行，例如在 `foreach` (C#) 或 `For Each` (Visual Basic) 列舉期間，或指定填滿 <xref:System.Collections.Generic.List%601> 集合時。 呼叫 <xref:System.Data.Objects.ObjectQuery%601.Execute%2A> 上的 <xref:System.Data.Objects.ObjectQuery%601> 方法，或呼叫會傳回單一查詢的 LINQ 方法 (例如 <xref:System.Linq.Enumerable.First%2A> 或 <xref:System.Linq.Enumerable.Any%2A>) 時，會立即開始執行查詢。 如需詳細資訊，請參閱[物件查詢](http://msdn.microsoft.com/en-us/0768033c-876f-471d-85d5-264884349276)和[執行查詢 (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md)。  
  
#### <a name="client-side-execution-of-linq-queries"></a>LINQ 查詢的用戶端執行  
 雖然 LINQ 查詢的執行會發生在裝載資料來源的電腦上，一個 LINQ 查詢中的某些部分可以在用戶端電腦上進行評估。 如需詳細資訊，請參閱 > 一節存放區執行[執行查詢 (LINQ to Entities)](../../../../../docs/framework/data/adonet/ef/language-reference/query-execution.md)。  
  
### <a name="query-and-mapping-complexity"></a>查詢和對應複雜度  
 在實體模型中，個別查詢和對應的複雜度對於查詢的效能有重大影響。  
  
#### <a name="mapping-complexity"></a>對應複雜度  
 在概念模型中的實體以及儲存體模型中的資料表之間，擁有比簡單的一對一對應更複雜的模型，因此，所產生的命令比擁有一對一對應的模型更複雜。  
  
#### <a name="query-complexity"></a>查詢複雜度  
 在命令中需要大量聯結的查詢會針對資料來源進行執行，否則傳回的大量資料可能會以下列方式影響效能：  
  
-   針對概念模型進行的查詢看似簡單，但可能會導致針對資料來源執行更複雜的查詢。 發生這個問題的原因是 Entity Framework 會將針對概念模型的查詢轉譯為針對資料來源的同等查詢。 當概念模型中的單一實體集對應至資料來源中一個以上的資料表，或當實體之間的關聯性對應至聯結資料表時，針對資料來源查詢執行的查詢命令可能需要一個以上的聯結。  
  
    > [!NOTE]
    >  請使用 <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> 的 <xref:System.Data.Objects.ObjectQuery%601> 方法或 <xref:System.Data.EntityClient.EntityCommand> 類別，檢視針對資料來源而執行之指定查詢的命令。 如需詳細資訊，請參閱[如何： 檢視存放區命令](http://msdn.microsoft.com/en-us/f9771c6e-3b62-4b24-a5d4-55d68e14fa79)。  
  
-   巢狀 Entity SQL 查詢可在伺服器上建立聯結，並傳回大量資料列。  
  
     下列是投影子句中巢狀查詢的範例：  
  
    ```  
    SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2   
        FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1   
        FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
    ```  
  
     此外，這類查詢會使查詢管線產生單一查詢，並重複跨巢狀查詢的物件。 因此，單一資料行可能會重複多次。 在某些些資料庫上 (包括 SQL Server)，這個工作會使 TempDB 資料表變得非常大，降低伺服器的效能。 您執行巢狀查詢時應特別注意。  
  
-   如果用戶端正在執行耗用資源與結果集大小成正比的作業，任何傳回大量資料的查詢可能會使效能降低。 在這種情況下，您應該考慮依查詢限制傳回的資料量。 如需詳細資訊，請參閱[How to： 頁面透過查詢結果](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)。  
  
 由 Entity Framework 自動產生的任何命令，會比由資料庫開發人員明確撰寫的類似命令更為複雜。 如果您需要明確控制針對資料來源執行的命令，請考慮資料表值函式的對應或預存程序。  
  
#### <a name="relationships"></a>關聯性  
 為最佳化查詢效能，您必須定義實體 (作為實體模型中的關聯和資料來源中的邏輯關聯性) 之間的關聯性，。  
  
### <a name="query-paths"></a>查詢路徑  
 根據預設，執行 <xref:System.Data.Objects.ObjectQuery%601> 時，不會傳回相關物件 (即使物件表示關聯性本身)。 您可以利用下列三種方法中的任何一種方式載入相關物件：  
  
1.  在執行 <xref:System.Data.Objects.ObjectQuery%601> 之前設定查詢路徑。  
  
2.  在物件公開的導覽屬性上呼叫 `Load` 方法。  
  
3.  將 <xref:System.Data.Objects.ObjectContextOptions.LazyLoadingEnabled%2A> 上的 <xref:System.Data.Objects.ObjectContext> 選項設定為 `true`。 請注意，這是自動產生物件層程式碼時[Entity Data Model Designer](http://msdn.microsoft.com/en-us/4ccd7ad6-b934-4f7c-82a0-cfd2d4a95faf)。 如需詳細資訊，請參閱[產生程式碼概觀](http://msdn.microsoft.com/en-us/6a88ea38-6a90-4107-bc33-531b79ce5b6a)。  
  
 考慮要使用哪一種方式時，請特別留意，在對資料庫要求的數目與單一查詢所傳回的資料量之間，必須有所取捨。 如需詳細資訊，請參閱[載入相關物件](http://msdn.microsoft.com/en-us/452347d2-7b3b-44cd-9001-231299a28cb1)。  
  
#### <a name="using-query-paths"></a>使用查詢路徑  
 查詢路徑會定義查詢傳回的物件圖形。 定義查詢路徑時，只需針對資料庫進行單一要求，即可傳回此路徑定義的所有物件。 使用查詢路徑可能會使表面上簡單的物件查詢變成要針對資料來源執行複雜的命令。 發生這種情況是因為必須進行一或多次聯結才能在單一查詢中傳回相關物件。 在針對複雜實體模型 (例如具有繼承的實體或包含多對多關聯性的路徑) 的查詢中，這種複雜性會變得更大。  
  
> [!NOTE]
>  使用 <xref:System.Data.Objects.ObjectQuery.ToTraceString%2A> 方法可查看將會由 <xref:System.Data.Objects.ObjectQuery%601> 產生的命令。 如需詳細資訊，請參閱[如何： 檢視存放區命令](http://msdn.microsoft.com/en-us/f9771c6e-3b62-4b24-a5d4-55d68e14fa79)。  
  
 如果查詢路徑包含太多相關物件，或是物件包含太多資料列資料，資料來源可能會無法完成查詢。 如果查詢需要超過資料來源能力的中繼暫時儲存體，就會發生這種情況。 發生這種情況時，請明確載入相關物件來降低資料來源查詢的複雜性。  
  
#### <a name="explicitly-loading-related-objects"></a>明確載入相關物件  
 您可以呼叫傳回 `Load` 之導覽屬性上的 <xref:System.Data.Objects.DataClasses.EntityCollection%601> 方法，或是呼叫 <xref:System.Data.Objects.DataClasses.EntityReference%601>，以明確載入相關物件。 明確載入物件必須在每次呼叫 `Load` 時反覆存取資料庫一次。  
  
> [!NOTE]
>  在傳回的物件集合中執行迴圈時，如果呼叫 `Load`，例如使用 `foreach` 陳述式時 (Visual Basic 中的 `For Each`)，資料來源特定的提供者必須支援單一連接上的多個作用中結果集。 若為 SQL Server 資料庫，您必須在提供者連接字串中指定 `MultipleActiveResultSets = true` 的值。  
  
 當實體上沒有 <xref:System.Data.Objects.ObjectContext.LoadProperty%2A> 或 <xref:System.Data.Objects.DataClasses.EntityCollection%601> 屬性時，您也可以使用 <xref:System.Data.Objects.DataClasses.EntityReference%601> 方法。 這在您使用 POCO 實體時很有用。  
  
 雖然明確載入相關物件將降低聯結數量和多餘資料量，`Load` 卻需要重複的資料庫連接，當明確載入大量物件時，這可能會耗用大量成本。  
  
### <a name="saving-changes"></a>儲存變更  
 呼叫 <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> 上的 <xref:System.Data.Objects.ObjectContext> 方法時，會針對內容中每一個已加入、已更新或已刪除的物件，產生另一個建立、更新或刪除的命令。 這些命令會在單一交易中的資料來源上執行。 若含有查詢，建立、更新和刪除作業的效能會依概念模型中對應的複雜度而有所不同。  
  
### <a name="distributed-transactions"></a>分散式異動  
 在明確交易中，需要由分散式交易協調器 (DTC) 管理之資源的作業，會比不需要 DTC 的相似作業耗用更多成本。 提升至 DTC 會發生以下狀況：  
  
-   包含針對 SQL Server 2000 資料庫或其他資料來源之作業的明確交易，永遠會將明確交易提升至 DTC。  
  
-   當連接是由 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 管理時，會執行包含針對 SQL Server 2005 之作業的明確交易。 發生這種情況，是因為每當單一交易內的連接關閉又重新開啟時，SQL Server 2005 會提升至 DTC，這是 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 的預設行為。 使用 SQL Server 2008 就不會發生 DTC 提升。 若要在使用 SQL Server 2005 時防止這個問題發生，您必須明確開啟和關閉異動內的連接。 如需詳細資訊，請參閱[管理連接與交易](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)。  
  
 當一個或多個作業在 <xref:System.Transactions> 交易內執行時，會使用明確交易。 如需詳細資訊，請參閱[管理連接與交易](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)。  
  
## <a name="strategies-for-improving-performance"></a>提升效能的策略  
 您可以利用下列策略，改善 Entity Framework 中查詢的整體效能。  
  
#### <a name="pre-generate-views"></a>預先產生檢視  
 應用程式第一次執行查詢時，根據實體模型產生檢視會耗用大量成本。 請使用 EdmGen.exe 公用程式，預先產生做為 Visual Basic 或 C# 程式碼檔案的檢視表，在設計期間就可以加入至專案中。 您也可以使用文字範本轉換工具組來產生預先編譯的檢視表。 預先產生的檢視表會在執行階段進行驗證，以確保與指定之實體模型的目前版本一致。 如需詳細資訊，請參閱[How to: Pre-Generate 檢視，以改善查詢效能](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579)和[隔離效能與先行編譯/前 generated 檢視 Entity Framework 4 中](http://go.microsoft.com/fwlink/?LinkID=201337&clcid=0x409)。  
  
 當您處理非常大的模型時，必須考量以下事項：  
  
 .NET 中繼資料格式會將給定二進位格式的使用者字串字元數目限制為 16,777,215 (0xFFFFFF)。 如果您要產生極大的模型的檢視，而且檢視表檔案到達這個大小限制，您會收到 「 沒有剩餘的邏輯空間來建立更多使用者字串。 」 編譯錯誤。 這個大小限制適用於所有 Managed 二進位檔。 如需詳細資訊，請參閱[部落格](http://go.microsoft.com/fwlink/?LinkId=201476)示範了如何使用大型且複雜的模型時避免錯誤。  
  
#### <a name="consider-using-the-notracking-merge-option-for-queries"></a>考慮針對查詢使用 NoTracking 合併選項  
 追蹤在物件內容中傳回的物件是必要成本。 偵測物件的變更，並確保相同邏輯實體的多個要求能傳回相同物件執行個體，需要將物件附加至 <xref:System.Data.Objects.ObjectContext> 執行個體。 如果沒有更新或刪除物件的計畫，且不需要識別管理，則執行查詢時，請考慮使用 <xref:System.Data.Objects.MergeOption.NoTracking> 合併選項。  
  
#### <a name="return-the-correct-amount-of-data"></a>傳回正確的資料量  
 在某些情況下，<xref:System.Data.Objects.ObjectQuery%601.Include%2A> 方法指定查詢路徑會比較快速，因為需要反覆存取資料庫的次數較少。 不過，在其他情況下，額外反覆存取資料庫以載入相關物件可能會比較快速，因為較簡單的查詢加上較少的聯結，可產生較少的資料重複。 因此，我們建議您測試各種不同的擷取相關物件方法。 如需詳細資訊，請參閱[載入相關物件](http://msdn.microsoft.com/en-us/452347d2-7b3b-44cd-9001-231299a28cb1)。  
  
 若要防止單一查詢傳回太多資料，請考慮將查詢結果分頁成多個可管理的群組。 如需詳細資訊，請參閱[How to： 頁面透過查詢結果](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)。  
  
#### <a name="limit-the-scope-of-the-objectcontext"></a>限制 ObjectContext 的範圍  
 在大多數的情況下，您應該在 <xref:System.Data.Objects.ObjectContext> 陳述式 (Visual Basic 中的 `using`) 中，建立 `Using…End Using` 執行個體。 確保當程式碼存在陳述式區塊時，與物件內容關聯的資源會自動公開，這麼做可以提高效能。 不過，當控制項繫結至由物件內容管理的物件時，只要繫結是必要且為手動公開的，則應維護 <xref:System.Data.Objects.ObjectContext> 執行個體。 如需詳細資訊，請參閱[管理連接與交易](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)。  
  
#### <a name="consider-opening-the-database-connection-manually"></a>考慮手動開啟資料庫連接  
 當您的應用程式執行一系列的物件查詢，或是經常呼叫<xref:System.Data.Objects.ObjectContext.SaveChanges%2A>保存建立、 更新和刪除資料來源，作業[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]必須不斷開啟和關閉資料來源的連接。 在這些情況下，請考慮在這些連接開始時，手動開啟連接，然後當作業完成時，關閉或處置連接。 如需詳細資訊，請參閱[管理連接與交易](http://msdn.microsoft.com/en-us/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)。  
  
## <a name="performance-data"></a>效能資料  
 有些 Entity Framework 的效能資料發佈中的下列文章[ADO.NET 小組部落格](http://go.microsoft.com/fwlink/?LinkId=91905):  
  
-   [瀏覽 ADO.NET Entity Framework 的效能-第 1 部分](http://go.microsoft.com/fwlink/?LinkId=123907)  
  
-   [瀏覽 ADO.NET Entity Framework 的效能-第 2 部分](http://go.microsoft.com/fwlink/?LinkId=123909)  
  
-   [ADO.NET Entity Framework 效能比較](http://go.microsoft.com/fwlink/?LinkID=123913)  
  
## <a name="see-also"></a>請參閱  
 [開發和部署考量](../../../../../docs/framework/data/adonet/ef/development-and-deployment-considerations.md)
