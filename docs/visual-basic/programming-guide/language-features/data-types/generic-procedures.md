---
title: 泛型程序
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 558601f038fccdcb9b94acb7c796e2b49fb6e6f4
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059193"
---
# <a name="generic-procedures-in-visual-basic"></a>Generic Procedures in Visual Basic

*泛型*程式（也稱為*泛型方法*）是至少以一個類型參數定義的程式。 這可讓呼叫程式碼在每次呼叫程式時，將資料類型自訂為其需求。  
  
 程式並非泛型，只要是在泛型類別或泛型結構內定義。 若為泛型，除了可能採用的任何一般參數之外，此程式必須至少要有一個型別參數。 泛型類別或結構可以包含非泛型程式，而非泛型類別、結構或模組可以包含泛型程式。  
  
 泛型程式可以在其一般參數清單中使用其型別參數（如果有的話），並在其程式碼中使用它的傳回型別。  
  
## <a name="type-inference"></a>類型推斷  

 您可以呼叫泛型程式，完全不提供任何類型引數。 如果您以這種方式呼叫它，則編譯器會嘗試判斷要傳遞給程式型別引數的適當資料類型。 這稱為「 *型別推斷*」。 下列程式碼示範編譯器推斷應將型別傳遞 `String` 至型別參數的呼叫 `t` 。  
  
 [!code-vb[VbVbalrDataTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#15)]  
  
 如果編譯器無法從呼叫內容推斷類型引數，則會報告錯誤。 這類錯誤的其中一個可能原因是陣列排名不相符。 例如，假設您將一般參數定義為型別參數的陣列。 如果您呼叫泛型程式來提供不同排名的陣列 () 的維度數目，則不相符會導致型別推斷失敗。 下列程式碼示範將二維陣列傳遞至需要一維陣列的程式的呼叫。  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 您只能藉由省略所有型別引數來叫用型別推斷。 如果您提供一個類型引數，則必須提供這些引數。  
  
 只有泛型程式才支援型別推斷。 您無法在泛型類別、結構、介面或委派上叫用型別推斷。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  

 下列範例會定義泛型 `Function` 程式，以尋找陣列中的特定元素。 它會定義一個型別參數，並使用它來在參數清單中建立兩個參數。  
  
### <a name="code"></a>程式碼  

 [!code-vb[VbVbalrDataTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#14)]  
  
### <a name="comments"></a>註解  

 上述範例需要能夠與 `searchValue` 的每個專案進行比較 `searchArray` 。 為保證這種功能，它會限制型別參數 `T` 來執行 <xref:System.IComparable%601> 介面。 程式碼會使用 <xref:System.IComparable%601.CompareTo%2A> 方法，而不是 `=` 運算子，因為不保證提供的型別引數可 `T` 支援 `=` 運算子。  
  
 您可以使用下列程式碼來測試程式 `findElement` 。  
  
 [!code-vb[VbVbalrDataTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#13)]  
  
 上述呼叫會 `MsgBox` 分別顯示 "0"、"1" 和 "-1"。  
  
## <a name="see-also"></a>另請參閱

- [Generic Types in Visual Basic](generic-types.md)
- [作法：定義可以為不同資料類型提供相同功能的類別](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [作法：使用泛型類別](how-to-use-a-generic-class.md)
- [程序](../procedures/index.md)
- [程序參數和引數](../procedures/procedure-parameters-and-arguments.md)
- [Type List](../../../language-reference/statements/type-list.md)
- [參數清單](../../../language-reference/statements/parameter-list.md)
