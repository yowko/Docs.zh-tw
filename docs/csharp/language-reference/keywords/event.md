---
title: event - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: 4149663422908069b5b65ed3c32ccc6dbdfd7729
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605807"
---
# <a name="event-c-reference"></a>event (C# 參考)
`event` 關鍵字用來在發行者類別中宣告事件。  
  
## <a name="example"></a>範例  
 下例範例示範如何宣告及引發使用 <xref:System.EventHandler> 作為基礎委派類型的事件。 如需同時示範如何使用泛型 <xref:System.EventHandler%601> 委派類型，以及如何訂閱事件並建立事件處理常式方法的完整程式碼範例，請參閱[如何：發行符合 .NET Framework 方針的事件](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)。  
  
 [!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]
  
 事件是一種特殊的多點傳送委派，只能從宣告委派的類別或結構內叫用 (發行者類別)。 如果其他類別或結構訂閱了事件，當發行者類別引發事件時，就會呼叫其事件處理常式方法。 如需詳細資訊與程式碼範例，請參閱[事件](../../programming-guide/events/index.md)及[委派](../../programming-guide/delegates/index.md)。  
  
 事件可以標記為 [public](./public.md)、[private](./private.md)、[protected](./protected.md)、[internal](./internal.md)、[protected internal](./protected-internal.md) 或 [private protected](./private-protected.md)。 這些存取修飾詞定義類別使用者如何存取事件。 如需詳細資訊，請參閱[存取修飾詞](../../programming-guide/classes-and-structs/access-modifiers.md)。  
  
## <a name="keywords-and-events"></a>關鍵字和事件  
 下列關鍵字適用於事件。  
  
|關鍵字|說明|如需詳細資訊|  
|-------------|-----------------|--------------------------|  
|[static](./static.md)|隨時向呼叫端提供事件，即使沒有任何類別執行個體存在。|[靜態類別和靜態類別成員](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[virtual](./virtual.md)|允許衍生類別使用 [override](./override.md) 關鍵字覆寫事件行為。|[繼承](../../programming-guide/classes-and-structs/inheritance.md)|  
|[sealed](./sealed.md)|指定它對衍生類別不再是虛擬。||  
|[abstract](./abstract.md)|編譯器不會產生 `add` 和 `remove` 事件存取子區塊，因此衍生類別必須提供自己的實作。||  
  
 事件可使用 [static](./static.md) 關鍵字宣告為靜態事件。 這可隨時向呼叫端提供事件，即使沒有任何類別執行個體存在。 如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。  
  
 事件可使用 [virtual](./virtual.md) 關鍵字標示為虛擬事件。 這可讓衍生類別使用 [override](./override.md) 關鍵字覆寫事件行為。 如需詳細資訊，請參閱[繼承](../../programming-guide/classes-and-structs/inheritance.md)。 事件覆寫虛擬事件也可以 [sealed](./sealed.md)，指定它對衍生類別不再是虛擬。 最後，您可以宣告事件為 [abstract](./abstract.md)，也就是編譯器不會產生 `add` 和 `remove` 事件存取子區塊。 因此，衍生類別必須提供自己的實作。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](./index.md)
- [add](./add.md)
- [remove](./remove.md)
- [修飾詞](./modifiers.md)
- [如何：組合委派 (多點傳送委派)](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
