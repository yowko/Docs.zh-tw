---
title: "執行個體建構函式 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "建構函式 [C#], 執行個體建構函式"
  - "執行個體建構函式 [C#]"
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# 執行個體建構函式 (C# 程式設計手冊)
當您使用 [new](../../../csharp/language-reference/keywords/new.md) 運算式建立的 [class](../../../csharp/language-reference/keywords/class.md) 的物件時，執行個體建構函式會用於建立並且初始化任一執行個體成員變數。  若要初始化 [static](../../../csharp/language-reference/keywords/static.md) 類別或是非靜態類別中的靜態變數，必須定義靜態建構函式。  如需詳細資訊，請參閱 [靜態建構函式](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)。  
  
 下列範例顯示執行個體建構函式：  
  
 [!code-cs[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/instance-constructors_1.cs)]  
  
> [!NOTE]
>  為了避免困擾，這個類別會包含公用欄位。  在撰寫程式碼的實際應用時，並不建議使用公用欄位，因為它允許程式中的任何方法以無限制和未經驗證的方式，存取物件內部的運作方法。  資料成員通常應該是私用的，並且只能經由類別方法和屬性存取。  
  
 當建立以 `CoOrds` 類別為基礎的物件時就會呼叫這個執行個體建構函式。  像這樣不使用引數的建構函式稱為「*預設建構函式*」\(Default Constructor\)。  然而，通常提供其他建構函式會很有用。  例如，您可以將建構函式加入 `CoOrds` 類別以允許指定資料成員的初始值：  
  
 [!code-cs[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/instance-constructors_2.cs)]  
  
 這可以讓要建立的 `CoOrd` 物件使用預設或特定初始值，如下所示：  
  
 [!code-cs[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/instance-constructors_3.cs)]  
  
 如果類別沒有任何的建構函式，則會自動產生預設建構函式，而預設值會用於初始化欄位。  例如，[int](../../../csharp/language-reference/keywords/int.md) 初始化為 0。  如需預設值的詳細資訊，請參閱[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)。  因此，由於 `CoOrds` 類別預設建構函式會將所有的資料成員初始化為零，所以能夠在不改變類別運作方式的情況下全部移除。  本主題稍後的「範例 1」會提供使用多個建構函式的完整範例，在「範例 2」中則會提供自動產生之建構函式的範例。  
  
 執行個體建構函式也可以用來呼叫基底類別的執行個體建構函式。  類別建構函式可透過初始設定式叫用基底類別的建構函式，例如：  
  
 [!code-cs[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/instance-constructors_4.cs)]  
  
 在這個範例中，`Circle` 類別會將代表半徑和高度的值傳遞至 `Shape` \(`Circle` 就是由此衍生\) 提供的建構函式。  本主題中的「範例 3」會示範使用 `Shape` 和 `Circle` 的完整範例。  
  
## 範例 1  
 下列範例示範具有兩個類別建構函式的類別，其中一個沒有引數，另一個有兩個引數。  
  
 [!code-cs[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/instance-constructors_5.cs)]  
  
## 範例 2  
 在這個範例中，`Person` 類別不具有任何的建構函式，在該情形中，會自動提供預設的建構函式並且將欄位初始化為預設值。  
  
 [!code-cs[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/instance-constructors_6.cs)]  
  
 請注意，`age` 的預設值為 `0`，`name` 的預設值為 `null`。  如需預設值的詳細資訊，請參閱[預設值表](../../../csharp/language-reference/keywords/default-values-table.md)。  
  
## 範例 3  
 下列範例示範使用基底類別初始設定式。  `Circle` 類別衍生自一般類別 `Shape`，`Cylinder` 類別衍生自 `Circle` 類別。  每一個衍生類別上的建構函式使用其基底類別初始設定式。  
  
 [!code-cs[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/instance-constructors_7.cs)]  
  
 如需叫用基底類別建構函式的更多範例，請參閱 [虛擬](../../../csharp/language-reference/keywords/virtual.md)、[override](../../../csharp/language-reference/keywords/override.md) 和 [base](../../../csharp/language-reference/keywords/base.md)。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [解構函式](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [static](../../../csharp/language-reference/keywords/static.md)