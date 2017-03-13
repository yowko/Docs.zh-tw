---
title: "靜態類別和靜態類別成員 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言, 靜態類別"
  - "C# 語言, 靜態成員"
  - "靜態類別成員 [C#]"
  - "靜態類別 [C#]"
  - "靜態成員 [C#]"
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
caps.latest.revision: 49
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 49
---
# 靜態類別和靜態類別成員 (C# 程式設計手冊)
[靜態](../../../csharp/language-reference/keywords/static.md)類別基本上跟非靜態類別相同，但有一個差別：靜態類別不能具現化 \(Instantiated\)。  換句話說，您不能使用 [new](../../../csharp/language-reference/keywords/new.md) 關鍵字建立類別型別的變數。  由於沒有執行個體變數，您要使用類別名稱本身存取靜態類別的成員。  例如，如果您有稱為 `UtilityClass` 的靜態類別，其中有稱為 `MethodA` 的公用方法，您必須如下列範例所示呼叫方法：  
  
```c#  
UtilityClass.MethodA();  
```  
  
 靜態類別能供只在輸入參數上作業，且不需要取得或設定任何內部執行個體欄位的方法集，做為方便的容器。  例如，在 .NET Framework 類別庫中，靜態 <xref:System.Math?displayProperty=fullName> 類別包含執行算術運算的方法，而完全不需要儲存或擷取 <xref:System.Math> 類別之特定執行個體的唯一性資料。  也就是說，您透過指定類別名稱和方法名稱套用類別的成員，如下列範例所示。  
  
```  
double dub = -3.14;  
Console.WriteLine(Math.Abs(dub));  
Console.WriteLine(Math.Floor(dub));  
Console.WriteLine(Math.Round(Math.Abs(dub)));  
  
// Output:  
// 3.14  
// -4  
// 3  
  
```  
  
 跟所有類別型別一樣，靜態類別的型別資訊，是由 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] Common Language Runtime \(CLR\) 在載入參考該類別的程式時載入。程式無法確實指定何時載入類別。  然而，類別卻能保證一定會載入，並會在您的程式第一次參考此類別前，先讓其中的欄位初始化，而其中的靜態建構函式也受到呼叫。  靜態建構函式只會受到一次呼叫，而後在您程式所在的應用程式定義域的存留期 \(Lifetime\) 中，都會在記憶體中保留靜態類別。  
  
> [!NOTE]
>  若要建立一個非靜態類別，僅允許為其本身建立一個執行個體，請參閱[在 C\# 中實作單一類別](http://msdn2.microsoft.com/zh-tw/library/ms998558.aspx) \(英文\)。  
  
 下列清單會提供靜態類別的主要特色：  
  
-   只包含靜態成員。  
  
-   無法具現化。  
  
-   是密封的。  
  
-   不能包含[執行個體建構函式](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)。  
  
 因此基本上，建立靜態類別就是建立只包含靜態成員和私用建構函式 \(Private Constructor\) 的類別。  私用建構函式可讓類別避免執行個體化。  使用靜態類別的好處是，編譯器可進行檢查，確定不會在不小心的情況下加入執行個體成員。  編譯器將可確保這個類別不會建立執行個體。  
  
 靜態類別是密封的，因此無法繼承。  它們不能繼承自 <xref:System.Object> 以外的任何類別。  靜態類別不能包含執行個體建構函式。不過，它們可以包含靜態建構函式。  非靜態類別如果包含需要非一般初始化的靜態成員，則也應該定義靜態建構函式。  如需詳細資訊，請參閱 [靜態建構函式](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)。  
  
## 範例  
 下面是靜態類別的範例，該類別包含可來回換算攝氏溫度與華氏溫度的兩個方法：  
  
 [!code-cs[csProgGuideObjects#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_1.cs)]  
  
## 靜態成員  
 非靜態類別能包含靜態方法、欄位、屬性或事件。  即使沒有建立類別的任何執行個體，還是可以在類別上呼叫靜態成員。  靜態成員永遠以類別名稱存取，而不以執行個體名稱存取。  不管一個類別建立多少個執行個體，還是只能有一個靜態成員的複本存在。  除非明確傳遞了方法參數，否則靜態方法和屬性不能在包含的型別中存取非靜態欄位與事件，也不能存取任何物件的執行個體變數。  
  
 比起將整個類別宣告為靜態，以一些靜態成員宣告非靜態類別是較典型的方法。  靜態欄位有兩個常見的作用，分別是計算已具現化的物件數，或儲存必須在所有執行個體間共用的值。  
  
 靜態方法由於屬於類別而不屬於類別的任何執行個體，因此能多載但不能覆寫。  
  
 雖然欄位不能宣告為 `static const`，[const](../../../csharp/language-reference/keywords/const.md) 欄位的行為基本上是靜態的，  屬於型別，而非型別的執行個體。  因此，const 欄位可透過用於靜態欄位的相同 `ClassName.MemberName` 標記法存取，  不需要任何物件執行個體。  
  
 C\# 不支援靜態區域變數 \(在方法範圍中宣告的變數\)。  
  
 您要使用 `static` 關鍵字，在成員的傳回型別前宣告靜態類別成員，如下列範例所示：  
  
 [!code-cs[csProgGuideObjects#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_2.cs)]  
  
 靜態成員會在第一次受到存取前，以及靜態建構函式 \(如果有\) 受到呼叫之前進行初始化。  若要存取靜態類別成員，請使用類別名稱 \(而非變數名稱\) 指定成員的位置，如下列範例所示：  
  
 [!code-cs[csProgGuideObjects#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_3.cs)]  
  
 如果您的類別包含靜態欄位，請提供在類別載入時會將其初始化的靜態建構函式。  
  
 對靜態方法的呼叫會在 Microsoft Intermediate Language \(MSIL\) 中產生呼叫指令，同時對執行個體方法的呼叫會產生 `callvirt` 指令，並會檢查 null 物件參考。  然而在大部分情況中，這兩者之間的效能差異並不顯著。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [static](../../../csharp/language-reference/keywords/static.md)   
 [類別](../../../csharp/programming-guide/classes-and-structs/classes.md)   
 [Class \- 類別](../../../csharp/language-reference/keywords/class.md)   
 [靜態建構函式](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)   
 [執行個體建構函式](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)