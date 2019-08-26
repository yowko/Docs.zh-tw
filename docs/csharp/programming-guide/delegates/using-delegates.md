---
title: 使用委派 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], how to use
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
ms.openlocfilehash: 6f4044591c2cd8d59970d8d2f6e65c51ce7498ff
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590554"
---
# <a name="using-delegates-c-programming-guide"></a>使用委派 (C# 程式設計手冊)
[委派](../../language-reference/keywords/delegate.md)是可以安全封裝方法的類型，類似於 C 和 C++ 中的函式指標。 與 C 函式指標不同之處在於，委派為物件導向且類型安全，同時安全性較佳。 委派的類型由委派的名稱所定義。 下列範例宣告名為 `Del` 的委派，其可封裝採用[字串](../../language-reference/keywords/string.md)作為引數並傳回 [void](../../language-reference/keywords/void.md) 的方法：  
  
 [!code-csharp[csProgGuideDelegates#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#21)]  
  
 通常會透過提供委派將包裝的方法名稱，或使用[匿名函式](../statements-expressions-operators/anonymous-functions.md)，來建構委派物件。 一旦對委派執行個體化之後，該委派即會將該委派的方法呼叫，傳遞至該方法。 由呼叫端傳遞至委派的參數，會傳遞至該方法，而從該方法傳回的值（如果有的話）會由該委派傳回至呼叫端。 這稱為叫用委派。 執行個體化的委派的叫用方法，就像其自身為包裝的方法一樣。 例如：  
  
 [!code-csharp[csProgGuideDelegates#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#22)]  
  
 [!code-csharp[csProgGuideDelegates#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#23)]  
  
 委派類型衍生自 .NET Framework 中的 <xref:System.Delegate> 類別。 委派類型是[密封](../../language-reference/keywords/sealed.md)的，不能作為其他類型的衍生來源，且不可能從 <xref:System.Delegate> 衍生自訂類別。 因為執行個體化的委派是物件，所以它可以做為參數傳遞或指派給屬性。 這可讓方法以參數方式接受委派，並於稍後呼叫委派。 這稱為非同步回呼，是較長處理序完成時通知呼叫端的常用方法。 以這種方式使用委派時，使用委派的程式碼不需要了解如何實作所用的方法。 該功能類似於介面提供的封裝。  
  
 回呼的另一種常見用法是定義自訂比較方法，並將該委派傳遞至排序方法。 它可讓呼叫端程式碼成為排序演算法的一部分。 下列的範例方法使用 `Del` 類型做為參數：  
  
 [!code-csharp[csProgGuideDelegates#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#24)]  
  
 然後，您可以將上述所建立的委派傳遞至該方法：  
  
 [!code-csharp[csProgGuideDelegates#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#25)]  
  
 並且會在主控台中收到下列輸出：  
  
 `The number is: 3`  
  
 使用委派做為抽象概念，`MethodWithCallback` 不需要直接呼叫主控台 — 設計時不需要一直考慮主控台。 `MethodWithCallback` 所做的只是準備一個字串，然後將該字串傳遞給另一個方法。 這項功能十分強大，因為委派的方法可以使用任何數目的參數。  
  
 當委派建構為要包裝執行個體方法時，該委派會參考執行個體與方法。 除了委派所包裝的方法之外，委派也不會知道執行個體的類型，因此委派可參考任何類型的物件，只要該物件上存在符合委派簽章的方法即可。 當委派建構為會包裝靜態方法時，它只會參考該方法。 請考慮下列宣告：  
  
 [!code-csharp[csProgGuideDelegates#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#26)]  
  
 連同先前所示的靜態 `DelegateMethod`，我們現在有三種方法，可以由 `Del` 執行個體進行包裝。  
  
 叫用委派時，可以呼叫一個以上的方法。 這稱為多點傳送。 若要將一個額外的方法加入委派的方法清單 (引動過程清單)，只需使用加法或加法指派運算子 ('+' 或 '+ =')，相加兩個委派即可。 例如：  
  
 [!code-csharp[csProgGuideDelegates#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#27)]  
  
 此時，`allMethodsDelegate` 在其引動過程清單中包含三種方法：`Method1`、`Method2` 和 `DelegateMethod`。 原始的三個委派 `d1`、`d2` 和 `d3` 維持不變。 當叫用 `allMethodsDelegate` 時，會依序呼叫所有三個方法。 如果委派使用參考參數，則參考會依序傳入這三個方法中的每一個，而且任一方法所做的任何變更，下一個方法都看得到。 當任一方法擲回未在該方法內攔截到例外狀況時，該例外狀況會傳遞至委派的呼叫端，且不會呼叫引動過程清單中的任何後續方法。 如果委派具有傳回值和 (或) 輸出參數，則它會傳回所叫用之最後一個方法的傳回值與參數。 若要將方法從引動過程清單中移除，請使用[減去或減去指派運算子](../../language-reference/operators/subtraction-operator.md) (`-` 或 `-=`)。 例如：  
  
 [!code-csharp[csProgGuideDelegates#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#28)]  
  
 因為委派類型衍生自 `System.Delegate`，所以可以在委派上呼叫該類別所定義的方法和屬性。 例如，若要求解委派引動過程清單中方法的數目，可以撰寫如下：  
  
 [!code-csharp[csProgGuideDelegates#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#29)]  
  
 其委派引動過程清單中有一個以上方法的委派，衍生自 <xref:System.MulticastDelegate>，即 `System.Delegate` 的子類別。 上述程式碼可以在任一情況下運作，因為這兩個類別都支援 `GetInvocationList`。  
  
 多點傳送委派常用於事件處理。 事件來源物件會將事件通知傳送給已註冊希望收到該事件的收件者物件。 若要註冊接收事件，收件者會建立旨在處理事件的方法，然後建立該方法的委派，並將該委派傳遞至事件來源。 在發生事件時，來源會呼叫委派。 接著，委派會呼叫收件者的事件處理方法，傳遞事件資料。 指定的事件之委派類型，由事件來源定義。 如需詳細資訊，請參閱[事件](../events/index.md)。  
  
 比較兩個在編譯時間所指定的不同類型之委派，會導致編譯錯誤。 如果委派執行個體是靜態類型的 `System.Delegate`，則允許比較，但會在執行階段傳回 false。 例如：  
  
 [!code-csharp[csProgGuideDelegates#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#30)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [委派](./index.md)
- [在委派中使用變異數](../concepts/covariance-contravariance/using-variance-in-delegates.md)
- [委派中的變異數](../concepts/covariance-contravariance/variance-in-delegates.md)
- [針對 Func 與 Action 泛型委派使用變異數](../concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
- [事件](../events/index.md)
