---
title: "使用動態類型 (C# 程式設計手冊) | Microsoft Docs"
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
  - "動態 [C#], 關於動態類型"
  - "動態類型 [C#]"
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
caps.latest.revision: 30
caps.handback.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 使用動態類型 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp_dev10_long_md.md)] 引進一種新型別 `dynamic`。  此型別是靜態型別，但型別為 `dynamic` 的物件會略過靜態型別檢查。  在大部分的情況下，其運作會像是具有 `object` 型別。  在編譯時期，會假設型別為 `dynamic` 的項目能夠支援所有作業。  因此，您無須考慮物件是從 COM API、動態語言 \(例如 IronPython\)、HTML 文件物件模型 \(DOM\)、反映或是程式其他地方取得其值。  不過，如果程式碼無效，則會在執行階段攔截到錯誤。  
  
 例如，如果下列程式碼中的執行個體方法 `exampleMethod1` 只有一個參數，則編譯器會將第一個方法呼叫 `ec.exampleMethod1(10, 4)` 視同無效，因為呼叫中包含兩個引數。  此呼叫會造成編譯器錯誤。  編譯器不會檢查第二個方法呼叫 `dynamic_ec.exampleMethod1(10, 4)`，因為 `dynamic_ec` 的型別是 `dynamic`。  因此，不會報告編譯器錯誤。  但是這項錯誤並不是永遠不會被發現，  執行階段會攔截到錯誤，並產生執行階段例外狀況。  
  
 [!CODE [CsProgGuideTypes#50](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#50)]  
  
 [!CODE [CsProgGuideTypes#56](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#56)]  
  
 上述範例中的編譯器角色，就是將每個陳述式應該對型別為 `dynamic` 的物件或運算式所進行之動作的相關資訊包裝在一起。  到了執行階段會檢驗這些儲存資訊，如果有任何陳述式是無效的，便會產生執行階段例外狀況。  
  
 大部分動態作業的結果就是其本身 \(`dynamic`\)。  例如，在下列範例中，如果您將滑鼠指標停在 `testSum` 的使用用途上，IntelliSense 會顯示型別 \[**\(區域變數\) dynamic testSum**\]。  
  
 [!CODE [CsProgGuideTypes#51](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#51)]  
  
 結果不是 `dynamic` 的作業包括從 `dynamic` 轉換為其他型別，以及包括 `dynamic` 型別之引數的建構函式呼叫。  例如，下列宣告中 `testInstance` 的型別是 `ExampleClass`，不是 `dynamic`。  
  
 [!CODE [CsProgGuideTypes#52](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#52)]  
  
 下一節＜轉換＞會顯示轉換範例。  
  
## 轉換  
 動態物件和其他型別間的轉換很簡單。  如此可讓開發人員在動態和非動態行為之間進行切換。  
  
 所有物件都能隱含轉換為動態型別，如下列範例所示。  
  
 [!CODE [CsProgGuideTypes#53](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#53)]  
  
 相反的，隱含轉換可以動態套用至任何型別為 `dynamic` 的運算式。  
  
 [!CODE [CsProgGuideTypes#54](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#54)]  
  
## 具有 dynamic 型別引數的多載解析  
 如果方法中有一個或多個引數具有型別 `dynamic`，或如果方法呼叫的接收端是型別 `dynamic`，則多載解析會發生在執行階段，而非編譯時期。  在下列範例中，如果唯一可存取的 `exampleMethod2` 方法被定義為接受字串引數，則將 `d1` 做為引數傳送不會造成編譯器錯誤，但會引起執行階段例外狀況。  多載解析在執行階段會失敗，因為 `d1` 的執行階段型別是 `int`，但 `exampleMethod2` 需要的是字串。  
  
 [!CODE [CsProgGuideTypes#55](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#55)]  
  
## Dynamic Language Runtime  
 Dynamic Language Runtime \(DLR\) 是 [!INCLUDE[net_v40_short](../../../csharp/programming-guide/types/includes/net_v40_short_md.md)] 中的新 API。  它提供的基礎結構支援 C\# 中的 `dynamic` 型別，也支援實作 IronPython 和 IronRuby 之類的動態程式設計語言。  如需 DLR 的詳細資訊，請參閱 [Dynamic Language Runtime 概觀](../Topic/Dynamic%20Language%20Runtime%20Overview.md)。  
  
## COM Interop  
 [!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp_dev10_long_md.md)] 包含數種可改善與 COM API \(例如 Office Automation API\) 相互操作之經驗的功能。  其中有一項改善功能是使用 `dynamic` 型別，另一項是使用[具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)。  
  
 許多 COM 方法都允許針對引數型別和傳回型別進行變化，方法是將型別指定為 `object`。  但這需要對值進行明確轉型，才能與 C\# 中的強型別變數配合使用。  如果您使用 [\/link \(Link to COM Assembly\)](../../../csharp/language-reference/compiler-options/link-compiler-option.md) 選項進行編譯，則採用 `dynamic` 型別就能讓您將 COM 簽章中的 `object` 項目視同 `dynamic` 型別，如此就不用進行轉型。  例如，下列陳述式將比較使用 `dynamic` 型別和不使用 `dynamic` 型別存取 Microsoft Office Excel 試算表中的儲存格。  
  
 [!code-cs[csOfficeWalkthrough#12](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_1.cs)]  
  
 [!code-cs[csOfficeWalkthrough#13](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_2.cs)]  
  
## 相關主題  
  
|標題|描述|  
|--------|--------|  
|[dynamic](../../../csharp/language-reference/keywords/dynamic.md)|說明 `dynamic` 關鍵字的使用方法。|  
|[Dynamic Language Runtime 概觀](../Topic/Dynamic%20Language%20Runtime%20Overview.md)|提供 DLR 概觀，DLR 是在 Common Language Runtime \(CLR\) 中加入了一組動態語言服務的執行階段環境。|  
|[逐步解說：建立和使用動態物件](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)|針對建立自訂動態物件以及建立專案用於存取 `IronPython` 程式庫，提供逐步指示。|  
|[如何：使用 Visual C\#  功能存取 Office Interop 物件](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)|說明如何使用具名和選擇性引數、`dynamic` 型別，以及其他可簡化 Office API 物件存取方式的增強功能，來建立專案。|