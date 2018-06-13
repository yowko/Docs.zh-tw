---
title: Generic Procedures in Visual Basic
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
ms.openlocfilehash: 686087e4520ea5e6e69e5906c628af3ad54749da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649392"
---
# <a name="generic-procedures-in-visual-basic"></a>Generic Procedures in Visual Basic
A*泛型程序*，也稱為*泛型方法*，是定義了至少一個型別參數的程序。 這可讓呼叫的程式碼來調整資料類型，使其符合需求每次呼叫程序。  
  
 程序不一定是泛型只是泛型類別或一般結構內定義。 為泛型，程序必須接受至少一個型別參數，除了它可能需要的任何一般參數。 泛型類別或結構可以包含非泛型程序和非泛型類別、 結構或模組可以包含泛型程序。  
  
 泛型程序可以使用其型別參數在其一般參數清單中，如果有的話，和其程序程式碼使用傳回型別。  
  
## <a name="type-inference"></a>類型推斷  
 您可以在未提供任何型別引數在所有情況下呼叫泛型程序。 如果您用這種方式呼叫，編譯器會嘗試判斷要傳遞至程序的型別引數的適當資料類型。 這稱為*型別推斷*。 下列程式碼會示範呼叫中的編譯器推斷型別，應傳遞`String`至型別參數`t`。  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 如果編譯器無法推斷的型別引數，從呼叫的內容，則會回報錯誤。 這類錯誤的其中一個可能的原因是陣列的陣序不符。 例如，假設您將一般參數定義為型別參數的陣列。 如果您呼叫泛型程序提供的不同陣序 （維度數目），陣列不相符會導致類型推斷失敗。 下列程式碼會示範呼叫在二維陣列傳遞至需要的一維陣列的程序。  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 您可以只是藉由略過所有型別引數叫用型別推斷。 如果您提供一個型別引數時，您必須將它們全部提供。  
  
 僅適用於泛型程序支援的類型推斷。 您無法叫用泛型類別、 結構、 介面或委派的型別的推斷。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例會定義泛型`Function`尋找特定的項目陣列中的程序。 它會定義一個型別參數，並使用它來建構參數清單中的兩個參數。  
  
### <a name="code"></a>程式碼  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a>註解  
 上述範例必須能夠比較`searchValue`針對每個項目`searchArray`。 若要確保這項功能，它會限制型別參數`T`實作<xref:System.IComparable%601>介面。 程式碼會使用<xref:System.IComparable%601.CompareTo%2A>方法，而非`=`運算子，因為型別引數提供給不保證`T`支援`=`運算子。  
  
 您可以測試`findElement`為下列程式碼的程序。  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 上述呼叫`MsgBox`分別顯示"0"、"1"和"-1"。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 中的泛型型別](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [如何：定義可以在不同資料類型上提供完全相同功能的類別](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [如何：使用泛型類別](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [程序](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [程序參數和引數](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [類型清單](../../../../visual-basic/language-reference/statements/type-list.md)  
 [參數清單](../../../../visual-basic/language-reference/statements/parameter-list.md)
