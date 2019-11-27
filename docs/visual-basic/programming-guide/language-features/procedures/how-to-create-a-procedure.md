---
title: 如何：建立程序
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: a831814c18f97991fca8067f1c9c8e491da1b665
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344915"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>如何：建立程序 (Visual Basic)

您可以將程式括在起始宣告語句（`Sub` 或 `Function`）與結束宣告語句（`End Sub` 或 `End Function`）之間。 所有程式的程式碼都位於這些語句之間。

 程式不能包含另一個程式，因此它的開始和結束語句必須在任何其他程式之外。

 如果您的程式碼在不同的位置執行相同的工作，您可以撰寫一次工作，然後從程式碼中的不同位置呼叫它。

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>若要建立不會傳回值的程式

1. 在任何其他程式之外，請使用 `Sub` 語句，後面接著 `End Sub` 語句。

2. 在 `Sub` 語句中，在 `Sub` 關鍵字後面加上程式的名稱，然後以括弧括住參數清單。

3. 將程式的程式碼語句放在 `Sub` 和 `End Sub` 語句之間。

### <a name="to-create-a-procedure-that-returns-a-value"></a>若要建立會傳回值的程式

1. 在任何其他程式之外，請使用 `Function` 語句，後面接著 `End Function` 語句。

2. 在 `Function` 語句中，請在 `Function` 關鍵字後面加上程式的名稱，然後以括弧括住參數清單，然後再指定傳回值的資料類型 `As` 子句。

3. 將程式的程式碼語句放在 `Function` 和 `End Function` 語句之間。

4. 使用 `Return` 語句，將值傳回給呼叫程式碼。

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>將您的新程式與舊的重複程式碼區塊連接

1. 請務必將新程式定義在舊程式碼有權存取的位置。

2. 在舊的重複程式碼區塊中，以呼叫 `Sub` 或 `Function` 程式的單一語句取代執行重複性工作的語句。

3. 如果您的程式是會傳回值的 `Function`，請確定您的呼叫語句會執行具有傳回值的動作，例如將它儲存在變數中，否則值會遺失。

## <a name="example"></a>範例

 下列 `Function` 程式會計算直角三角形的最長邊（或斜邊），並指定其他兩邊的值：

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a>請參閱

- [程序](index.md)
- [Sub 程序](sub-procedures.md)
- [函式程序](function-procedures.md)
- [屬性程序](property-procedures.md)
- [運算子程序](operator-procedures.md)
- [程序參數和引數](procedure-parameters-and-arguments.md)
- [遞迴程序](recursive-procedures.md)
- [程序多載化](procedure-overloading.md)
- [物件和類別](../objects-and-classes/index.md)
- [物件導向程式設計 (Visual Basic)](../../concepts/object-oriented-programming.md)
