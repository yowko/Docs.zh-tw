---
title: 完成項 - C# 程式設計手冊
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 62fc531a8064a8a5cb144a89aa9975b3199db976
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990117"
---
# <a name="finalizers-c-programming-guide"></a>完成項 (C# 程式設計手冊)
完成項 (也稱為**解構函式**) 可在記憶體回收行程收集類別執行個體時，用來執行任何必要的最後清除。  
  
## <a name="remarks"></a>備註  
  
- 無法在結構中定義完成項。 它們只能與類別搭配使用。  
  
- 一個類別只能有一個完成項。  
  
- 無法繼承或多載完成項。  
  
- 無法呼叫完成項。 會自動呼叫它們。  
  
- 完成項不會接受修飾詞，也不會包含參數。  
  
 例如，下列是 `Car` 類別的完成項宣告。
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

完成項也可以實作為運算式主體定義，如下列範例所示。

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
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
  
 這項設計表示 `Finalize` 會針對繼承鏈中的所有實例，以遞迴方式呼叫方法，從最常衍生到最低衍生的。  
  
> [!NOTE]
> 不應該使用空的完成項。 類別包含完成項時，會在 `Finalize` 佇列中建立一個項目。 呼叫完成項時，會叫用記憶體回收行程來處理佇列。 空的完成項只會導致不必要的效能損失。  
  
 程式設計人員無法控制何時呼叫完成項;垃圾收集行程會決定何時呼叫它。 記憶體回收行程會檢查應用程式不再使用的物件。 如果它認為物件適合進行完成，則會呼叫完成項 (如果有的話)，並回收用來儲存物件的記憶體。

 在 .NET Framework 應用程式 (而非 .NET Core 應用程式) 中，程式結束時也會呼叫完成項。
  
 您可以藉由呼叫來強制進行垃圾收集 <xref:System.GC.Collect%2A> ，但大部分的情況下，應該避免此呼叫，因為它可能會造成效能問題。  
  
## <a name="using-finalizers-to-release-resources"></a>使用完成項來釋放資源  
 一般而言，c # 不需要在開發人員的部分記憶體管理，做為不是以垃圾收集的執行時間為目標的語言。 這是因為 .NET 垃圾收集行程會隱含地管理物件的記憶體配置和釋放。 不過，當您的應用程式封裝非受控資源（例如 windows、檔案和網路連接）時，您應該使用完成項來釋放這些資源。 適合完成物件時，記憶體回收行程會執行物件的 `Finalize` 方法。
  
## <a name="explicit-release-of-resources"></a>明確釋放資源  
 如果您的應用程式使用過多的外部資源，則也建議您提供一種方式，以在記憶體回收行程釋放物件之前明確釋放資源。 若要釋出資源，請 `Dispose` 從介面中 <xref:System.IDisposable> 執行方法，以對物件執行必要的清除。 這可以大幅改善應用程式效能。 即使對資源進行這項明確的控制，如果方法呼叫失敗，完成項還是會成為清除資源的保護措施 `Dispose` 。  
  
 如需有關清除資源的詳細資訊，請參閱下列文章：  
  
- [清除非受控資源](../../../standard/garbage-collection/unmanaged.md)  
  
- [執行 Dispose 方法](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [using 陳述式](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a>範例  
 下列範例會建立三個產生繼承鏈結的類別。 `First` 類別是基底類別、`Second` 衍生自 `First`，而 `Third` 衍生自 `Second`。 所有這三個都有完成項。 在 `Main` 中，會建立最高衍生性類別的執行個體。 程式執行時，請注意，會依最高衍生性到最低衍生性的順序，自動呼叫這三個類別的完成項。  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a>C# 語言規格  

如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的[解構函式](~/_csharplang/spec/classes.md#destructors)一節。
  
## <a name="see-also"></a>另請參閱

- <xref:System.IDisposable>
- [C # 程式設計指南](../index.md)
- [建構函式](./constructors.md)
- [記憶體回收](../../../standard/garbage-collection/index.md)
