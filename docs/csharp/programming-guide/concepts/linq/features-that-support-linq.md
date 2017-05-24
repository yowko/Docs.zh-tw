---
title: "支援 LINQ 的 C# 功能 | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f844e967e2abb7ea23e04a797017261e33bb4d75
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="c-features-that-support-linq"></a>支援 LINQ 的 C# 功能
下節將介紹 C# 3.0 中引進的新語言建構。 雖然這些新功能或多或少都會用於 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢，但不限於 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]，還可用於任何您認為實用的內容中。  
  
## <a name="query-expressions"></a>查詢運算式  
 查詢運算式使用類似於 SQL 或 XQuery 的宣告式語法來查詢 IEnumerable 集合。 在編譯時期，查詢語法會轉換成對 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 提供者實作的標準查詢運算子擴充方法進行的方法呼叫。 應用程式使用 `using` 指示詞來指定適當的命名空間，藉此控制範圍內的標準查詢運算子。 下列查詢運算式會擷取字串的陣列，然後根據字串的第一個字元分組字串，再排序這些群組。  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 如需詳細資訊，請參閱 [LINQ 查詢運算式](../../../../csharp/programming-guide/linq-query-expressions/index.md)。  
  
## <a name="implicitly-typed-variables-var"></a>隱含型別變數 (var)  
 除了在宣告和初始化變數時明確指定類型，您還可以使用 [var](../../../../csharp/language-reference/keywords/var.md) 修飾詞，指示編譯器推斷並指派類型，如下所示：  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 宣告為 `var` 的變數和明確指定類型的變數一樣具有強型別。 `var` 可用來建立匿名型別，但也可用於任何區域變數。 陣列也可以使用隱含型別進行宣告。  
  
 如需詳細資訊，請參閱[隱含型別區域變數](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。  
  
## <a name="object-and-collection-initializers"></a>物件和集合初始設定式  
 物件和集合初始設定式可以初始化物件，而不需要明確呼叫物件的建構函式。 初始設定式通常會用於將來源資料投影為新資料類型的查詢運算式中。 假設有個名為 `Customer` 的類別具有公用的 `Name` 和 `Phone` 屬性，則可如下列程式碼所示使用物件初始設定式：  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 如需詳細資訊，請參閱[物件和集合初始設定式](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。  
  
## <a name="anonymous-types"></a>匿名類型  
 匿名型別是由編譯器所建構，只有編譯器才知道類型名稱。 匿名型別提供了一個便利的方法，暫時將查詢結果中的一組屬性分組，而不需要另外定義具名類型。 匿名型別是以新的運算式和物件初始設定式進行初始化，如下所示：  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 如需詳細資訊，請參閱[匿名型別](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。  
  
## <a name="extension-methods"></a>擴充方法  
 擴充方法是一種可以與類型相關聯的靜態方法，因此可以像呼叫類型上的執行個體方法一樣呼叫它。 這項功能實際上可讓您「新增」方法至現有的類型，而不需要實際修改這些類型。 標準查詢運算子是一組擴充方法，可為實作 <xref:System.Collections.Generic.IEnumerable%601> 的任何類型提供 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 查詢功能。  
  
 如需詳細資訊，請參閱[擴充方法](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。  
  
## <a name="lambda-expressions"></a>Lambda 運算式  
 Lambda 運算式是一種內嵌函式，其使用 => 運算子分隔輸入參數與函式主體，而且可以在編譯期間轉換成委派或運算式樹狀架構。 在 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 程式設計中，當您直接對標準查詢運算子進行方法呼叫時，就會遇到 Lambda 運算式。  
  
 如需詳細資訊，請參閱:  
  
-   [匿名函式](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [Lambda 運算式](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [運算式樹狀架構 (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
  
## <a name="auto-implemented-properties"></a>自動實作的屬性  
 自動實作的屬性讓屬性宣告更簡潔。 當您如下列範例所示宣告屬性時，編譯器會建立私用、匿名的支援欄位，只能透過 getter 和 setter 屬性進行存取。  
  
```  
public string Name {get; set;}  
```  
  
 如需詳細資訊，請參閱[自動實作的屬性](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)。  
  
## <a name="see-also"></a>另請參閱  
 [Language-Integrated Query (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
