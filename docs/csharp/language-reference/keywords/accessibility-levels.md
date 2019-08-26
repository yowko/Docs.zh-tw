---
title: 存取範圍層級 - C# 參考
ms.custom: seodec18
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 2d6605a305e5003e19f4fe1dd260746302691215
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602396"
---
# <a name="accessibility-levels-c-reference"></a>存取範圍層級 (C# 參考)

使用存取修飾詞 `public`、`protected`、`internal` 或 `private` 來指定成員的下列其中一個已宣告存取範圍層級。  
  
|已宣告存取範圍|意義|  
|----------------------------|-------------|  
|[`public`](public.md)|未限制存取。|  
|[`protected`](protected.md)|存取限於包含類別或衍生自包含類別的類型。|  
|[`internal`](internal.md)|存取限於目前組件。|  
|[`protected internal`](protected-internal.md)|存取限於目前組件或衍生自包含類別的類型。|  
|[`private`](private.md)|存取限於包含類型。|  
|[`private protected`](private-protected.md)|存取限於目前組件內包含類別或衍生自包含類別的類型。 自 C# 7.2 起可用。 |  
  
 一個成員或類型只允許一個存取修飾詞，但合併使用 `protected internal` 或 `private protected` 時除外。  
  
 命名空間上不允許存取修飾詞。 命名空間沒有存取限制。  
  
 根據發生成員宣告的內容，僅允許某些已宣告存取範圍。 如果未在成員宣告中指定任何存取修飾詞，則會使用預設存取範圍。  
  
 未巢狀於其他類型中的最上層類型，只能有 `internal` 或 `public` 存取範圍。 這些類型的預設存取範圍是 `internal`。  
  
 巢狀型別 (即其他類型的成員) 可以有下表中所指出的已宣告存取範圍。  
  
|成員|預設成員存取範圍|允許的成員已宣告存取範圍|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|None|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|None|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 巢狀型別的存取範圍取決於其[存取範圍定義域](./accessibility-domain.md)，這是由成員的已宣告存取範圍和立即包含類型的存取範圍定義域所決定。 但是，巢狀型別的存取範圍領域不能超過包含型別 (Containing Type) 的存取範圍領域。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](./index.md)
- [存取修飾詞](./access-modifiers.md)
- [存取範圍定義域](./accessibility-domain.md)
- [使用存取範圍層級的限制](./restrictions-on-using-accessibility-levels.md)
- [存取修飾詞](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
- [internal](./internal.md)
