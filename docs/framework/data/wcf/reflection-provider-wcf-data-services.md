---
title: "反映提供者 (WCF 資料服務)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, providers
ms.assetid: ef5ba300-6d7c-455e-a7bd-d0cc6d211ad4
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52fe7e777cfea04b6da2a04c0badfe92b2a0a756
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="reflection-provider-wcf-data-services"></a>反映提供者 (WCF 資料服務)
除了透過 Entity Framework 從資料模型公開資料外，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 還可以公開在實體架構模型中未嚴格定義的資料。 反映提供者會公開類別中的資料，而這些類別會傳回實作 <xref:System.Linq.IQueryable%601> 介面的類型。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 使用反映來推斷這些類別的資料模型，而且可以針對資源將定址架構的查詢轉譯為 Language Integrated Query (LINQ) 架構的查詢 (針對已公開的 <xref:System.Linq.IQueryable%601> 類型)。  
  
> [!NOTE]
>  您可以使用 <xref:System.Linq.Queryable.AsQueryable%2A> 方法，從實作 <xref:System.Linq.IQueryable%601> 介面的任何類別傳回 <xref:System.Collections.Generic.IEnumerable%601> 介面。 這樣可將大部分的泛型集合類型做為資料服務的資料來源使用。  
  
 反映提供者支援型別階層。 如需詳細資訊，請參閱[How to： 建立資料服務，使用反映提供者](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)。  
  
## <a name="inferring-the-data-model"></a>推斷資料模型  
 當您建立資料服務時，提供者會使用反映推斷資料模型。 下列清單顯示反映提供者推斷資料模型的方式：  
  
-   實體容器：該類別可將資料公開為傳回 <xref:System.Linq.IQueryable%601> 執行個體的屬性。 當您定址反映架構的資料模型時，實體容器代表服務的根。 一個指定的命名空間僅支援一個實體容器類別。  
  
-   實體集：傳回 <xref:System.Linq.IQueryable%601> 執行個體的屬性會被視為實體集。 實體集會在查詢中直接定址為資源。 實體容器上只有一個屬性可以傳回指定型別的 <xref:System.Linq.IQueryable%601> 執行個體。  
  
-   實體型別：實體集所傳回之 `T` 的型別 <xref:System.Linq.IQueryable%601>。 反映提供者會將屬於繼承階層的類別轉譯為對等的實體類型階層。  
  
-   實體索引鍵：每個屬於實體類型的資料類別都必須具有一個索引鍵屬性。 此屬性會以 <xref:System.Data.Services.Common.DataServiceKeyAttribute> 屬性 (`[DataServiceKeyAttribute]`) 加以屬性化。  
  
    > [!NOTE]
    >  您應該只將 <xref:System.Data.Services.Common.DataServiceKeyAttribute> 屬性 (Attribute) 套用至可以用來唯一識別實體類型之執行個體的屬性 (Property)。 此屬性 (Attribute) 在套用到導覽屬性 (Property) 時會遭到忽略。  
  
-   實體類型屬性：除了實體索引鍵外，反映提供者會如下所示處理類別 (為實體類型) 的可存取非索引子屬性：  
  
    -   如果屬性傳回基本型別，則會假設該屬性為實體類型的屬性。  
  
    -   如果屬性傳回同時為實體類型的型別，則會假設該屬性為導覽屬性，代表多對一或一對一關聯性中的「一」端。  
  
    -   如果屬性傳回實體類型的 <xref:System.Collections.Generic.IEnumerable%601>，則會假設該屬性為導覽屬性，代表一對多或多對一關聯性中的「多」端。  
  
    -   如果屬性的傳回型別是實值型別，則該屬性就代表複雜類型。  
  
> [!NOTE]
>  不同於以實體關聯式模型為基礎的資料模型，以反映提供者為基礎的模型無法解譯關聯性資料。 您應該使用 Entity Framework 透過 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 公開關聯式資料。  
  
## <a name="data-type-mapping"></a>資料型別對應  
 若資料模型是從 .NET Framework 類別推斷的，資料模型中的基本型別會對應至 .NET Framework 資料型別，如下所示：  
  
|.NET Framework 資料型別|資料模型型別|  
|------------------------------|---------------------|  
|<xref:System.Byte> `[]`|`Edm.Binary`|  
|<xref:System.Boolean>|`Edm.Boolean`|  
|<xref:System.Byte>|`Edm.Byte`|  
|<xref:System.DateTime>|`Edm.DateTime`|  
|<xref:System.Decimal>|`Edm.Decimal`|  
|<xref:System.Double>|`Edm.Double`|  
|<xref:System.Guid>|`Edm.Guid`|  
|<xref:System.Int16>|`Edm.Int16`|  
|<xref:System.Int32>|`Edm.Int32`|  
|<xref:System.Int64>|`Edm.Int64`|  
|<xref:System.SByte>|`Edm.SByte`|  
|<xref:System.Single>|`Edm.Single`|  
|<xref:System.String>|`Edm.String`|  
  
> [!NOTE]
>  .NET Framework 可為 Null 的值型別會對應至相同的資料模型類型，當成無法指派 Null 之對應值型別。  
  
## <a name="enabling-updates-in-the-data-model"></a>可在資料模型中更新  
 為允許更新透過此類資料模型公開的資料，反映提供者會定義 <xref:System.Data.Services.IUpdatable> 介面。 此介面會指示資料服務持續更新已公開型別的方法。 若要更新資料模型定義的資源，實體容器類別必須實作 <xref:System.Data.Services.IUpdatable> 介面。 如需範例實作的<xref:System.Data.Services.IUpdatable>介面，請參閱[How to： 建立使用資料服務的 LINQ to SQL 資料來源](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)。  
  
 必須實作 <xref:System.Data.Services.IUpdatable> 介面的下列成員，才能使用反映提供者將更新傳播至資料來源。  
  
|成員|描述|  
|------------|-----------------|  
|<xref:System.Data.Services.IUpdatable.AddReferenceToCollection%2A>|提供將物件加入至相關物件集合的功能，該物件集合可透過導覽屬性來存取。|  
|<xref:System.Data.Services.IUpdatable.ClearChanges%2A>|提供取消暫止資料變更的功能。|  
|<xref:System.Data.Services.IUpdatable.CreateResource%2A>|提供在指定容器中建立新資源的功能。|  
|<xref:System.Data.Services.IUpdatable.DeleteResource%2A>|提供刪除資源的功能。|  
|<xref:System.Data.Services.IUpdatable.GetResource%2A>|提供擷取按特定查詢和型別名稱識別之資源的功能。|  
|<xref:System.Data.Services.IUpdatable.GetValue%2A>|提供傳回資源屬性值的功能。|  
|<xref:System.Data.Services.IUpdatable.RemoveReferenceFromCollection%2A>|提供將物件移至相關物件集合的功能，該物件集合可透過導覽屬性進行存取。|  
|<xref:System.Data.Services.IUpdatable.ResetResource%2A>|提供更新指定之資源的功能。|  
|<xref:System.Data.Services.IUpdatable.ResolveResource%2A>|提供傳回資源的功能，該資源是由特定物件執行個體所代表。|  
|<xref:System.Data.Services.IUpdatable.SaveChanges%2A>|提供儲存所有暫止變更的功能。|  
|<xref:System.Data.Services.IUpdatable.SetReference%2A>|提供使用導覽屬性來設定相關物件參考的功能。|  
|<xref:System.Data.Services.IUpdatable.SetValue%2A>|提供設定資源屬性值的功能。|  
  
## <a name="handling-concurrency"></a>處理並行  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 支援開放式並行存取模型，其方式是讓您定義實體的並行語彙基元。 這個並行語彙基元包含實體的一個或多個屬性，資料服務會使用它來判斷正在要求、更新或刪除的資料中是否已經發生變更。 當取自要求中 eTag 的語彙基元值與目前實體的值不同時，資料服務就會引發例外狀況。 <xref:System.Data.Services.ETagAttribute> 會套用至實體類型，以便在反映提供者中定義並行語彙基元。 並行語彙基元不得包含索引鍵屬性或導覽屬性。 如需詳細資訊，請參閱[更新資料服務](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)。  
  
## <a name="using-linq-to-sql-with-the-reflection-provider"></a>使用 LINQ to SQL 搭配反映提供者  
 由於 Entity Framework 原本就依預設受到支援，因此在使用關聯式資料與 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 時建議使用資料提供者。 不過，您可以使用反映提供者來搭配使用 LINQ to SQL 類別與資料服務。 <xref:System.Data.Linq.Table%601>結果集傳回的方法上<xref:System.Data.Linq.DataContext>LINQ to SQL 物件關聯式設計工具 （O/R 設計工具） 實作所產生<xref:System.Linq.IQueryable%601>介面。 這樣可讓反映提供者存取這些方法，並使用所產生的 LINQ to SQL 類別從 SQL Server 傳回實體資料。 不過，由於 LINQ to SQL 不會實作 <xref:System.Data.Services.IUpdatable> 介面，因此您需要加入部分類別以延伸現有的 <xref:System.Data.Linq.DataContext> 部分類別，來加入 <xref:System.Data.Services.IUpdatable> 實作。 如需詳細資訊，請參閱[How to： 建立使用資料服務的 LINQ to SQL 資料來源](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料服務提供者](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
