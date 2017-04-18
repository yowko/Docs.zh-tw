---
title: "使用 DataView 進行篩選 (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 使用 DataView 進行篩選 (LINQ to DataSet)
使用特定準則來篩選資料，然後透過 UI 控制項呈現資料給用戶端的功能是資料繫結的重要層面。  <xref:System.Data.DataView> 提供了許多方式來篩選資料並傳回符合特定篩選準則的資料列子集。  除了以字串為基礎的篩選功能以外，<xref:System.Data.DataView> 也提供針對篩選準則使用 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 運算式的功能。[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 運算式比以字串為基礎的篩選允許更複雜且功能更強大的篩選作業。  
  
 目前有兩種方式可以使用 <xref:System.Data.DataView> 來篩選資料：  
  
-   從含有 Where 子句的 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢中建立 <xref:System.Data.DataView>。  
  
-   使用 <xref:System.Data.DataView> 現有的以字串為基礎的篩選功能。  
  
## 從含有篩選資訊的查詢中建立 DataView  
 您可以從 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢中建立 <xref:System.Data.DataView> 物件。  如果該查詢包含 `Where` 子句，<xref:System.Data.DataView> 就是使用查詢的篩選資訊建立的。  `Where` 子句中的運算式可用來決定哪些資料列將包含在 <xref:System.Data.DataView> 中，而且它是篩選的基礎。  
  
 以運算式為基礎的篩選會比較簡單的以字串為基礎的篩選提供功能更強大且更複雜的篩選。  以字串為基礎的篩選和以運算式為基礎的篩選會互斥。  如果您從查詢中建立 <xref:System.Data.DataView> 之後才設定以字串為基礎的 <xref:System.Data.DataView.RowFilter%2A>，就會清除從查詢中推斷的以運算式為基礎的篩選。  
  
> [!NOTE]
>  在大部分清況中，用於篩選的運算式不應該具有副作用 \(Side Effect\) 而且必須具決定性。  此外，這些運算式不應該包含取決於固定執行次數的任何邏輯，因為篩選作業可能會執行任何次數。  
  
### 範例  
 下列範例會在 SalesOrderDetail 資料表中查詢是否有數量大於 2 而小於 6 的訂單、從該查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView> 繫結至 <xref:System.Windows.Forms.BindingSource>：  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### 範例  
 下列範例會從 2001 年 6 月 6 日之後下單的訂單查詢中建立 <xref:System.Data.DataView>：  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### 範例  
 篩選也可以與排序結合。  下列範例會從姓氏以 "S" 為開頭並先依據姓氏，然後再依據名字排序的連絡人查詢中建立 <xref:System.Data.DataView>。  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhereorderbythenby)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhereorderbythenby)]  
  
### 範例  
 下列範例會使用 SoundEx 演算法來尋找姓氏類似於 "Zhu" 的連絡人。  SoundEx 演算法是在 SoundEx 方法中實作的。  
  
 [!code-csharp[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvsoundexfilter)]
 [!code-vb[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvsoundexfilter)]  
  
 SoundEx 是用於依據聲音索引名稱的語音演算法，而這些名稱都是以英文發音 \(原本由美國  人口普查局 \(U.S. Census Bureau\) 所開發\)。  SoundEx 方法會針對名稱傳回四個字元碼，其中包含一個英文字母，後面接著三個數字。  該字母是名稱的第一個字母，而這些數字則編碼名稱中的其餘子音字母。  類似發音的名稱會共用相同的 SoundEx 代碼。  在先前範例之 SoundEx 方法中使用的 SoundEx 實作如下所示：  
  
 [!code-csharp[DP DataView Samples#SoundEx](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#soundex)]
 [!code-vb[DP DataView Samples#SoundEx](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#soundex)]  
  
## 使用 RowFilter 屬性  
 <xref:System.Data.DataView> 現有的以字串為基礎的篩選功能仍然可在 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 內容中運作。  如需以字串為基礎之 <xref:System.Data.DataView.RowFilter%2A> 篩選的詳細資訊，請參閱[排序和篩選資料](../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)。  
  
 下列範例會從 Contact 資料表中建立 <xref:System.Data.DataView>，然後設定 <xref:System.Data.DataView.RowFilter%2A> 屬性，以便傳回連絡人姓氏為 "Zhu" 的資料列：  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 在您已經從 <xref:System.Data.DataTable> 或 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢中建立 <xref:System.Data.DataView> 之後，就可以使用 <xref:System.Data.DataView.RowFilter%2A> 屬性，根據資料列的資料行值來指定資料列的子集。  以字串為基礎的篩選和以運算式為基礎的篩選會互斥。  因此，設定 <xref:System.Data.DataView.RowFilter%2A> 屬性將會清除從 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢中推斷的篩選運算式，而且無法重設篩選運算式。  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 如果您想要傳回特定資料查詢的結果，但不要提供資料子集的動態檢視，就可以使用 <xref:System.Data.DataView> 的 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 方法，而非設定 <xref:System.Data.DataView.RowFilter%2A> 屬性。  <xref:System.Data.DataView.RowFilter%2A> 屬性最適於資料繫結應用程式，因為這種應用程式會用繫結控制項顯示篩選結果。  設定 <xref:System.Data.DataView.RowFilter%2A> 屬性會重建資料索引，因而增加應用程式的負荷並降低效能。  <xref:System.Data.DataView.Find%2A> 和 <xref:System.Data.DataView.FindRows%2A> 方法會使用目前的索引，而不需要重建索引。  如果您只要呼叫 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 一次，就應該使用現有的 <xref:System.Data.DataView>。  如果您要呼叫 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 多次，就應該建立新的 <xref:System.Data.DataView> 來重建您想要搜尋之資料行的索引，然後呼叫 <xref:System.Data.DataView.Find%2A> 或 <xref:System.Data.DataView.FindRows%2A> 方法。  如需 <xref:System.Data.DataView.Find%2A> 和 <xref:System.Data.DataView.FindRows%2A> 方法的詳細資訊，請參閱[尋找資料列](../../../../docs/framework/data/adonet/dataset-datatable-dataview/finding-rows.md)和 [DataView 效能](../../../../docs/framework/data/adonet/dataview-performance.md)。  
  
## 清除篩選  
 在您已經使用 <xref:System.Data.DataView.RowFilter%2A> 屬性來設定篩選之後，就可以清除 <xref:System.Data.DataView> 上的篩選。  您可以使用兩種不同的方式來清除 <xref:System.Data.DataView> 上的篩選：  
  
-   將 <xref:System.Data.DataView.RowFilter%2A> 屬性設定為 `null`。  
  
-   將 <xref:System.Data.DataView.RowFilter%2A> 屬性設定為空字串。  
  
### 範例  
 下列範例會從查詢中建立 <xref:System.Data.DataView>，然後將 <xref:System.Data.DataView.RowFilter%2A> 屬性設定為 `null`，藉以清除篩選：  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### 範例  
 下列範例會從資料表中建立 <xref:System.Data.DataView>、設定 <xref:System.Data.DataView.RowFilter%2A> 屬性，然後將 <xref:System.Data.DataView.RowFilter%2A> 屬性設定為空字串，藉以清除篩選：  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## 請參閱  
 [資料繫結和 LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)   
 [使用 DataView 進行排序](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)