---
title: "列舉類型 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "位元旗標 [C#]"
  - "C# 語言, 列舉"
  - "列舉 [C#]"
  - "列舉 [C#]"
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 列舉類型 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

列舉型別 \(也稱為列舉\) 提供有效的方式，讓您定義一組可以指派給變數的具名整數常數。  例如，假設您必須定義的變數的值是代表星期幾。  則只有 7 個有意義的值是該變數所要儲存的。  若要定義這些值，您可以使用列舉型別，這是藉由使用 [enum](../../csharp/language-reference/keywords/enum.md) 關鍵字來宣告的。  
  
 [!CODE [csProgGuideEnums#1](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideEnums#1)]  
  
 根據預設，列舉中每個項目的基礎型別是 [int](../../csharp/language-reference/keywords/int.md)。  您可以使用冒號指定其他整數數字型別 \(Numeric Type\)，如前述範例所示。  如需可能型別的完整清單，請參閱 [enum \(C\# 參考\)](../../csharp/language-reference/keywords/enum.md)。  
  
 您可以透過轉型驗證基本數值為基礎型別，，如下列範例所示。  
  
```c#  
Days today = Days.Monday;  
int dayNumber =(int)today;  
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);  
  
Months thisMonth = Months.Dec;  
byte monthNumber = (byte)thisMonth;  
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);  
  
// Output:  
// Monday is day number #1.  
// Dec is month number #11.  
```  
  
 使用列舉取代數字型別的好處如下：  
  
-   您可以為用戶端程式碼清楚指定變數的有效值。  
  
-   [!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)] 中的 IntelliSense 會列出所定義的值。  
  
 在您沒有為列舉程式清單的項目指定值時，會以 1 自動累加這些值。  在前述範例中，`Days.Sunday` 的值為 0，而 `Days.Monday` 的值為 1，以此類推。  如果在建立新 `Days` 物件時沒有明確指派值，則會使用預設值 `Days.Sunday` \(0\)。  所以在您建立列舉時，請選取邏輯上最適合的預設值，並讓其值為零。  這樣在建立列舉時即使沒有明確指派值，所有的列舉都會使用該預設值。  
  
 如果變數 `meetingDay` 的型別是 `Days`，則 \(在沒有明確轉型的情況下\) 您只可以指派 `Days` 所定義的其中一個值給它。  而且在會議日變更時，您可以從 `Days` 指派新值給 `meetingDay`：  
  
 [!CODE [csProgGuideEnums#4](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideEnums#4)]  
  
> [!NOTE]
>  您可以指派任意整數值給 `meetingDay`。  例如，這行程式碼並不會產生錯誤：`meetingDay = (Days) 42`。  然而，您應該避免這樣做，因為使用列舉變數，即隱含意味著列舉變數只會持有列舉所定義的其中一個值。  所以，指派任意值給列舉型別的變數，極可能會產生錯誤。  
  
 您可以指派任何值給列舉型別的列舉值清單中的項目，而且也可以使用計算值：  
  
 [!CODE [csProgGuideEnums#3](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideEnums#3)]  
  
## 列舉型別做為位元旗標  
 您可以使用列舉型別定義位元旗標，這樣可以讓列舉型別的執行個體，儲存列舉值清單中所定義值的任何組合   \(當然，有些組合可能不具意義，或是程式碼中不允許這些組合\)。  
  
 您可以藉由適當套用 <xref:System.FlagsAttribute?displayProperty=fullName> 屬性並定義值來建立位元旗標列舉，這樣就可以對其執行 `AND`、`OR`、`NOT` 和 `XOR` 位元運算。  在位元旗標列舉中，使用零值加入具名常數代表著「未設定旗標」。在旗標不代表「未設定旗標」時，請勿將值設為零。  
  
 下列範例會定義另一個版本的 `Days` 列舉，名為 `Days2`。  `Days2` 具有 `Flags` 屬性，且每個值會指派為 2 的乘冪。  這樣可以讓所建立 `Days2` 變數的值為 `Days2.Tuesday` 和 `Days2.Thursday`。  
  
 [!CODE [csProgGuideEnums#2](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideEnums#2)]  
  
 若要對列舉設定旗標，請使用位元 `OR` 運算子，如下列範例所示：  
  
 [!CODE [csProgGuideEnums#6](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideEnums#6)]  
  
 若要判斷是否有設定特定旗標，請使用位元 `AND` 運算，如下列範例所示：  
  
 [!CODE [csProgGuideEnums#7](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideEnums#7)]  
  
 如需使用 <xref:System.FlagsAttribute?displayProperty=fullName> 屬性定義列舉型別時的考慮事項的詳細資訊，請參閱 <xref:System.Enum?displayProperty=fullName>。  
  
## 使用 System.Enum 方法探索和處理列舉值  
 所有的列舉都是 <xref:System.Enum?displayProperty=fullName> 型別的執行個體。  您無法從 <xref:System.Enum?displayProperty=fullName> 衍生新類別，但對於列舉執行個體中的值，您可以使用方法探索其資訊並進行處理。  
  
 [!CODE [csProgGuideEnums#5](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideEnums#5)]  
  
 如需詳細資訊，請參閱<xref:System.Enum?displayProperty=fullName>。  
  
 您也可以使用擴充方法建立列舉的新方法。  如需詳細資訊，請參閱[如何：建立列舉類型的新方法](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md)。  
  
## 精選書籍章節  
 [更多關於變數](http://go.microsoft.com/fwlink/?LinkId=221230) 在 [啟動 Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## 請參閱  
 <xref:System.Enum?displayProperty=fullName>   
 [C\# 程式設計手冊](../../csharp/programming-guide/index.md)   
 [enum](../../csharp/language-reference/keywords/enum.md)