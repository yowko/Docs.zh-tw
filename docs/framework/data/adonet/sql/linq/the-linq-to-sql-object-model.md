---
title: "LINQ to SQL 物件模型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# LINQ to SQL 物件模型
在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，以開發人員之程式語言表示的物件模型 \(Object Model\) 會對應至關聯式資料庫的資料模型。  然後就會根據物件模型對資料執行作業。  
  
 在這種情況下，您不會發出資料庫命令 \(例如，`INSERT`\) 至資料庫。  而是在您的物件模型中變更值和執行方法。  當您要查詢資料庫或將變更傳送至資料庫時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將您的要求轉譯為正確的 SQL 命令，並將這些命令傳送至資料庫。  
  
 ![DLinqObjectModel](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinqobjectmodel.png "DLinqObjectModel")  
  
 下表摘要說明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件模型中最基本的項目，以及其與關聯式資料模型中項目的關聯性：  
  
|LINQ to SQL 物件模型|關聯式資料模型|  
|----------------------|-------------|  
|實體類別|資料表|  
|類別成員|Column|  
|關聯|外部索引鍵關聯性|  
|方法|預存程序或函式|  
  
> [!NOTE]
>  下列說明假設您對於關聯式資料模型和規則有基本知識。  
  
## LINQ to SQL 實體類別和資料庫資料表  
 在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，資料庫資料表是由「*實體類別*」\(Entity Class\) 所表示。  實體類別就像您可能建立的任何其他類別，但您會使用能讓類別與資料庫資料表產生關聯的特殊資訊來標註此類別。  您可將自訂屬性 \(<xref:System.Data.Linq.Mapping.TableAttribute>\) 加入至您的類別宣告，藉以產生此附註，如下列範例所示：  
  
### 範例  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 只有宣告為資料表的類別執行個體 \(也就是實體類別\) 可以儲存至資料庫。  
  
 如需詳細資訊，請參閱[以屬性為基礎的對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) 的＜資料表屬性＞一節。  
  
## LINQ to SQL 類別成員和資料庫資料行  
 除了使類別和資料表產生關聯以外，您還會指定欄位或屬性，以表示資料庫資料行。  基於這個目的，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會定義 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性，如下列範例所示：  
  
### 範例  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 只有對應到資料行的欄位和屬性會保存至資料庫或自資料庫擷取。  至於未宣告為資料行者，則會被視為應用程式邏輯的暫時性部分。  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 \(Attribute\) 具有各種屬性 \(Property\)，您可以用於自訂表示資料行的這些成員 \(例如，指定成員以表示主索引鍵資料行\)。  如需詳細資訊，請參閱[以屬性為基礎的對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) 的＜資料行屬性＞一節。  
  
## LINQ to SQL 關聯和資料庫外部索引鍵關聯性  
 在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，您可藉由套用 <xref:System.Data.Linq.Mapping.AssociationAttribute> 屬性來表示資料庫關聯 \(例如，外部索引鍵和主索引鍵的關聯性\)。  在下列程式碼區段中，`Order` 類別包含具有 `Customer` 屬性 \(Attribute\) 的 <xref:System.Data.Linq.Mapping.AssociationAttribute> 屬性 \(Property\)。  這個屬性 \(Property\) 與其屬性 \(Attribute\) 提供了與 `Order` 類別有關的 `Customer` 類別。  
  
 下列程式碼範例顯示 `Customer` 類別中的 `Order` 屬性 \(Property\)。  
  
### 範例  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 如需詳細資訊，請參閱[以屬性為基礎的對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) 的＜關聯屬性＞一節。  
  
## LINQ to SQL 方法和資料庫預存程序  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 支援預存程序和使用者定義函式。  在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，您可將這些資料庫定義的抽象對應至用戶端物件，便可以強型別的方式從用戶端程式碼存取這些抽象。  方法簽章與資料庫中定義的程序和函式簽章十分相似。  您可以使用 IntelliSense 來探索這些方法。  
  
 呼叫對應程序所傳回的結果集是強型別集合。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會使用 <xref:System.Data.Linq.Mapping.FunctionAttribute> 和 <xref:System.Data.Linq.Mapping.ParameterAttribute> 屬性，將預存程序和函式對應至方法。  <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> 屬性可以區分表示預存程序的方法和表示使用者定義函式的方法。  如果此屬性設為 `false` \(預設值\)，則此方法表示預存程序。  如果設為 `true`，則此方法表示資料庫函式。  
  
> [!NOTE]
>  如果您使用的是 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]，就可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]來建立對應至預存程序和使用者定義函式的方法。  
  
### 範例  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 如需詳細資訊，請參閱[以屬性為基礎的對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) 和[預存程序](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md) 的＜函式屬性＞、＜預存程序屬性＞和＜參數屬性＞小節。  
  
## 請參閱  
 [以屬性為基礎的對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)   
 [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)