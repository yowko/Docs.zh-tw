---
title: "欄位 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "欄位 [C#]"
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
caps.latest.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 29
---
# 欄位 (C# 程式設計手冊)
「*欄位*」\(Field\) 是一個任意型別的變數，直接在[類別](../../../csharp/language-reference/keywords/class.md)或[建構](../../../csharp/language-reference/keywords/struct.md)中宣告。  欄位是其包含型別 \(Containing Type\) 的「*成員*」\(Member\)。  
  
 類別 \(Class\) 或結構 \(Struct\) 可能會有執行個體 \(Instance\) 欄位或靜態 \(Static\) 欄位，或者兩個都有。  執行個體欄位專屬於某個型別的執行個體。  如果您有類別 T 搭配執行個體欄位 F，則您可以建立兩個型別 T 的物件，然後修改每個物件中 F 的值，而不會影響到另一個物件中的值。  相較之下，靜態欄位屬於類別本身所有，在該類別的所有執行個體之間共用。  對執行個體 A 所做的變更，執行個體 B 和 C 只要存取該欄位就會馬上看到。  
  
 一般來說，欄位只應用在具有 private 或 protected 存取範圍的變數上。  類別公開 \(Expose\) 給用戶端程式碼的資料應透過[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)、[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)和[索引子](../../../csharp/programming-guide/indexers/index.md)來提供。  透過以這些建構來間接存取內部欄位，您可以防範無效的輸入值。  儲存由公用屬性公開之資料的私用欄位稱為「*支援存放區*」\(Backing Store\) 或「*支援欄位*」\(Backing Field\)。  
  
 欄位通常用來儲存必須由一個以上類別方法存取的資料，以及其儲存時間比任何單一方法的存留期 \(Lifetime\) 都還要長的資料。  例如，表示行事曆日期的類別有三個整數欄位，分別為月、日和年。  不會在單一方法以外範圍使用的變數，應在方法主體當中宣告為「*區域變數*」\(Local Variable\)。  
  
 您必須依序指定欄位的存取層級、欄位型別和欄位名稱，以在類別區塊中宣告欄位。  例如：  
  
 [!code-cs[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/fields_1.cs)]  
  
 若要存取物件中的欄位，請在物件名稱後加上句號，再加上欄位的名稱，就像是 `objectname.fieldname`。  例如：  
  
 [!code-cs[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/fields_2.cs)]  
  
 您可以在宣告欄位時使用指派運算子指定欄位的初始值。  例如，若要將 `day` 欄位自動指派為 `"Monday"`，您應該宣告 `day`，如下列範例所示：  
  
 [!code-cs[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/fields_3.cs)]  
  
 在物件執行個體 \(Instance\) 的建構函式 \(Constructor\) 即將進行呼叫之前，欄位就會進行初始化。  當建構函式指派欄位的值時，它就會覆寫在欄位宣告期間所指定的任何值。  如需詳細資訊，請參閱 [使用建構函式](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)。  
  
> [!NOTE]
>  欄位初始設定式無法參考其他執行個體欄位。  
  
 欄位可以標記為 [public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md) 或 `protected internal`。  這些存取修飾詞將定義類別使用者如何存取欄位。  如需詳細資訊，請參閱 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)。  
  
 欄位也可以選擇性地宣告為 [static](../../../csharp/language-reference/keywords/static.md)。  這讓呼叫端即使沒有類別的執行個體，也可以隨時使用該欄位。  如需詳細資訊，請參閱 [靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
 欄位可以宣告為 [readonly](../../../csharp/language-reference/keywords/readonly.md)。  若為唯讀欄位，就只能在初始化期間或在建構函式中指派值給該欄位。  `static` `readonly` 欄位非常類似於常數，唯一不同的是，C\# 編譯器無法在編譯時期存取靜態唯讀欄位的值，只有在執行階段才能這麼做。  如需詳細資訊，請參閱 [常數](../../../csharp/programming-guide/classes-and-structs/constants.md)。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [使用建構函式](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)   
 [繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)