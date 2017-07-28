---
title: "集合初始設定式 (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.CollectionInitializer
dev_langs:
- VB
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 72ca6506d0bd867efa60ba73ecda72c32def129e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="collection-initializers-visual-basic"></a>集合初始設定式 (Visual Basic)
「集合初始設定式」提供簡短的語法，以讓您建立集合，並填入一組初始值。 當您透過一組已知值來建立集合時，集合初始設定式十分有用，例如，一份功能表選項或類別清單、一組初始數值、一份日期或月份名稱這類靜態字串清單，或用於驗證的這類省市清單的地理位置。  
  
 如需集合的詳細資訊，請參閱[集合](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)。  
  
 您可以使用後面接著大括弧 (`{}`) 的 `From` 關鍵字，來識別集合初始設定式。 這類似[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)中所述的陣列常值語法。 下列範例顯示使用集合初始設定式建立集合的各種方式。  
  
 [!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]  
  
> [!NOTE]
>  C# 也提供集合初始設定式。 C# 集合初始設定式所提供的功能與 Visual Basic 集合初始設定式相同。 如需 C# 集合初始設定式的詳細資訊，請參閱[物件和集合初始設定式](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。  
  
## <a name="syntax"></a>語法  
 集合初始設定式包含逗號分隔值清單，而這些值以大括弧 (`{}`) 括住而且前面加上 `From` 關鍵字，如下列程式碼所示。  
  
 [!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]  
  
 當您建立 <xref:System.Collections.Generic.List%601> 或 <xref:System.Collections.Generic.Dictionary%602> 這類集合時，必須在集合初始設定式之前提供集合類型，如下列程式碼所示。  
  
 [!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]  
  
> [!NOTE]
>  您無法合併使用集合初始設定式與物件初始設定式來初始化相同的集合物件。 您可以使用物件初始設定式來初始化集合初始設定式中的物件。  
  
## <a name="creating-a-collection-by-using-a-collection-intializer"></a>使用集合初始設定式來建立集合  
 當您使用集合初始設定式建立集合時，集合初始設定式中所提供的每個值都會傳遞給集合的適當 `Add` 方法。 例如，如果您使用集合初始設定式建立 <xref:System.Collections.Generic.List%601>，則會將集合初始設定式中的每個字串值傳遞給 <xref:System.Collections.Generic.List%601.Add%2A> 方法。 如果您想要使用集合初始設定式建立集合，則指定的類型必須是有效的集合類型。 有效集合類型的範例包括可實作 <xref:System.Collections.Generic.IEnumerable%601> 介面或繼承 <xref:System.Collections.CollectionBase> 類別的類別。 指定的類型也必須公開符合下列準則的 `Add` 方法。  
  
-   `Add` 方法必須可從將在其中呼叫集合初始設定式的範圍使用。 如果您在可存取集合之非公開方法的情況下使用集合初始設定式，則 `Add` 方法不一定要是公開的。  
  
-   `Add` 方法必須是集合類別的執行個體成員或 `Shared` 成員或是擴充方法。  
  
-   根據多載解析規則，`Add` 方法必須要符合集合初始設定式中所提供的類型。  
  
 例如，下列程式碼範例示範如何使用集合初始設定式，來建立 `List(Of Customer)` 集合。 程式碼執行時，每個 `Customer` 物件都會傳遞給泛型清單的 `Add(Customer)` 方法。  
  
 [!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]  
  
 下列程式碼範例示範未使用集合初始設定式的對等程式碼。  
  
 [!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]  
  
 如果集合的 `Add` 方法具有與 `Customer` 物件建構函式相符的參數，則可以將 `Add` 方法的參數值巢狀在集合初始設定式內，如下節所述。 如果集合沒有這類 `Add` 方法，您可以建立此方法作為擴充方法。 如需如何建立 `Add` 方法作為集合之擴充方法的範例，請參閱[如何：建立集合初始設定式所使用的 Add 擴充方法](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)。 如需如何建立可與集合初始設定式搭配使用之自訂集合的範例，請參閱[如何：建立集合初始設定式所使用的集合](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)。  
  
## <a name="nesting-collection-initializers"></a>巢狀集合初始設定式  
 您可以將值巢狀在集合初始設定式內，以識別所建立集合之 `Add` 方法的特定多載。 傳遞給 `Add` 方法的值必須以逗號區隔，並用大括弧 (`{}`) 括住，就像在陣列常值或集合初始設定式中一樣。  
  
 當您使用巢狀值來建立集合時，巢狀值清單的每個項目都會傳遞為符合項目類型之 `Add` 方法的引數。 例如，下列程式碼範例會建立 <xref:System.Collections.Generic.Dictionary%602>其中，索引鍵的類型為 `Integer`，而值的類型為 `String`。 每個巢狀值清單都會對應到 `Dictionary` 的 <xref:System.Collections.Generic.Dictionary%602.Add%2A> 方法。  
  
 [!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]  
  
 先前的程式碼範例等同於下列程式碼。  
  
 [!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]  
  
 只會將第一層巢狀層的巢狀值清單傳送至集合類型的 `Add` 方法。 更深入的巢狀層會視為陣列常值，而且巢狀值清單不會對應到任何集合的 `Add` 方法。  
  
## <a name="related-topics"></a>相關主題  
  
|標題|說明|  
|---|---|  
|[如何：建立集合初始設定式所使用的 Add 擴充方法](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|示範如何建立稱為 `Add` 的擴充方法，以用來將集合初始設定式中的值填入集合。|  
|[如何：建立集合初始設定式所使用的集合](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|示範如何將 `Add` 方法包括在可實作 `IEnumerable` 的集合類別中，以啟用集合初始設定式。|  
  
## <a name="see-also"></a>另請參閱  
 [集合](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)   
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [物件初始設定式：具名和匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)   
 [自動實作的屬性](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)   
 [如何：在 Visual Basic 中初始化陣列變數](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)   
 [區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [如何：建立項目清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)

