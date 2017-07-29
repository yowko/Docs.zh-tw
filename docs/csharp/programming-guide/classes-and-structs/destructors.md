---
title: "完成項 (C# 程式設計手冊)"
ms.date: 2017-05-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
caps.latest.revision: 24
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 43bb7e6488da5eda863e7ad70b25c9bf55bebb52
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="finalizers-c-programming-guide"></a>完成項 (C# 程式設計手冊)
完成項是用來解構類別的執行個體。  
  
## <a name="remarks"></a>備註  
  
-   無法在結構中定義完成項。 它們只能與類別搭配使用。  
  
-   一個類別只能有一個完成項。  
  
-   無法繼承或多載完成項。  
  
-   無法呼叫完成項。 會自動呼叫它們。  
  
-   完成項不會接受修飾詞，也不會包含參數。  
  
 例如，下列是 `Car` 類別的完成項宣告。
  
 [!code-cs[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  

完成項也可以實作為運算式主體定義，如下列範例所示。

[!code-cs[運算式主體完成項](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 完成項會在物件的基底類別上隱含地呼叫 <xref:System.Object.Finalize%2A>。 因此，會將完成項呼叫隱含地轉譯為下列程式碼︰  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 這表示，會依最高衍生性到最低衍生性的順序，對繼承鏈結中的所有執行個體遞迴呼叫 `Finalize` 方法。  
  
> [!NOTE]
>  不應該使用空的完成項。 類別包含完成項時，會在 `Finalize` 佇列中建立一個項目。 呼叫完成項時，會叫用記憶體回收行程來處理佇列。 空的完成項只會導致不必要的效能損失。  
  
 因為這是由記憶體回收行程所決定，所以程式設計人員無法控制完成項的呼叫時機。 記憶體回收行程會檢查應用程式不再使用的物件。 如果它認為物件適合進行完成，則會呼叫完成項 (如果有的話)，並回收用來儲存物件的記憶體。 程式結束時，也會呼叫完成項。  
  
 呼叫 <xref:System.GC.Collect%2A> 可能會強制執行記憶體回收，但在大部分的情況下，這種情況可能會造成效能問題，因此應該予以避免。  
  
## <a name="using-finalizers-to-release-resources"></a>使用完成項來釋放資源  
 一般而言，C# 所需要的記憶體管理，會少於使用不以具有記憶體回收的執行階段為目標之語言進行開發所需的記憶體管理。 這是因為 .NET Framework 記憶體回收行程會隱含地管理您物件的記憶體配置和釋放。 不過，您的應用程式封裝視窗、檔案和網路連線這類未受管理資源時，應該使用完成項來釋放這些資源。 適合完成物件時，記憶體回收行程會執行物件的 `Finalize` 方法。  
  
## <a name="explicit-release-of-resources"></a>明確釋放資源  
 如果您的應用程式使用過多的外部資源，則也建議您提供一種方式，以在記憶體回收行程釋放物件之前明確釋放資源。 做法是從對物件執行必要清除的 <xref:System.IDisposable> 介面實作 `Dispose` 方法。 這可以大幅改善應用程式效能。 即使對資源使用這個明確控制，如果 `Dispose` 方法呼叫失敗，完成項還是會成為清除資源的保護措施。  
  
 如需清除資源的詳細資訊，請參閱下列主題︰  
  
-   [清除 Unmanaged 資源](../../../standard/garbage-collection/unmanaged.md)  
  
-   [實作 Dispose 方法](../../../standard/garbage-collection/implementing-dispose.md)  
  
-   [using 陳述式](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>範例  
 下列範例會建立三個產生繼承鏈結的類別。 `First` 類別是基底類別、`Second` 衍生自 `First`，而 `Third` 衍生自 `Second`。 所有這三個都有完成項。 在 `Main` 中，會建立最高衍生性類別的執行個體。 程式執行時，請注意，會依最高衍生性到最低衍生性的順序，自動呼叫這三個類別的完成項。  
  
 [!code-cs[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IDisposable>   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [記憶體回收](../../../standard/garbage-collection/index.md)

