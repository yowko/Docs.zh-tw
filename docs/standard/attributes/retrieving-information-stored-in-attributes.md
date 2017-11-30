---
title: "擷取儲存於屬性中的資訊"
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
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9d3fd9a5a49d65b37d2cdb5107e9c516a6df5847
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-information-stored-in-attributes"></a>擷取儲存於屬性中的資訊
擷取自訂屬性是簡單的程序。 首先，宣告您想要擷取之屬性的執行個體。 然後，使用<xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>方法來初始化新的屬性，為您想要擷取之屬性的值。 一旦完成初始化新的屬性，您只要使用其屬性以取得的值。  
  
> [!IMPORTANT]
>  本主題描述如何擷取屬性的執行內容所載入的程式碼。 若要擷取的程式碼載入至僅限反映的內容屬性，您必須使用<xref:System.Reflection.CustomAttributeData>類別，如中所示[如何： 載入組件放入 Reflection-Only 內容](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)。  
  
 本章節描述下列方式來擷取屬性：  
  
-   [擷取屬性的單一執行個體](#cpconretrievingsingleinstanceofattribute)  
  
-   [擷取多個執行個體的屬性套用至相同的範圍](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [擷取多個執行個體的屬性套用至不同的範圍](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a>擷取屬性的單一執行個體  
 在下列範例中， `DeveloperAttribute` （如上一節中所述） 套用至`MainApp`類別層級上的類別。 `GetAttribute`方法會使用**GetCustomAttribute**擷取中所儲存值`DeveloperAttribute`類別層級之後，它們顯示在主控台上。  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 此程式會顯示下列文字時執行。  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 如果找不到屬性， **GetCustomAttribute**方法初始化`MyAttribute`為 null 值。 這個範例會檢查`MyAttribute`這類執行個體，並通知使用者，如果不找到任何屬性。 如果`DeveloperAttribute`找不到在類別範圍中，下列訊息顯示到主控台。  
  
```  
The attribute was not found.   
```  
  
 這個範例會假設屬性定義為目前的命名空間中。 請記住，如果不是目前的命名空間中，將屬性定義的所在的命名空間匯入。  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>擷取多個執行個體的屬性套用至相同的範圍  
 在上述範例中，若要檢查的類別與要尋找特定的屬性會傳遞至<xref:System.Attribute.GetCustomAttribute%2A>。 該程式碼可以運作良好如果只有一個執行個體的屬性會套用至類別層級。 不過，如果多個執行個體的屬性會在相同的類別層級，套用**GetCustomAttribute**方法不會擷取所有的資訊。 在多個執行個體相同的屬性會套用至相同範圍的情況，您可以使用<xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>將放入陣列屬性的所有執行個體。 比方說，如果兩個執行個體`DeveloperAttribute`相同類別的類別層級上套用`GetAttribute`方法可以修改以顯示這兩個屬性中找到的資訊。 請記住，在相同的層級上套用多個屬性的屬性都必須定義**AllowMultiple**屬性設定為**true**中<xref:System.AttributeUsageAttribute>。  
  
 下列程式碼範例示範如何使用**GetCustomAttributes**方法來建立陣列所參考的所有執行個體`DeveloperAttribute`在任何指定的類別。 所有屬性的值隨即顯示到主控台。  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 如果找不到任何屬性，此程式碼會提醒使用者。 否則，所包含的資訊中的兩個執行個體`DeveloperAttribute`隨即出現。  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>擷取多個執行個體的屬性套用至不同的範圍  
 <xref:System.Attribute.GetCustomAttributes%2A>和<xref:System.Attribute.GetCustomAttribute%2A>方法不搜尋整個類別，並傳回該類別中的所有執行個體的屬性。 相反地，它們會一次搜尋只能有一個指定的方法或成員。 如果您擁有的類別具有相同的屬性套用至每個成員，而且您想要擷取套用至這些成員的所有屬性的值，您必須提供每個方法或成員為個別**GetCustomAttributes**和**GetCustomAttribute**。  
  
 下列程式碼範例會採用做為參數的類別，並搜尋`DeveloperAttribute`（已定義的先前） 和每個個別的方法，該類別的類別層級上。  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 如果沒有執行個體的`DeveloperAttribute`方法層級或類別層級上找到`GetAttribute`方法通知使用者，找不到任何屬性，並顯示方法或類別不包含屬性的名稱。 如果找到屬性， `Name`， `Level`，和`Reviewed`欄位會顯示到主控台。  
  
 您可以使用的成員<xref:System.Type>傳遞的類別中取得的個別方法和成員的類別。 下列範例會先查詢**類型**取得類別層級的屬性資訊的物件。 接著，它會使用<xref:System.Type.GetMethods%2A?displayProperty=nameWithType>放置成陣列的所有方法的執行個體<xref:System.Reflection.MemberInfo?displayProperty=nameWithType>擷取的方法層級的屬性資訊的物件。 您也可以使用<xref:System.Type.GetProperties%2A?displayProperty=nameWithType>方法來檢查屬性層級上的屬性或<xref:System.Type.GetConstructors%2A?displayProperty=nameWithType>檢查建構函式層級上的屬性。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [屬性](../../../docs/standard/attributes/index.md)
