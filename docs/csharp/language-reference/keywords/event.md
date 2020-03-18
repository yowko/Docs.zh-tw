---
title: event - C# 參考
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: eb1805ed55921497fea88e6b39989c876ef003d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713563"
---
# <a name="event-c-reference"></a>事件（C# 引用）

`event` 關鍵字用來在發行者類別中宣告事件。

## <a name="example"></a>範例

下例範例示範如何宣告及引發使用 <xref:System.EventHandler> 作為基礎委派類型的事件。 有關演示如何使用泛型<xref:System.EventHandler%601>委託類型以及如何訂閱事件和創建事件處理常式方法的完整代碼示例，請參閱[如何發佈符合 .NET 框架準則的事件](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)。

[!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]

事件是一種特殊的多點傳送委派，只能從宣告委派的類別或結構內叫用 (發行者類別)。 如果其他類別或結構訂閱了事件，當發行者類別引發事件時，就會呼叫其事件處理常式方法。 如需詳細資訊與程式碼範例，請參閱[事件](../../programming-guide/events/index.md)及[委派](../../programming-guide/delegates/index.md)。

事件可以標記為[公共](./public.md)、[私有](./private.md)、[受保護](./protected.md)、[內部](./internal.md)、[受保護的內部](./protected-internal.md)或[私有保護](./private-protected.md)。 這些存取修飾詞定義類別使用者如何存取事件。 如需詳細資訊，請參閱[存取修飾詞](../../programming-guide/classes-and-structs/access-modifiers.md)。

## <a name="keywords-and-events"></a>關鍵字和事件

下列關鍵字適用於事件。

|關鍵字|描述|取得詳細資訊|
|-------------|-----------------|--------------------------|
|[靜態](./static.md)|隨時向呼叫端提供事件，即使沒有任何類別執行個體存在。|[靜態類別和靜態類別成員](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|
|[虛擬](./virtual.md)|允許衍生類別使用 [override](./override.md) 關鍵字覆寫事件行為。|[繼承](../../programming-guide/classes-and-structs/inheritance.md)|
|[密封](./sealed.md)|指定它對衍生類別不再是虛擬。||
|[抽象](./abstract.md)|編譯器不會產生 `add` 和 `remove` 事件存取子區塊，因此衍生類別必須提供自己的實作。||

事件可使用 [static](./static.md) 關鍵字宣告為靜態事件。 這可隨時向呼叫端提供事件，即使沒有任何類別執行個體存在。 有關詳細資訊，請參閱[靜態類和靜態類成員](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。

事件可使用 [virtual](./virtual.md) 關鍵字標示為虛擬事件。 這可讓衍生類別使用 [override](./override.md) 關鍵字覆寫事件行為。 如需詳細資訊，請參閱[繼承](../../programming-guide/classes-and-structs/inheritance.md)。 事件覆寫虛擬事件也可以 [sealed](./sealed.md)，指定它對衍生類別不再是虛擬。 最後，您可以宣告事件為 [abstract](./abstract.md)，也就是編譯器不會產生 `add` 和 `remove` 事件存取子區塊。 因此，衍生類別必須提供自己的實作。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](./index.md)
- [新增](./add.md)
- [移除](./remove.md)
- [修飾詞](index.md)
- [如何組合委託（多播代表）](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
