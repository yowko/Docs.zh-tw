---
title: . 運算子 - C# 參考
ms.custom: seodec18
ms.date: 02/25/2019
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: 2661676d53deb874c5e5a90b4443b301730e09df
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836457"
---
# <a name="-operator-c-reference"></a>. operator (C# 參考)

點 (`.`) 通常是用於成員存取。

您會使用 `.` 語彙基元來存取命名空間或類型的成員，如下列範例所示：

- 使用 `.` 來存取命名空間內的巢狀命名空間，如下列 [`using` 指示詞](../keywords/using-directive.md)的範例所示：

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#NestedNamespace)]

- 使用 `.` 來形成「限定名稱」以存取命名空間內的類型，如下列程式碼所示：

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#QualifiedName)]

  使用 [`using` 指示詞](../keywords/using-directive.md)來使限定名稱的使用為選擇性。

- 使用 `.` 來存取[類型成員](../../programming-guide/classes-and-structs/index.md#members) (靜態及非靜態)，如下列程式碼所示：

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#TypeMemberAccess)]

您也可以使用 `.` 來叫用[擴充方法](../../programming-guide/classes-and-structs/extension-methods.md)。

## <a name="operator-overloadability"></a>運算子是否可多載

無法多載 `.` 運算子。

## <a name="c-language-specification"></a>C# 語言規格

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[成員存取](~/_csharplang/spec/expressions.md#member-access)一節。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 運算子](index.md)
- [?. 和 ?[] 運算子](null-conditional-operators.md)