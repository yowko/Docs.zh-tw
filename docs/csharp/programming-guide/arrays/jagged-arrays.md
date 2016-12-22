---
title: "不規則陣列 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "陣列 [C#], 不規則"
  - "不規則陣列 [C#]"
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 不規則陣列 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

不規則陣列是一種陣列，其元素也是陣列。  不規則陣列的元素可以有不同維度及大小。  不規則陣列有時稱為「陣列中的陣列」。 下列範例會示範如何宣告、初始化和存取不規則陣列。  
  
 以下是一個一維陣列的宣告，其中有三個元素，而每個元素都是一維的整數陣列：  
  
 [!code-cs[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]  
  
 必須先初始化元素，才可以使用 `jaggedArray`。  初始化元素的方法如下：  
  
 [!code-cs[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]  
  
 每個元素都是一維的整數陣列。  第一個元素是具有五個整數的陣列，第二個是具有四個整數的陣列，而第三個是具有兩個整數的陣列。  
  
 您也可以使用初始設定式 \(Initializer\) 將值填入陣列元素，在此情況下，您就不需要陣列大小。  例如：  
  
 [!code-cs[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]  
  
 您也可以在宣告時初始化陣列，如下所示：  
  
 [!code-cs[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 您可使用下列縮寫格式：  請注意，由於元素沒有預設的初始設定，您不能從元素初始設定中移除 `new` 運算子。  
  
 [!code-cs[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 不規則陣列是指包含陣列的陣列，因此其元素為參考型別，而且會初始化為 `null`。  
  
 您可以存取個別陣列元素，如下列範例所示：  
  
 [!code-cs[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]  
  
 您也可以混合不規則陣列和多維陣列。  以下是一維不規則陣列的宣告和初始化，其中包含三個大小不同的二維陣列元素。  如需二維陣列的詳細資訊，請參閱[多維陣列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)。  
  
 [!code-cs[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]  
  
 如以下範例所示，您可以存取個別元素，其中顯示第一個陣列中元素 `[1,0]` 的值 \(`5` 值\)：  
  
 [!code-cs[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]  
  
 `Length` 方法會傳回包含在不規則陣列中的陣列數目。  例如，假設您已經宣告先前的陣列，以下這行：  
  
 [!code-cs[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]  
  
 會傳回 3 這個值。  
  
## 範例  
 以下範例會建立一個陣列，它的元素本身也是陣列。  每個陣列元素的大小都不同。  
  
 [!code-cs[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]  
  
## 請參閱  
 <xref:System.Array>   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [陣列](../../../csharp/programming-guide/arrays/index.md)   
 [一維陣列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [多維陣列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)