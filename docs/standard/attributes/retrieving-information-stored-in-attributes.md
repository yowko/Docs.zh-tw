---
title: 擷取儲存於屬性中的資訊
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6939c215633be10e487f9cd5bd25856c0c611921
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623661"
---
# <a name="retrieving-information-stored-in-attributes"></a>擷取儲存於屬性中的資訊
擷取自訂屬性是一個簡單的程序。 首先，對想要擷取的屬性宣告執行個體。 然後，使用 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> 方法將新屬性初始化為所要擷取之屬性的值。 在將新屬性 (Attribute) 初始化之後，只要使用其屬性 (Poperty) 即可取得值。  
  
> [!IMPORTANT]
>  本文說明如何針對載入到執行內容的程式碼擷取屬性。 若要對載入僅限反射內容中的程式碼擷取屬性，您必須使用 <xref:System.Reflection.CustomAttributeData> 類別，如以下連結所示：[如何：將組件載入僅限反映的內容](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)。  
  
 本節說明下列擷取屬性的方式：  
  
- [擷取單一屬性執行個體](#cpconretrievingsingleinstanceofattribute)  
  
- [擷取套用至相同範圍的多個屬性執行個體](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
- [擷取套用至不同範圍的多個屬性執行個體](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a>擷取單一屬性執行個體  
 在下列範例中，`DeveloperAttribute` (上節所述) 會在類別層級上套用至 `MainApp` 類別。 `GetAttribute` 方法會先使用 **GetCustomAttribute** 來擷取類別層級上的 `DeveloperAttribute` 中所儲存的值，再顯示於主控台。  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 此程式會在執行後顯示下列文字。  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 如果找不到屬性，**GetCustomAttribute**方法會將 `MyAttribute` 初始化為 Null 值。 此範例會檢查 `MyAttribute` 是否有此類執行個體，並在找不到屬性時通知使用者。 如果在類別範圍中找不到 `DeveloperAttribute`，會在主控台顯示下列訊息。  
  
```  
The attribute was not found.   
```  
  
 此範例會假設屬性定義在目前的命名空間中。 如果屬性定義不在目前的命名空間中，請記得匯入屬性定義所在的命名空間。  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a>擷取套用至相同範圍的多個屬性執行個體  
 在上述範例中，要檢查的類別和要尋找的特定屬性都會傳遞至 <xref:System.Attribute.GetCustomAttribute%2A>。 如果類別層級上只套用一個屬性執行個體，該程式碼可以運作良好。 不過，如果在相同的類別層級上套用多個屬性執行個體，**GetCustomAttribute** 方法不會擷取所有資訊。 在相同屬性的多個執行個體都套用至相同範圍的情況下，您可以使用 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> 將屬性的所有執行個體放入陣列。 例如，如果在相同類別的類別層級上套用 `DeveloperAttribute` 的兩個執行個體，可修改 `GetAttribute` 方法以顯示在兩個屬性中找到的資訊。 請記住，若要在相同層級上套用多個屬性，屬性必須使用 <xref:System.AttributeUsageAttribute> 中設定為 **true** 的 **AllowMultiple** 屬性來定義。  
  
 下列程式碼範例會示範如何使用 **GetCustomAttributes** 方法，來建立會參考任何指定類別中所有 `DeveloperAttribute` 執行個體的陣列。 所有屬性的值隨即顯示在主控台。  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 如果找不到任何屬性，此程式碼會警示使用者。 否則，`DeveloperAttribute` 的兩個執行個體中所包含的資訊隨即顯示。  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a>擷取套用至不同範圍的多個屬性執行個體  
 <xref:System.Attribute.GetCustomAttributes%2A> 和 <xref:System.Attribute.GetCustomAttribute%2A> 方法不會搜尋整個類別，然後傳回該類別中屬性的所有執行個體。 而會一次只搜尋一個指定的方法或成員。 如果您有每個成員都套用相同屬性的類別，並想要擷取所有套用至那些成員的屬性值，就必須將每個方法或成員個別提供給 **GetCustomAttributes** 和 **GetCustomAttribute**。  
  
 下列程式碼範例會將類別視為參數，並在類別層級和該類別的每一個方法搜尋 `DeveloperAttribute` (先前所定義)。  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 如果在方法層級或類別層級上找不到任何 `DeveloperAttribute` 的執行個體，`GetAttribute` 會通知使用者找不到任何屬性，並顯示不包含該屬性的方法或類別名稱。 如果找到屬性，會在主控台顯示 `Name`、`Level` 及 `Reviewed` 欄位。  
  
 您可以使用 <xref:System.Type> 類別的成員來取得所傳遞類別中的個別方法和成員。 此範例會先查詢 **Type** 物件以取得類別層級的屬性資訊。 接著，它會使用 <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> 以將所有方法的執行個體置入 <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> 物件的陣列，以擷取方法層級的屬性資訊。 您也可以使用 <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> 方法來檢查屬性層級上的屬性，或使用 <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> 來檢查建構函式層級上的屬性。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [屬性](../../../docs/standard/attributes/index.md)
