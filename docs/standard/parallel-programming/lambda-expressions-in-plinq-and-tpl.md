---
title: PLINQ 和 TPL 中的 Lambda 運算式
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
ms.openlocfilehash: 469c164630e1dab84b3d54c16c43d031ebf560ed
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063766"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>PLINQ 和 TPL 中的 Lambda 運算式

工作平行程式庫 (TPL) 包含了許多會採用其中一個委派的 <xref:System.Func%601?displayProperty=nameWithType> 或 <xref:System.Action?displayProperty=nameWithType> 系列作為輸入參數的方法。 您可以使用這些委派將您自訂的程式邏輯傳遞到平行迴圈、工作或查詢中。 TPL 以及 PLINQ 的程式碼範例會使用 lambda 運算式來建立這些委派的執行個體，以作為內嵌程式碼區塊。 本主題將簡單介紹 Func 與 Action，並說明如何在工作平行程式庫和 PLINQ 中使用 lambda 運算式。

> [!NOTE]
> 如需有關委派的一般詳細資訊，請參閱[委派](../../csharp/programming-guide/delegates/index.md)和[委派](../../visual-basic/programming-guide/language-features/delegates/index.md)。 如需 C# 和 Visual Basic 中之 lambda 運算式的詳細資訊，請參閱 [Lambda 運算式](../../csharp/language-reference/operators/lambda-expressions.md)和 [Lambda 運算式](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。

## <a name="func-delegate"></a>Func 委派

`Func` 委派所封裝的方法會傳回值。 在簽章中 `Func` ，最後一個或最右邊的型別參數一律會指定傳回型別。 其中一個常見的編譯器錯誤原因是嘗試將兩個輸入參數傳入 <xref:System.Func%602?displayProperty=nameWithType>；事實上，此型別只會採用一個輸入參數。 .Net 會定義17版的 `Func` ： <xref:System.Func%601?displayProperty=nameWithType> 、 <xref:System.Func%602?displayProperty=nameWithType> 、 <xref:System.Func%603?displayProperty=nameWithType> ，依此類推 <xref:System.Func%6017?displayProperty=nameWithType> 。

## <a name="action-delegate"></a>Action 委派

<xref:System.Action?displayProperty=nameWithType>委派會將方法封裝 (不會傳回值之 Visual Basic) 中的 Sub。 在型別簽章中 `Action` ，型別參數只代表輸入參數。 如同 `Func` ，.net 定義了17版的 `Action` ，從沒有型別參數的版本，一直到具有16個型別參數的版本。

## <a name="example"></a>範例

下列 <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> 方法的範例顯示如何透過使用 Lambda 運算式來表達 Func 與 Action 委派。

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a>另請參閱

- [平行程式設計](index.md)
