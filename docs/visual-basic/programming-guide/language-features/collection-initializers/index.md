---
title: "Collection Initializers (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.CollectionInitializer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "collection initializers [Visual Basic]"
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Collection Initializers (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

「*集合初始設定式*」\(Collection Initializer\) 提供縮短的語法，供您建立集合並填入一組初始值。  當您從一組已知值 \(例如，功能表選項或分類的清單、數值初始集、日期或月份名稱等字串靜態清單，或地理位置如用於驗證的州\/省清單\) 建立集合時，集合初始設定式會很有用。  
  
 如需集合的詳細資訊，請參閱 [集合](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 使用 `From` 關鍵字，並在後面接著大括號 \(`{}`\)，即可識別集合初始設定式。  這類似於 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)中所述的陣列常值語法。  在下列範例中，會示範以不同方式使用集合初始設定式來建立集合。  
  
 [!code-vb[VbVbalrCollectionInitializers#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/index_1.vb)]  
  
> [!NOTE]
>  C\# 也會提供集合初始設定式。  C\# 集合初始設定式提供的功能與 Visual Basic 集合初始設定式相同。  如需 C\# 集合初始設定式的詳細資訊，請參閱[物件和集合初始設定式](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。  
  
## 語法  
 集合初始設定式是由 `From` 關鍵字後面接著以大括號 \(`{}`\) 括住的逗點分隔值清單組成，如下列程式碼所示。  
  
 [!code-vb[VbVbalrCollectionInitializers#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/index_2.vb)]  
  
 當您建立如 <xref:System.Collections.Generic.List%601> 或 <xref:System.Collections.Generic.Dictionary%602> 等集合時，必須在集合初始設定式之前提供集合型別，如下列程式碼所示。  
  
 [!code-vb[VbVbalrCollectionInitializers#13](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/index_3.vb)]  
  
> [!NOTE]
>  您無法將集合初始設定式與物件初始設定式合併在一起，來初始化相同的物件集合。  您可以使用物件初始設定式，在集合初始設定式中初始化物件。  
  
## 使用集合初始設定式建立集合  
 使用集合初始設定式建立集合時，集合初始設定式中提供的每個值都會傳遞至集合的適當 `Add` 方法。  例如，如果您使用集合初始設定式建立 <xref:System.Collections.Generic.List%601>，則集合初始設定式中的每個字串值都會傳遞至 <xref:System.Collections.Generic.List%601.Add%2A> 方法。  如果您想要使用集合初始設定式建立集合，則指定的型別必須是有效的集合型別。  有效集合型別的範例包括實作 <xref:System.Collections.Generic.IEnumerable%601> 介面或繼承 <xref:System.Collections.CollectionBase> 類別的類別。  指定的型別也必須公開符合下列準則的 `Add` 方法。  
  
-   `Add` 方法必須可以從呼叫集合初始設定式的範圍中使用。  如果可以存取集合的非公用方法，那麼您在使用集合初始設定式時，`Add` 方法就不必是公用方法。  
  
-   `Add` 方法必須是集合類別的執行個體成員或 `Shared` 成員，或是擴充方法。  
  
-   `Add` 方法必須存在，才能根據多載解析規則配合集合初始設定式中提供的型別。  
  
 例如，下列程式碼範例示範如何使用集合初始設定式來建立 `List(Of Customer)` 集合。  當程式碼執行時，每個 `Customer` 物件就會傳遞至泛型清單的 `Add(Customer)` 方法。  
  
 [!code-vb[VbVbalrCollectionInitializers#9](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/index_4.vb)]  
  
 在下列程式碼範例中，會示範不使用集合初始設定式的對等程式碼。  
  
 [!code-vb[VbVbalrCollectionInitializers#10](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/index_5.vb)]  
  
 如果集合具有 `Add` 方法，而且方法的參數符合 `Customer` 物件的建構函式，則可以在集合初始設定式內巢狀化 `Add` 方法的參數值，這在下節將會討論。  如果集合沒有這樣的 `Add` 方法，您可以建立這個方法做為擴充方法。  如需如何建立 `Add` 方法做為集合擴充方法的範例，請參閱 [How to: Create an Add Extension Method Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)。  如需如何建立可搭配集合初始設定式使用之自訂集合的範例，請參閱 [How to: Create a Collection Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)。  
  
## 巢狀化集合初始設定式  
 您可以將值巢狀置於集合初始設定式內，以便在所建立的集合中識別 `Add` 方法的特定多載。  傳遞至 `Add` 方法的值必須以逗點分隔，並放在大括號 \(`{}`\) 之中，就如同您在陣列常值或集合初始設定式中所做的一樣。  
  
 當您使用巢狀值建立集合時，會將巢狀值清單的每個項目當做引數傳遞至對應項目型別的 `Add` 方法。  例如，下列程式碼範例會建立 <xref:System.Collections.Generic.Dictionary%602>，其中索引鍵的型別為 `Integer`，而值的型別則為 `String`。  每個巢狀值清單都符合 `Dictionary` 的 <xref:System.Collections.Generic.Dictionary%602.Add%2A> 方法。  
  
 [!code-vb[VbVbalrCollectionInitializers#5](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/index_6.vb)]  
  
 前述程式碼範例相當於下列程式碼。  
  
 [!code-vb[VbVbalrCollectionInitializers#6](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/index_7.vb)]  
  
 只有第一層巢狀化的巢狀值清單會傳送至集合型別的 `Add` 方法。  較深層次的巢狀化則視為陣列常值，而且巢狀值清單都不符合任何集合的 `Add` 方法。  
  
## 相關主題  
  
|||  
|-|-|  
|標題|描述|  
|[How to: Create an Add Extension Method Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|示範如何建立呼叫擴充方法`Add` ，可以用來填入集合初始設定式中的值集合。|  
|[How to: Create a Collection Used by a Collection Initializer](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|示範如何藉由啟用使用集合初始設定式`Add`中實作的集合類別的方法`IEnumerable`。|  
  
## 請參閱  
 [集合](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)   
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md)   
 [Auto\-Implemented Properties](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)   
 [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)