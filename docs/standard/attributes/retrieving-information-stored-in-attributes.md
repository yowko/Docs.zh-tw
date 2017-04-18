---
title: "擷取儲存於屬性中的資訊 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "屬性 [.NET Framework], 擷取"
  - "多個屬性執行個體"
  - "擷取屬性"
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 擷取儲存於屬性中的資訊
擷取自訂屬性是一簡單的程序。  首先，宣告您想要擷取的屬性的執行個體。  接著，使用 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> 方法來初始化新屬性成您想要擷取的屬性值。  一旦屬性初始化後，您只要使用它的屬性來取得值。  
  
> [!IMPORTANT]
>  本主題將說明如何替載入至執行內容的程式碼擷取屬性。  若要替載入至僅限反映之內容的程式碼擷取屬性，您必須使用 <xref:System.Reflection.CustomAttributeData> 類別，如 [如何：將組件載入僅限反映的內容](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)所示。  
  
 這個章節描述下列擷取屬性的方式：  
  
-   [擷取屬性的單一執行個體](#cpconretrievingsingleinstanceofattribute)  
  
-   [擷取套用至相同範圍的屬性的多個執行個體](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [擷取套用至不同範圍的屬性的多個執行個體](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## 擷取屬性的單一執行個體  
 下列範例中，`DeveloperAttribute` \(前面章節描述的\) 套用至在類別層級上的 `MainApp` 類別。  `GetAttribute` 方法使用 **GetCustomAttribute**，在顯示到主控台 \(Console\) 之前擷取儲存於類別層級上 `DeveloperAttribute` 的值。  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 這個程式在執行時顯示下列文字。  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 如果找不到屬性，**GetCustomAttribute** 方法初始化 `MyAttribute` 為 null 值。  這範例對此類執行個體檢查 `MyAttribute`，並且如果找不到屬性將告知使用者。  如果類別範圍中找不到 `DeveloperAttribute`，則將下列訊息顯示到主控台。  
  
```  
The attribute was not found.   
```  
  
 這範例假設屬性定義在目前命名空間中。  如果它不是在目前的命名空間中，請記得將屬性定義所在的命名空間匯入。  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## 擷取套用至相同範圍的屬性的多個執行個體  
 前面範例中，要檢查的類別和要尋找的特定屬性被傳遞到 <xref:System.Attribute.GetCustomAttribute%2A>。  如果類別層級上只套用一個屬性執行個體，那個程式碼將正常運作。  然而，如果在相同類別層級套用屬性的多個執行個體，**GetCustomAttribute** 方法不會擷取所有資訊。  假使相同屬性的多個執行個體套用到相同範圍，您可以使用 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=fullName> 將屬性的所有執行個體放到陣列裡。  例如，如果 `DeveloperAttribute` 的兩個執行個體套用至相同類別的類別層級上，可以修改 `GetAttribute` 方法以顯示兩個屬性中都有的資訊。  請記得，若要在相同層級套用多重屬性 \(Attribute\)，必須在 <xref:System.AttributeUsageAttribute> 中將 **AllowMultiple** 屬性 \(Property\) 設定為 **true** 以定義屬性 \(Attribute\)。  
  
 下列程式碼範例說明如何使用 **GetCustomAttributes** 方法來建立陣列，參考任何指定類別中 `DeveloperAttribute` 的所有執行個體。  接著顯示所有屬性值到主控台。  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 如果找不到屬性，這個程式碼會警示使用者。  否則，顯示 `DeveloperAttribute` 的兩個執行個體包含的全部資訊。  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## 擷取套用至不同範圍的屬性的多個執行個體  
 <xref:System.Attribute.GetCustomAttributes%2A> 和 <xref:System.Attribute.GetCustomAttribute%2A> 方法不會搜尋整個類別和傳回類別中屬性的所有執行個體。  也就是，它們一次只搜尋一個方法或成員。  如果您將帶著相同屬性的類別套用到每個成員，而且您想要擷取套用到那些成員的所有屬性中的值，您必須將每個方法或成員個別提供給 **GetCustomAttributes** 和 **GetCustomAttribute**。  
  
 下列程式碼範例將類別當做參數，並且在類別層級和該類別的每一個個別方法上搜尋 `DeveloperAttribute` \(前面定義的\)。  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 如果在方法層級或類別層級上找不到 `DeveloperAttribute` 的執行個體，`GetAttribute` 方法會告知使用者找不到屬性，並顯示不包含屬性的方法或類別。  如果找到屬性，則將 `Name`、`Level` 和 `Reviewed` 欄位顯示到主控台。  
  
 您可以使用 <xref:System.Type> 類別的成員，以取得傳遞的類別中的個別方法和成員。  這範例首先查詢 **Type** 物件以取得類別層級的屬性資訊。  其次，它使用 <xref:System.Type.GetMethods%2A?displayProperty=fullName> 將所有方法的執行個體放到 <xref:System.Reflection.MemberInfo?displayProperty=fullName> 物件的陣列中，來擷取方法層級的屬性資訊。  您也可以使用 <xref:System.Type.GetProperties%2A?displayProperty=fullName> 方法在屬性 \(Property\) 層級上檢查屬性 \(Attribute\)，或 <xref:System.Type.GetConstructors%2A?displayProperty=fullName> 在建構函式層級上檢查屬性 \(Attribute\)。  
  
## 請參閱  
 <xref:System.Type?displayProperty=fullName>   
 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName>   
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=fullName>   
 [屬性](../../../docs/standard/attributes/index.md)