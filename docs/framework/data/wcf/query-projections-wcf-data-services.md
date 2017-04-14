---
title: "查詢投影 (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "投影 [WCF Data Services]"
  - "查詢投影 [WCF Data Services]"
  - "WCF Data Services, 投影"
  - "WCF Data Services, 查詢"
ms.assetid: a09f4985-9f0d-48c8-b183-83d67a3dfe5f
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 查詢投影 (WCF Data Services)
投影會在 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 中提供一種機制，可藉由指定回應中僅傳回特定實體屬性的方式，減少查詢傳回之摘要中的資料量。  如需詳細資訊，請參閱 [OData：Select 系統查詢選項 \($select\)](http://go.microsoft.com/fwlink/?LinkId=186076)。  
  
 本主題描述如何定義查詢投影、實體與非實體類型的需求為何、對投影結果進行更新、建立投影類型，以及列出一些投影考量因素。  
  
## 定義查詢投影  
 您可以將投影子句加入查詢中，方式為在 URI 中使用 `$select` 查詢選項或在 LINQ 查詢中使用 [select](../Topic/select%20clause%20\(C%23%20Reference\).md) 子句 \(在 Visual Basic 中為 [Select](../Topic/Select%20Clause%20\(Visual%20Basic\).md)\)。  傳回的實體資料可以投影至用戶端上的實體類型或非實體類型。  此主題中的範例將示範如何在 LINQ 查詢中使用 `select` 子句。  
  
> [!IMPORTANT]
>  當您儲存對投影類型所進行的更新時，資料服務中可能會遺失資料。  如需詳細資訊，請參閱[投影考量因素](#considerations)。  
  
## 實體與非實體類型的需求  
 實體類型必須具備一個或多個構成實體索引鍵的識別屬性。  實體類型在用戶端上是利用下列其中一種方式來定義：  
  
-   將 <xref:System.Data.Services.Common.DataServiceKeyAttribute> 或 <xref:System.Data.Services.Common.DataServiceEntityAttribute> 套用至類型。  
  
-   當類型具有名為 `ID` 的屬性時。  
  
-   當類型具有名為 *type*`ID` 的屬性時，其中 *type* 是類型的名稱。  
  
 根據預設，當您將查詢結果投影至用戶端上定義的類型時，投影中要求的屬性必須是用戶端上現有的類型。  但是，當您為 <xref:System.Data.Services.Client.DataServiceContext> 的 <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> 屬性指定 `true` 值時，投影中指定的屬性就不一定要用戶端上現有的類型。  
  
### 對投影結果進行更新  
 若已呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法，當您將查詢結果投影至用戶端上的實體類型時，<xref:System.Data.Services.Client.DataServiceContext> 可以使用要傳送回資料服務的更新來追蹤該些物件。  但是，對投影至用戶端上之非實體類型的資料所進行之更新，無法傳送回資料服務。  這是因為沒有索引鍵可識別實體執行個體，資料服務無法更新資料來源中的正確實體。  非實體類型並未附加至 <xref:System.Data.Services.Client.DataServiceContext>。  
  
 當資料服務中所定義之實體類型的一個或多個屬性並不存在實體所投影至的用戶端類型中時，插入新的實體並不會包含這些遺漏的屬性。  在這種情況下，對現有實體進行的更新**也**不會包括這些遺漏的屬性。  若此類屬性中已存有值，更新會依資料來源中所定義，將它重設為屬性的預設值。  
  
### 建立投影類型  
 下列範例使用匿名 LINQ 查詢，將 `Customers` 類型的地址相關屬性投影至新的 `CustomerAddress` 類型，後者類型已在用戶端上定義並屬性化為實體類型：  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#selectcustomeraddressspecific)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#selectcustomeraddressspecific)]  
  
 在此範例中，物件初始設定式模式會用來建立 `CustmerAddress` 類型的新執行個體，而非用來呼叫建構函式。  在投影至實體類型時不支援建構函式，但是投影至非實體與匿名型別時可以使用建構函式。  因為 `CustomerAddress` 是實體類型，所以可以進行變更並將變更傳送回資料服務。  
  
 而且，取自 `Customer` 類型的資料是投影至 `CustomerAddress` 實體類型的執行個體，而非投影至匿名型別。  可支援投影至匿名型別，但是因為匿名型別被視為非實體類型，所以資料是唯讀的。  
  
 <xref:System.Data.Services.Client.DataServiceContext> 的 <xref:System.Data.Services.Client.MergeOption> 設定可在查詢投影期間供識別解析使用。  這表示如果 <xref:System.Data.Services.Client.DataServiceContext> 中已有 `Customer` 類型的執行個體，使用相同識別之 `CustomerAddress` 的執行個體將會依照 <xref:System.Data.Services.Client.MergeOption> 所設定的識別解析規則  
  
 下表描述將結果投影至實體與非實體類型時的行為：  
  
|動作|實體類型|非實體類型|  
|--------|----------|-----------|  
|使用初始設定式建立新的投影執行個體，如下列範例所示：<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithinitializer)]
 [!code-vb[Astoria Northwind Client#ProjectWithInitializer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithinitializer)]|支援|支援|  
|使用建構函式建立新的投影執行個體，如下列範例所示：<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithconstructor)]
 [!code-vb[Astoria Northwind Client#ProjectWithConstructor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithconstructor)]|引發 <xref:System.NotSupportedException>。|支援|  
|使用投影來轉換屬性值，如下列範例所示：<br /><br /> [!code-csharp[Astoria Northwind Client#ProjectWithTransform](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#projectwithtransform)]
 [!code-vb[Astoria Northwind Client#ProjectWithTransform](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#projectwithtransform)]<br /><br /> 實體類型不支援此種轉換，因為它可能造成混淆且可能覆寫屬於另一個實體之資料來源中的資料。|引發 <xref:System.NotSupportedException>。|支援|  
  
<a name="considerations"></a>   
## 投影考量因素  
 下列其他考量因素適用於定義查詢投影時。  
  
-   在定義 Atom 格式的自訂摘要時，您必須確保所有已定義自訂對應的實體屬性都包含在投影中。  若投影中未包含對應的實體屬性，則可能會發生資料遺失。  如需詳細資訊，請參閱[摘要自訂](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)。  
  
-   對未包含資料服務之資料模型中的所有實體屬性之投影類型進行插入時，用戶端上未包含在投影內的屬性會設定為它們的預設值。  
  
-   對未包含資料服務之資料模型中的所有實體屬性之投影類型進行更新時，用戶端上未包含在投影內的現有值將被覆寫成未初始化的預設值。  
  
-   當投影包括一種複雜屬性時，必須傳回整個複雜物件。  
  
-   當投影包含導覽屬性時，相關物件會以隱含方式載入，不必呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 方法。  不支援將 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 方法用於投影查詢中。  
  
-   查詢用戶端上的投影查詢會轉譯為在要求 URI 中使用 `$select` 查詢選項。  針對不支援 `$select` 查詢選項的舊版 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 執行具有投影的查詢時，系統會傳回錯誤。當資料服務之 <xref:System.Data.Services.DataServiceBehavior> 的 <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> 設為 <xref:System.Data.Services.Common.DataServiceProtocolVersion> 的值時，也可能會發生這個情況。  如需詳細資訊，請參閱[資料服務版本控制](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)。  
  
 如需詳細資訊，請參閱[HOW TO：專案查詢結果](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)。  
  
## 請參閱  
 [查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)