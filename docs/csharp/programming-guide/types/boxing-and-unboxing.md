---
title: "Boxing 和 Unboxing (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.boxing"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 語言，boxing"
  - "C# 語言，unboxing"
  - "unboxing [C#]"
  - "boxing [C#]"
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
caps.latest.revision: 34
caps.handback.revision: 34
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Boxing 和 Unboxing (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Boxing 是將[實值類型](../../../csharp/language-reference/keywords/value-types.md)轉換成 `object` 類型或是由這個實值類型實作之任何介面類型的程序。  當 CLR Box 處理實值類型時，它會將值包裝在 System.Object 內，並儲存到 Managed 堆積上。  Unbox 處理則會從物件中擷取實值類型。  Boxing 是隱含處理，unboxing 則是明確處理。  Boxing 和 unboxing 的概念是 C\# 類型系統統一檢視的基礎，其中任何類型的值都可視為物件。  
  
 在下列範例中，整數變數 `i` 會經過 *Box* 處理並且指派給物件 `o`。  
  
 [!CODE [csProgGuideTypes#14](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#14)]  
  
 接著就可以對物件 `o` 進行 Unbox 處理，並將該物件指派給整數變數 `i`：  
  
 [!CODE [csProgGuideTypes#15](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#15)]  
  
 下列範例將說明在 C\# 中使用 boxing 的方式。  
  
 [!CODE [csProgGuideTypes#47](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#47)]  
  
## 效能  
 相對於單純的指派，boxing 和 unboxing 是會耗費大量運算資源的處理序。  當實值類型經過 Box 處理時，必須配置及建構新的物件。  Unboxing 所需的轉換雖然較為簡單，但也同樣需要大量運算資源。  如需詳細資訊，請參閱[效能](../Topic/.NET%20Performance%20Tips.md)。  
  
## Boxing  
 Boxing 可用來儲存記憶體回收堆積中的實值類型。  Boxing 是一種隱含轉換，可將[實值類型](../../../csharp/language-reference/keywords/value-types.md)轉換成 `object` 類型，或是由這個實值類型實作的任何介面類型。  對實值類型進行 Boxing 處理時，會在堆積上配置物件執行個體，並將值複製到新物件中。  
  
 請考慮下列實值類型變數的宣告：  
  
 [!CODE [csProgGuideTypes#17](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#17)]  
  
 下列陳述式會以隱含方式對變數 `i` 套用 boxing 作業：  
  
 [!CODE [csProgGuideTypes#18](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#18)]  
  
 這個陳述式的結果是在堆疊上建立物件參考 `o`，用於參考堆積中 `int` 類型的值。  這個值是指派給變數 `i` 之實值類型值的複本。  `i` 和 `o` 這兩個變數之間的差異如下圖所示。  
  
 ![BoxingConversion 圖形](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")  
Boxing 轉換  
  
 您也可以執行明確的 boxing 處理，如同下列範例中所示，但是明確的 boxing 處理並非必要：  
  
 [!CODE [csProgGuideTypes#19](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#19)]  
  
## 描述  
 這個範例會使用 Boxing 將整數變數 `i` 轉換為物件 `o`。  接著，儲存在變數 `i` 中的值就會從 `123` 變更為 `456`。  這個範例顯示，原始實值類型以及經過 Box 處理的物件分別使用不同的記憶體位置，因此可以儲存不同的值。  
  
## 範例  
 [!CODE [csProgGuideTypes#16](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#16)]  
  
## Unboxing  
 Unboxing 是將 `object` 類型明確轉換成[實值類型](../../../csharp/language-reference/keywords/value-types.md)，或將介面類型明確轉換成實作介面之實值類型的程序。  Unboxing 作業包含：  
  
-   檢查物件執行個體，確定它是所指定實值類型經過 Box 處理的值。  
  
-   將值從執行個體複製到實值類型變數。  
  
 下列陳述式將示範 boxing 和 unboxing 作業：  
  
 [!CODE [csProgGuideTypes#21](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#21)]  
  
 下圖示範上述陳述式的結果。  
  
 ![UnBoxing 轉換圖形](../../../csharp/programming-guide/types/media/vcunboxingconversion.png "vcUnBoxingConversion")  
Unboxing 轉換  
  
 若要在執行階段成功對實值類型進行 Unbox 處理，要進行 Unbox 處理的項目必須是物件的參考，而且該物件是先前對該實值類型的執行個體進行 Box 處理所建立的物件。  嘗試對 `null` 進行 Unbox 處理會造成 <xref:System.NullReferenceException>。  嘗試對不相容的實值類型參考進行 Unbox 處理會造成 <xref:System.InvalidCastException>。  
  
## 範例  
 下列範例將示範 Unboxing 無效且產生 `InvalidCastException` 的案例。  若使用 `try` 和 `catch`，則會在發生錯誤時顯示錯誤訊息。  
  
 [!CODE [csProgGuideTypes#20](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#20)]  
  
 這個程式會輸出：  
  
 `Specified cast is not valid.  Error: Incorrect unboxing.`  
  
 如果您將陳述式：  
  
```  
int j = (short) o;  
```  
  
 變更為：  
  
```  
int j = (int) o;  
```  
  
 轉換將會執行，而且您會得到下列輸出結果：  
  
 `Unboxing OK.`  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 相關章節  
 如需詳細資訊：  
  
-   [參考類型](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [實值類型](../../../csharp/language-reference/keywords/value-types.md)  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)