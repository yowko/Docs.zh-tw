---
title: "HOW TO：對應繼承階層架構 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# HOW TO：對應繼承階層架構
若要在 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 中實作繼承對應，您必須如下列步驟所述，在繼承階層架構 \(Inheritance Hierarchy\) 的根類別上指定屬性 \(Attribute\) 與其屬性 \(Property\)。  使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 的開發人員可以使用 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 來對應繼承階層架構。  請參閱[HOW TO：使用 O\/R 設計工具設定繼承](../Topic/How%20to:%20Configure%20inheritance%20by%20using%20the%20O-R%20Designer.md)。  
  
> [!NOTE]
>  子類別上不需要任何特別的屬性 \(Attribute\) 或屬性 \(Property\)。  請特別注意，子類別沒有 <xref:System.Data.Linq.Mapping.TableAttribute> 屬性 \(Attribute\)。  
  
### 若要對應繼承階層架構  
  
1.  將 <xref:System.Data.Linq.Mapping.TableAttribute> 屬性 \(Attribute\) 加入至根類別。  
  
2.  同樣在根類別中，加入階層結構中每個類別的 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 屬性 \(Attribute\)。  
  
3.  針對每個 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 屬性 \(Attribute\)，定義 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> 屬性 \(Property\)。  
  
     這個屬性 \(Property\) 保留的值會顯示在資料庫資料表的 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> 資料行中，以表示此資料列屬於哪個類別或子類別。  
  
4.  針對每個 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 屬性 \(Attribute\)，同時加入 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> 屬性 \(Property\)。  
  
     這個屬性 \(Property\) 保留的值會指定索引鍵值所表示的類別或子類別。  
  
5.  僅在其中一個 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 屬性 \(Attribute\) 中，加入 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> 屬性 \(Property\)。  
  
     當資料庫資料表中的鑑別子值不符合繼承對應中的任何 *後援* 值時，這個屬性 \(Property\) 即可用於指定「<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>」\(Fallback\) 對應。  
  
6.  加入 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> 屬性 \(Attribute\) 的 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 \(Property\)。  
  
     這個屬性 \(Property\) 表示此為保留 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> 值的資料行。  
  
## 範例  
  
> [!NOTE]
>  如果您使用的是 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]，就可以使用 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 來設定繼承。  請參閱[HOW TO：使用 O\/R 設計工具設定繼承](../Topic/How%20to:%20Configure%20inheritance%20by%20using%20the%20O-R%20Designer.md)  
  
 在下列程式碼範例中，`Vehicle` 會定義為根類別，而且會實作先前的步驟以描述 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 的階層架構。  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## 請參閱  
 [繼承支援](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)   
 [HOW TO：使用程式碼編輯器自訂實體類別](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)