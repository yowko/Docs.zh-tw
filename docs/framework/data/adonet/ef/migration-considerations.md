---
title: 移轉考量 (Entity Framework)
ms.date: 03/30/2017
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
ms.openlocfilehash: 3554f530acf0e3ca3e66dddf74f63e7ede03708e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248560"
---
# <a name="migration-considerations-entity-framework"></a>移轉考量 (Entity Framework)
ADO.NET Entity Framework 為現有的應用程式提供數個優點。 其中一項最重要的優勢，就是使用概念模型將應用程式所使用的資料結構從資料來源中的結構描述分隔。 這樣能方便您以後對儲存體模型或資料來源本身進行變更，而不必對應用程式進行補償變更。 如需使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]之優點的詳細資訊，請參閱[Entity Framework 總覽](overview.md)和[實體資料模型](../entity-data-model.md)。  
  
 若要利用的優點[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]，您可以將現有的應用程式遷移[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]至。 有些工作通用於所有移轉的應用程式。 這些常見的工作包括將應用程式升級為使用從3.5 版 Service Pack 1 （SP1）開始的 .NET Framework、定義模型和對應，以及設定 Entity Framework。 在將應用程式移轉至 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 的時候，有其他的適用考量。 這些考量取決於要移轉的應用程式類型以及應用程式的特定功能。 本主題所提供的資訊有助於您選擇在升級現有應用程式時要使用的最佳方式。  
  
## <a name="general-migration-considerations"></a>一般移轉考量  
 下列考量適用於將任何應用程式移轉至 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 的情況：  
  
- 只要應用程式所使用之資料來源的資料提供者支援 Entity Framework，任何使用從版本 3.5 SP1 開始之 .NET Framework 的應用程式都可以遷移至 Entity Framework。  
  
- Entity Framework 可能無法支援資料來源提供者的所有功能，即使那個提供者支援 Entity Framework 也一樣。  
  
- 針對大型或複雜應用程式，您不必一次將整個應用程式移轉至 Entity Framework， 但是資料來源變更時，還是要變更未使用 Entity Framework 的任何應用程式部分。  
  
- Entity Framework 所使用的資料提供者連接可以與應用程式的其他部分共用，因為[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]會使用 ADO.NET 的資料提供者來存取資料來源。 例如，Entity Framework 是使用 SqlClient 提供者進行存取 SQL Server 資料庫。 如需詳細資訊，請參閱[Entity Framework 的 EntityClient 提供者](entityclient-provider-for-the-entity-framework.md)。  
  
## <a name="common-migration-tasks"></a>通用移轉工作  
 移轉現有應用程式至 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 的途徑取決於應用程式的類型以及現有資料存取策略。 不過，在將現有應用程式移轉至 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 時，一律必須執行下列工作：  
  
> [!NOTE]
> 當您使用從 Visual Studio 2008 開始的實體資料模型工具時，會自動執行所有這些工作。 如需詳細資訊，請參閱[如何：使用實體資料模型 Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。  
  
1. 升級應用程式。  
  
     使用舊版 Visual Studio 和 .NET Framework 所建立的專案，必須先升級，才能使用 Visual Studio 2008 SP1 和從版本 3.5 SP1 開始的 .NET Framework。  
  
2. 定義模型與對應  
  
     模型和對應檔案定義概念模型中的實體、資料來源中的結構 (例如資料表、預存程序和檢視表)，以及實體與資料來源結構間的對應。 如需詳細資訊，請參閱[如何：手動定義模型和對應](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))檔。  
  
     儲存體模型中定義的類型必須與資料來源中物件的名稱相符。 如果現有應用程式將資料公開 (Expose) 為物件，您必須確保概念模型中定義的實體和屬性與這些現有資料類別和屬性的名稱相符。 如需詳細資訊，請參閱[如何：自訂模型和對應檔，以使用自](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738625(v=vs.100))定義物件。  
  
    > [!NOTE]
    > Entity Data Model Designer 可以用來重新命名概念模型中的實體，使其與現有物件相符。 如需詳細資訊，請參閱[實體資料模型設計](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100))工具。  
  
3. 定義連接字串 (Connection String)。  
  
     針對概念模型執行查詢時，[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 會使用特殊格式化的連接字串。 此連接字串會封裝與模型和對應檔以及資料來源連接有關的資訊。 如需詳細資訊，請參閱[如何：定義連接字串](how-to-define-the-connection-string.md)。  
  
4. 設定 Visual Studio 專案。  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]元件和模型和對應檔的參考必須加入至 Visual Studio 專案。 您可以將這些對應檔加入至專案，以確保它們與應用程式一起部署在連接字串中所指示的位置。 如需詳細資訊，請參閱[如何：手動設定 Entity Framework 專案](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))。  
  
## <a name="considerations-for-applications-with-existing-objects"></a>適用於具有現有物件的應用程式之考量  
 從 .NET Framework 4 開始， [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]支援「純舊」 CLR 物件（POCO），也稱為非持續性物件。 大部分的情況下，只要稍加變更您現有的物件，它們都能與 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 搭配使用。 如需詳細資訊，請參閱[使用 POCO 實體](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456853(v=vs.100))。 您也可以將應用程式遷移至[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ，並使用 Entity Framework 工具所產生的資料類別。 如需詳細資訊，請參閱[如何：使用實體資料模型 Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>適用於使用 ADO.NET 提供者的應用程式之考量  
 ADO.NET 提供者（例如 SqlClient）可讓您查詢資料來源以傳回表格式資料。 資料也可以載入至 ADO.NET 資料集。 下列清單描述升級使用現有 ADO.NET 提供者之應用程式的考慮：  
  
- 使用資料讀取器 (Reader) 顯示表格式資料。  

  您可以考慮使用 EntityClient [!INCLUDE[esql](../../../../../includes/esql-md.md)]提供者執行查詢，並透過傳回<xref:System.Data.EntityClient.EntityDataReader>的物件進行列舉。 只有在應用程式使用資料讀取器顯示表格式資料，而且不需要 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 提供的功能進行將資料具體化為物件、追蹤變更和處理更新時才這麼做。 您可以繼續使用對資料來源進行更新的現有資料存取程式碼，不過您可以使用從 <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> 的 <xref:System.Data.EntityClient.EntityConnection> 屬性存取的現有連接。 如需詳細資訊，請參閱[Entity Framework 的 EntityClient 提供者](entityclient-provider-for-the-entity-framework.md)。  
  
- 使用資料集。  

  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]提供了許多由資料集提供的相同功能，包括記憶體中的持續性、變更追蹤、資料系結，以及將物件序列化為 XML 資料。 如需詳細資訊，請參閱[使用物件](working-with-objects.md)。  
  
  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]如果未提供您應用程式所需的資料集功能，您仍然可以利用 LINQ to DataSet 使用 LINQ 查詢的優點。 如需詳細資訊，請參閱 [LINQ to DataSet](../linq-to-dataset.md)。  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>適用於將資料繫結至控制項的應用程式之考量  
 .NET Framework 可讓您封裝資料來源中的資料，例如 DataSet 或 ASP.NET 資料來源控制項，然後將使用者介面專案系結至這些資料控制項。 下列清單說明適用於將控制項繫結至 Entity Framework 資料的考量。  
  
- 將資料繫結至控制項。  

  當您查詢概念模型時， [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]會傳回資料做為實體類型實例的物件。 這些物件可以直接系結至控制項，而且此系結支援更新。 這表示在呼叫<xref:System.Windows.Forms.DataGridView> <xref:System.Data.Objects.ObjectContext.SaveChanges%2A>方法時，會自動將控制項中的資料變更（例如中的資料列）儲存至資料庫。  
  
  如果應用程式列舉查詢的結果，以在 <xref:System.Windows.Forms.DataGridView> 或其他支援資料繫結程序的控制項類型中顯示資料，您則可以把應用程式修改為將控制項繫結程序至 <xref:System.Data.Objects.ObjectQuery%601> 的結果。  
  
  如需詳細資訊，請參閱[將物件系結至控制項](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738469(v=vs.100))。  
  
- ASP.NET 資料來源控制項。  

  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]包含設計用來簡化 ASP.NET Web 應用程式中資料系結的資料來源控制項。 如需詳細資訊，請參閱[EntityDataSource Web 服務器控制項總覽](https://docs.microsoft.com/previous-versions/aspnet/cc488502(v=vs.100))。  
  
## <a name="other-considerations"></a>其他考量  
 下列考量可適用於將特定應用程式類型移轉至 Entity Framework 的情況。  
  
- 公開資料服務的應用程式。  

  以 Windows Communication Foundation (WCF) 為架構的 Web 服務和應用程式使用 XML 要求/回應訊息格式公開來自基礎資料來源的資料。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 使用二進位、XML 或 WCF 資料合約序列化 (Serialization) 支援實體物件的序列化。 二進位和 WCF 序列化都支援物件圖形的完整序列化。 如需詳細資訊，請參閱[建立多層式應用程式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896304(v=vs.100))。  
  
- 使用 XML 資料的應用程式。  

  物件序列化能讓您建立 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 資料服務。 這些服務為使用 XML 資料的應用程式提供資料，例如以 AJAX 為基礎的網際網路應用程式。 在這些情況下，請考慮使用 [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)]。 這些資料服務是以實體資料模型為基礎，並使用標準具像狀態傳輸（REST） HTTP 動作（例如 GET、PUT 和 POST）提供實體資料的動態存取。 如需詳細資訊，請參閱 [WCF Data Services 4.5](../../wcf/index.md)。  
  
  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 不支援原生 XML 資料型別， 亦即將實體對應至具有 XML 資料行的資料表時，XML 資料行的對等實體屬性會是字串。 您可以中斷物件的連接，而且將其序列化為 XML。 如需詳細資訊，請參閱序列化[物件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100))。  
  
  如果應用程式需要有查詢 XML 資料的功能，您還是可以使用 LINQ to XML 來善用 LINQ 查詢的優勢。 如需詳細資訊，請參閱[LINQ to XMLC#（）](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md)或[LINQ to XML （Visual Basic）](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)。  
  
- 維護狀態的應用程式。  

  ASP.NET Web 應用程式必須經常維護網頁或使用者會話的狀態。 <xref:System.Data.Objects.ObjectContext>實例中的物件可以儲存在用戶端檢視狀態或伺服器上的會話狀態中，並于稍後抓取並重新附加至新的物件內容。 如需詳細資訊，請參閱[附加和卸離物件](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896271(v=vs.100))。  
  
## <a name="see-also"></a>另請參閱

- [部署考量](deployment-considerations.md)
- [Entity Framework 詞彙](terminology.md)
