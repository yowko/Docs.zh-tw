---
title: 類型 '<typename>' 上的 'For Each'模稜兩可，因為該類型實作了 'System.Collections.Generic.IEnumerable(Of T)' 的多個執行個體化
ms.date: 07/20/2015
f1_keywords:
- vbc32096
- bc32096
helpviewer_keywords:
- BC32096
ms.assetid: ed20d09c-913f-482e-89f8-c0a596c3ec24
ms.openlocfilehash: 0f19836efeabcf1d9e5097667c719c1f7d99cbbb
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163463"
---
# <a name="bc32096-for-each-on-type-typename-is-ambiguous-because-the-type-implements-multiple-instantiations-of-systemcollectionsgenericienumerableof-t"></a>類型 ' ' 上的 BC32096： ' For Each ' \<typename> 不明確，因為類型會實 (T) ' 的多重具現化

`For Each`語句會指定具有一個以上方法的 iterator 變數 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 。

 反覆運算器變數的型別必須是在 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> .NET Framework 其中一個命名空間中的或介面 `Collections` 。 類別可以針對每個結構使用不同的型別引數，來執行一個以上的結構化泛型介面。 如果執行此程式的類別用於反覆運算器變數，該變數就會有一個以上的 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 方法。 在這種情況下，Visual Basic 無法選擇要呼叫的方法。

 **錯誤識別碼：** BC32096

## <a name="to-correct-this-error"></a>更正這個錯誤

- 使用 [DirectCast 運算子](../operators/directcast-operator.md) 或 [TryCast 運算子](../operators/trycast-operator.md) ，將反覆運算器變數型別轉換為定義 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 您想要使用之方法的介面。

## <a name="see-also"></a>另請參閱

- [For Each...Next 陳述式](../statements/for-each-next-statement.md)
- [介面](../../programming-guide/language-features/interfaces/index.md)
