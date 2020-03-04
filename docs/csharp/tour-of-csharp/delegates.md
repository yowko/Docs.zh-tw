---
title: C# 委派 - C# 語言教學課程
description: 了解使用 C# 委派進行的晚期繫結
ms.date: 02/27/2020
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: b1740ddc65dcb0ee8775f4cbaa8356293ea55fae
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159165"
---
# <a name="delegates"></a>委派

「委派型別」代表對方法的參考，其中含有特定參數清單與傳回型別。 委派讓您可將方法視為實體，而實體能指派給變數或當作參數來傳遞。 委派類似于在某些其他語言中找到的函式指標概念。 不同于函式指標，委派是物件導向且為型別安全。

下列範例會宣告並使用名為 `Function` 的委派型別。

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

`Function` 委派型別的執行個體可以參考任何採用 `double` 引數並傳回 `double` 值的方法。 `Apply` 方法會將指定的函式套用到 `double[]` 的元素，其中會傳回含有結果的 `double[]`。 在 `Main` 方法中，是使用 `Apply` 將三個不同的函式套用到 `double[]`。

委派可以參考靜態方法 (例如上一個範例中的 `Square` 或 `Math.Sin`)，或是參考執行個體方法 (例如上一個範例中的 `m.Multiply`)。 參考執行個體方法的委派也會參考特定的物件，而且透過委派來叫用執行個體方法時，該物件就會變成叫用中的 `this`。

您也可以使用匿名函式來建立委派，這些函式是宣告時所建立的「內嵌方法」。 匿名函式可以看見周圍方法的區域變數。 下列範例不會建立類別：

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

委派不知道或在意它所參考之方法的類別;重點在於，參考的方法具有與委派相同的參數和傳回型別。

>[!div class="step-by-step"]
>[上一頁](interfaces.md)
>[下一頁](attributes.md)
