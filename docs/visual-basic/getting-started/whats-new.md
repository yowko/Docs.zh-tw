---
title: "Visual Basic 的新功能 | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- VB.StartPage.WhatsNew
dev_langs:
- VB
helpviewer_keywords:
- new features, Visual Basic
- what's new [Visual Basic]
- Visual Basic, what's new
ms.assetid: d7e97396-7f42-4873-a81c-4ebcc4b6ca02
caps.latest.revision: 145
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 55cf69a06a047c12f027007ed7180bf74307f2c9
ms.lasthandoff: 03/13/2017

---
# <a name="whats-new-for-visual-basic"></a>Visual Basic 的新功能
本頁列出每個 Visual Basic 版本的主要功能名稱，並說明該語言最新版本的新功能和增強功能。  
  
## <a name="previous-versions"></a>舊版本  
 Visual Basic / Visual Studio .NET 2002  
 初次發行  
  
 Visual Basic / Visual Studio .NET 2003  
 位元移位運算子、迴圈變數宣告  
  
 Visual Basic / Visual Studio .NET 2005  
 `My` 類型和協助程式類型 (應用程式、電腦、檔案系統、網路的存取)  
  
 Visual Basic / Visual Studio .NET 2008  
 Language Integrated Query (LINQ)、XML 常值、區域類型推斷、物件初始設定式、匿名類型、擴充方法、區域 `var` 類型推斷、Lambda 運算式、`if` 運算子、部分方法、可為 Null 的實值類型  
  
 Visual Basic / Visual Studio .NET 2010  
 自動實作的屬性、集合初始設定式、隱含行接續符號、動態、泛型共變數/反變數、全域命名空間存取  
  
 Visual Basic / Visual Studio .NET 2012  
 `Async` / `await`、迭代器、呼叫端資訊屬性  
  
 Visual Basic / Visual Studio .NET 2013  
 .NET 編譯器平台 ("Roslyn") 的技術預覽  
  
 Visual Basic / Visual Studio .NET 2015  
 目前的版本 (如下所示)  
  
## <a name="current-version"></a>目前版本  
 [Nameof](../../csharp/language-reference/keywords/nameof.md)  
 您可以取得用於錯誤訊息之類型或成員的未限定字串名稱，而不需要對字串進行硬式編碼。  這可讓您的程式碼在重構時保持正確。  這項功能也可用來連接模型檢視控制器 MVC 連結，以及引發屬性已變更事件。  
  
 [字串內插補點](../../csharp/language-reference/keywords/interpolated-strings.md)  
 您可以使用字串插值運算式來建構字串。  字串插值運算式類似包含運算式的範本字串。  對於引數而言，字串插值比[複合格式](../../standard/base-types/composite-format.md)更容易了解。  
  
 [Null 條件式成員存取和索引](../../csharp/language-reference/operators/null-conditional-operators.md)  
 您可以在執行成員存取 (`?.`) 或對 (`?[]`) 作業編製索引之前，透過非常精簡的語法來測試是否為 Null。  這些運算子可協助您撰寫較少的程式碼來處理 Null 檢查，特別是遞減至資料結構。  如果左運算元或物件參考為 Null，則作業會傳回 Null。  
  
 [多行字串常值](../../visual-basic/programming-guide/language-features/strings/string-basics.md)  
 字串常值可包含新行字元序列。  您不再需要使用 `<xml><![CDATA[...text with newlines...]]></xml>.Value` 的舊解決方法  
  
 註解  
 您可以將註解放到隱含行接續符號之後、初始設定式運算式之內和 LINQ 運算式詞彙之間。  
  
 更聰明的完整名稱解析  
 以程式碼 `Threading.Thread.Sleep(1000)` 為例，Visual Basic 之前會查詢命名空間 "Threading"，發現它在 System.Threading 和 System.Windows.Threading 之間模稜兩可，然後回報錯誤。  Visual Basic 現在會同時考慮這兩種可能的命名空間。  如果您顯示完成清單，Visual Studio 編輯器會在完成清單中列出這兩種類型的成員。  
  
 以年起始的日期常值  
 您可以有 yyyy-mm-dd 格式的日期常值 (`#2015-03-17 16:10 PM#`)。  
  
 唯讀介面屬性  
 您可以使用讀寫屬性來實作唯讀介面屬性。  這個介面可確保提供基本功能，並且不會防止實作類別允許設定屬性。  
  
 [TypeOf \<expr> IsNot \<類型>](../../visual-basic/language-reference/operators/typeof-operator.md)  
 為了增加程式碼的可讀性，您現在可以搭配使用 `TypeOf` 和 `IsNot`。  
  
 [#Disable Warning \<識別碼> 和 #Enable Warning \<識別碼>](../../visual-basic/language-reference/directives/directives.md)  
 您可以停用及啟用原始程式檔中區域的特定警告。  
  
 XML 文件註解增強功能  
 撰寫文件註解時，您會取得智慧型編輯器，以及驗證參數名稱、適當處理 `crefs` (泛型、運算子等)、色彩標示和重構的建置支援。  
  
 [部分模組和介面定義](../../visual-basic/language-reference/modifiers/partial.md)  
 除了類別和結構之外，您還可以宣告部分模組和介面。  
  
 [方法主體內的 #Region 指示詞](../../visual-basic/language-reference/directives/region-directive.md)  
 您可以將 #Region…#End Region 分隔符號放到檔案的任何位置及函式內，甚至是橫跨不同的函式主體。  
  
 [Overrides 定義隱含為 Overloads](../../visual-basic/language-reference/modifiers/overrides.md)  
 如果您將 `Overrides` 修飾詞加入定義，編譯器會隱含加入 `Overloads`，讓您可以在一般情況下輸入較少的程式碼。  
  
 屬性引數允許 CObj  
 編譯器之前會提供錯誤，指出 CObj(…) 用於屬性建構時不是常數。  
  
 從不同的介面宣告及使用模稜兩可的方法  
 之前，下列程式碼會產生錯誤，使您無法宣告 `IMock` 或呼叫 `GetDetails` (如果已在 C# 中宣告這些項目)：  
  
```vb  
Interface ICustomer  
  Sub GetDetails(x As Integer)  
End Interface  
  
Interface ITime  
  Sub GetDetails(x As String)  
End Interface  
  
Interface IMock : Inherits ICustomer, ITime  
  Overloads Sub GetDetails(x As Char)  
End Interface  
  
Interface IMock2 : Inherits ICustomer, ITime  
End Interface  
  
```  
  
 現在，編譯器會使用一般多載解析規則來選擇要呼叫的最適合 `GetDetails`，而且您可以在 Visual Basic 中宣告介面關聯性 (如範例所示)。  
  
## <a name="see-also"></a>請參閱  
 [Visual Studio 2017 的新功能](https://docs.microsoft.com/en-us/visualstudio/ide/whats-new-in-visual-studio)
