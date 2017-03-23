---
title: "readonly (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "readonly_CSharpKeyword"
  - "readonly"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "readonly 關鍵字 [C#]"
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# readonly (C# 參考)
`readonly` 關鍵字是可以用於欄位的修飾詞。  欄位宣告如果包含 `readonly` 修飾詞，由宣告引入的欄位設定只能發生在宣告的一部分或者是相同類別裡的建構函式。  
  
## 範例  
 在這個範例中，`year` 欄位的值無法在方法 `ChangeYear` 中改變，即使在此類別建構函式中已指定值給它：  
  
 [!code-cs[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 您只能在下列內容裡對 `readonly` 欄位指定值：  
  
-   例如，當變數在宣告裡初始化時：  
  
    ```  
    public readonly int y = 5;  
    ```  
  
-   若是執行個體欄位，則在包含欄位宣告之類別的執行個體建構函式裡，或若是靜態欄位，則在包含欄位宣告之類別的靜態建構函式裡。  這些也是唯一能夠將 `readonly` 欄位當做 [out](../../../csharp/language-reference/keywords/out.md) 或 [ref](../../../csharp/language-reference/keywords/ref.md) 參數傳遞的有效內容。  
  
> [!NOTE]
>  `readonly` 關鍵字與 [const](../../../csharp/language-reference/keywords/const.md) 關鍵字不同。  `const` 欄位僅可以在該欄位宣告時初始化。  `readonly` 欄位則是可以在宣告或是在建構函式中初始化。  因此，`readonly` 欄位會根據使用的建構函式而產生不同值。  另外，`const` 欄位是編譯時期常數，而 `readonly` 欄位則可當做執行階段常數使用，如下列範例所示：  
  
```  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## 範例  
 [!code-cs[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]  
  
 上述範例裡，如果您使用像這樣的陳述式：  
  
 `p2.y = 66;        // Error`  
  
 您會獲得編譯器錯誤訊息：  
  
 `The left-hand side of an assignment must be an l-value`  
  
 這和您嘗試為常數設定值所得到的錯誤相同。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)   
 [const](../../../csharp/language-reference/keywords/const.md)   
 [欄位](../../../csharp/programming-guide/classes-and-structs/fields.md)