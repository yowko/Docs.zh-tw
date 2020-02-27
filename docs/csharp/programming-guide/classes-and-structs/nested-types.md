---
title: 巢狀類型 - C# 程式設計手冊
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 12e44ccc1254424c152a238c8390f133550fa54c
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626486"
---
# <a name="nested-types-c-programming-guide"></a>巢狀類型 (C# 程式設計手冊)

在[類別](../../language-reference/keywords/class.md)、[結構](../../language-reference/builtin-types/struct.md)或[介面](../../language-reference/keywords/interface.md)中定義的型別稱為「嵌套型別」。 例如：

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

不論外部類型是類別、介面或結構，巢狀型別都會預設為[私](../../language-reference/keywords/private.md)用;它們只能從其包含類型存取。 在上述範例中，外部類型無法存取 `Nested` 類別。

您也可以指定[存取修飾詞](../../language-reference/keywords/access-modifiers.md)來定義巢狀型別的存取範圍，如下所示：

- **類別**的巢狀型別可以是 [public](../../language-reference/keywords/public.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md)、[private](../../language-reference/keywords/private.md) 或 [private protected](../../language-reference/keywords/private-protected.md)。

   不過，在 `protected`sealed 類別`protected internal`內部定義 `private protected`、[ 或 ](../../language-reference/keywords/sealed.md) 巢狀類別會產生編譯器警告 [CS0628](../../misc/cs0628.md)「在 sealed 類別中已宣告新的 protected 成員」。
  
- **struct** 的巢狀型別可以是 [public](../../language-reference/keywords/public.md)、[internal](../../language-reference/keywords/internal.md) 或 [private](../../language-reference/keywords/private.md)。

下列範例會將 `Nested` 類別設為 public：

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

巢狀型別或內部類型可存取包含類型或外部類型。 若要存取包含類型，請將它當作引數傳遞至巢狀型別的建構函式。 例如：

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

巢狀型別可以存取其包含型別可存取的所有成員。 它可存取包含型別的 private 和 protected 成員，包括任何繼承的 protected 成員。

在先前的宣告，`Nested` 類別的完整名稱為 `Container.Nested`。 這是用來建立巢狀類別新執行個體的名稱，如下所示：

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../index.md)
- [類別和結構](./index.md)
- [存取修飾詞](./access-modifiers.md)
- [建構函式](./constructors.md)
