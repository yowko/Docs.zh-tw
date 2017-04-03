---
title: "使用動態類型 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
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
ms.openlocfilehash: f9ee1f0cae90120692fa4f41d2f432551281ab6d
ms.lasthandoff: 03/13/2017

---
# <a name="using-type-dynamic-c-programming-guide"></a>使用動態類型 (C# 程式設計手冊)
[!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp_dev10_long_md.md)] 引進一種新類型 `dynamic`。 此類型是靜態類型，但 `dynamic` 類型的物件會略過靜態類型檢查。 在大多數情況下，其運作會像是具有 `object` 類型。 在編譯時期，會假設類型為 `dynamic` 的項目能夠支援所有作業。 因此，您無須考慮物件是從 COM API、動態語言 (例如 IronPython)、HTML 文件物件模型 (DOM)、反映或是程式其他地方取得其值。 不過，如果程式碼無效，則會在執行階段攔截到錯誤。  
  
 例如，如果下列程式碼中的執行個體方法 `exampleMethod1` 只有一個參數，則編譯器會將 `ec.exampleMethod1(10, 4)` 方法的第一個呼叫視為無效，因為它包含兩個引數。 呼叫會造成編譯器錯誤。 編譯器不會檢查 `dynamic_ec.exampleMethod1(10, 4)` 方法的第二個呼叫，因為 `dynamic_ec` 的類型為 `dynamic`。 因此，不會報告編譯器錯誤。 不過，這項錯誤並不是永遠不會被發現。 它會在執行階段被攔截，並造成執行階段例外狀況。  
  
 [!code-cs[CsProgGuideTypes#50](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_1.cs)]  
  
 [!code-cs[CsProgGuideTypes#56](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_2.cs)]  
  
 上述範例中的編譯器角色，就是將每個陳述式應該對類型為 `dynamic` 的物件或運算式所進行之動作的相關資訊封裝在一起。 在執行階段，會檢查這些預存資訊，如果有任何陳述式無效，便會造成執行階段例外狀況。  
  
 大多數動態作業的結果本身就是 `dynamic`。 例如，如果您在下列範例中將滑鼠指標停在 `testSum` 的使用用途上，IntelliSense 會顯示 **(區域變數) dynamic testSum** 類型。  
  
 [!code-cs[CsProgGuideTypes#51](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_3.cs)]  
  
 結果不是 `dynamic` 的作業包括從 `dynamic` 轉換成另一種類型，以及包含 `dynamic` 類型引數的建構函式呼叫。 例如，下列宣告中 `testInstance` 的類型是 `ExampleClass`，而不是 `dynamic`。  
  
 [!code-cs[CsProgGuideTypes#52](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_4.cs)]  
  
 下一節＜轉換＞會顯示轉換範例。  
  
## <a name="conversions"></a>轉換  
 動態物件和其他類型間的轉換很簡單。 因此，開發人員可以在動態和非動態行為之間進行切換。  
  
 所有物件都能隱含轉換成動態類型，如下列範例所示。  
  
 [!code-cs[CsProgGuideTypes#53](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_5.cs)]  
  
 相反地，隱含轉換可以動態套用至 `dynamic` 類型的任何運算式。  
  
 [!code-cs[CsProgGuideTypes#54](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_6.cs)]  
  
## <a name="overload-resolution-with-arguments-of-type-dynamic"></a>dynamic 類型引數的多載解析  
 如果方法呼叫中有一或多個引數的類型為 `dynamic`，或如果方法呼叫的接收端類型為 `dynamic`，則會在執行階段 (而不是編譯時期) 發生多載解析。 在下列範例中，如果唯一可存取的 `exampleMethod2` 方法已定義為接受字串引數，則將 `d1` 作為引數傳送不會造成編譯器錯誤，但會造成執行階段例外狀況。 多載解析會在執行階段失敗，因為 `d1` 的執行階段類型為 `int`，而 `exampleMethod2` 需要字串。  
  
 [!code-cs[CsProgGuideTypes#55](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-type-dynamic_7.cs)]  
  
## <a name="dynamic-language-runtime"></a>Dynamic Language Runtime  
 Dynamic Language Runtime (DLR) 是 [!INCLUDE[net_v40_short](../../../csharp/programming-guide/types/includes/net_v40_short_md.md)] 中的新 API。 它提供的基礎結構支援 C# 中的 `dynamic` 類型，也支援實作 IronPython 和 IronRuby 之類的動態程式設計語言。 如需 DLR 的詳細資訊，請參閱 [Dynamic Language Runtime 概觀](http://msdn.microsoft.com/library/f769a271-8aff-4bea-bfab-6160217ce23d)。  
  
## <a name="com-interop"></a>COM Interop  
 [!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp_dev10_long_md.md)] 包含幾項功能，可改善與 COM API (例如 Office Automation API) 相互操作的體驗。 這些改進包括使用 `dynamic` 類型，以及使用[具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)。  
  
 許多 COM 方法允許針對引數類型和傳回型別進行變化，方法是將類型指定為 `object`。 這需要對值進行明確轉型，才能與 C# 中的強型別變數配合使用。 如果您使用 [/link (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/link-compiler-option.md) 選項進行編譯，則引進 `dynamic` 類型可讓您將 COM 簽章中出現的 `object` 項目視為具有 `dynamic` 類型，藉此避免大部分的轉型。 例如，下列陳述式將比較使用 `dynamic` 類型和不使用 `dynamic` 類型存取 Microsoft Office Excel 試算表中儲存格的方式。  
  
 [!code-cs[csOfficeWalkthrough#12](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_8.cs)]  
  
 [!code-cs[csOfficeWalkthrough#13](../../../csharp/programming-guide/interop/codesnippet/CSharp/using-type-dynamic_9.cs)]  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[dynamic](../../../csharp/language-reference/keywords/dynamic.md)|說明如何使用 `dynamic` 關鍵字。|  
|[Dynamic Language Runtime 概觀](http://msdn.microsoft.com/library/f769a271-8aff-4bea-bfab-6160217ce23d)|提供 DLR 概觀，DLR 是在 Common Language Runtime (CLR) 中新增一組動態語言服務的執行階段環境。|  
|[逐步解說：建立和使用動態物件](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)|針對建立自訂動態物件及建立存取 `IronPython` 程式庫的專案，提供逐步指示。|  
|[如何：使用 Visual C# 功能存取 Office Interop 物件](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)|示範如何建立使用具名和選擇性引數、`dynamic` 類型，以及其他可簡化 Office API 物件存取之增強功能的專案。|
