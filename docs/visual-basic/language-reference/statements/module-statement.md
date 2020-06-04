---
title: Module 陳述式
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 24a27ba41f5ac889f2f2725a2852368a4292a6fb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404446"
---
# <a name="module-statement"></a>Module 陳述式

宣告模組的名稱，並引進模組所組成之變數、屬性、事件和程式的定義。

## <a name="syntax"></a>語法

```vb
[ <attributelist> ] [ accessmodifier ]  Module name
    [ statements ]
End Module
```

## <a name="parts"></a>組件

`attributelist`  
選擇性。 請參閱[屬性清單](attribute-list.md)。

`accessmodifier`  
選擇性。 可以是下列其中一項：

- [公開](../modifiers/public.md)

- [給](../modifiers/friend.md)

請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。

`name`  
必要。 此模組的名稱。 請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。

`statements`  
選擇性。 定義此模組之變數、屬性、事件、程式和巢狀型別的語句。

`End Module`  
結束 `Module` 定義。

## <a name="remarks"></a>備註

`Module`語句會定義其命名空間中可用的參考型別。 *模組*（有時稱為*標準模組*）類似于類別，但有一些重要的區別。 每個模組只有一個實例，不需要建立或指派給變數。 模組不支援繼承或執行介面。 請注意，模組不是類別或結構所用的*型*別，您無法宣告程式設計專案來擁有模組的資料型別。

您 `Module` 只能在命名空間層級上使用。 這表示模組的宣告*內容*必須是原始程式檔或命名空間，而且不能是類別、結構、模組、介面、程式或區塊。 您不能將模組放在另一個模組中，或在任何類型內。 如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。

模組與您的程式具有相同的存留期。 因為其成員都是 `Shared` ，所以其存留期也會等於程式的存留期間。

模組預設為[Friend](../modifiers/friend.md)存取。 您可以使用存取修飾詞來調整其存取層級。 如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。

模組的所有成員都是隱含的 `Shared` 。

## <a name="classes-and-modules"></a>類別和模組

這些元素有許多相似之處，但也有一些重要的差異。

- **庫.** 舊版的 Visual Basic 會辨識兩種類型的模組：*類別模組*（cls 檔）和*標準模組*（bas 檔案）。 目前的版本會分別呼叫這些*類別*和*模組*。

- **共用成員。** 您可以控制類別的成員是否為共用或實例成員。

- **物件方向。** 類別是物件導向，但模組則不是。 因此，只有類別可以具現化為物件。 如需詳細資訊，請參閱[物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)。

## <a name="rules"></a>規則

- **修改.** 所有模組成員都是隱含[共用](../modifiers/shared.md)的。 您不能在宣告 `Shared` 成員時使用關鍵字，而且也不能改變任何成員的共用狀態。

- **繼承性.** 模組無法繼承自所有模組所繼承之以外的任何類型 <xref:System.Object> 。 特別是一個模組無法繼承自另一個模組。

  您不能在模組定義中使用[Inherits 語句](inherits-statement.md)，即使指定了亦然 <xref:System.Object> 。

- **Default 屬性。** 您不能在模組中定義任何預設屬性。 如需詳細資訊，請參閱[Default](../modifiers/default.md)。

## <a name="behavior"></a>行為

- **存取層級。** 在模組中，您可以使用自己的存取層級來宣告每個成員。 模組成員預設為[公用](../modifiers/public.md)存取，但變數和常數除外，預設為[私](../modifiers/private.md)用存取。 當模組的存取權高於其中一個成員時，會優先使用指定的模組存取層級。

- **範圍.** 模組在整個命名空間的範圍內。

  每個模組成員的範圍都是整個模組。 請注意，所有成員都會經歷*型別提升*，使其範圍升級為包含模組的命名空間。 如需詳細資訊，請參閱[型別提升](../../programming-guide/language-features/declared-elements/type-promotion.md)。

- **加.** 專案中可以有多個模組，而且可以在兩個或多個模組中宣告具有相同名稱的成員。 不過，如果參考來自于該模組之外，則您必須使用適當的模組名稱來限定這類成員的任何參考。 如需詳細資訊，請參閱 [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)。

## <a name="example"></a>範例

[!code-vb[VbVbalrStatements#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#69)]

## <a name="see-also"></a>另請參閱

- [Class 陳述式](class-statement.md)
- [Namespace 陳述式](namespace-statement.md)
- [Structure 陳述式](structure-statement.md)
- [Interface 陳述式](interface-statement.md)
- [Property Statement](property-statement.md)
- [型別提升](../../programming-guide/language-features/declared-elements/type-promotion.md)
