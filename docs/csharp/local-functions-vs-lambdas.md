---
title: "區域函式與 Lambda 運算式的比較"
description: "了解區域函式可能比 Lambda 運算式更適用的原因。"
keywords: "C#, .NET, .NET Core, 最新功能, 新功能, 區域函式, Lambda 運算式"
author: BillWagner
ms.author: wiwagn
ms.date: 06/27/2016
ms.topic: article
ms.prod: visual-studio-dev-15
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.translationtype: HT
ms.sourcegitcommit: 4582cb0ee091526423cce3fc1d8243029f34f59c
ms.openlocfilehash: 366d7465433f2786960e22418b8aa46ba10e1fd1
ms.contentlocale: zh-tw
ms.lasthandoff: 08/16/2017

---

### <a name="local-functions-compared-to-lambda-expressions"></a>區域函式與 Lambda 運算式的比較

第一眼，[區域函式](programming-guide/classes-and-structs/local-functions.md)和 [Lambda 運算式](lambda-expressions.md)十分類似。
根據您的需求，區域函式可能是較好且更簡單的方案。

讓我們檢查階乘演算法的區域函式與 Lambda 運算式實作差異。 首先是使用區域函式的版本：

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "使用區域函式的遞迴階乘")]

針對使用 Lambda 運算式的實作版本進行對比：

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "使用 Lambda 運算式的遞迴階乘")]

首先，Lambda 運算式是由具現化委派並叫用該委派的方式所實作。 區域函式則是以方法呼叫的形式來實作。
Lambda 運算式所需的具現化代表額外的記憶體配置，這可能會在具時效性的程式碼路徑中成為影響效能的因素。
區域函式不會造成這項額外負荷。 在上述範例中，區域函式版本會比 Lambda 運算式版本少 2 個配置。

區域函式會實作為具有編譯器產生名稱的私用方法，因此這個遞迴方法就已足夠。 與其他私用方法的唯一差異在於它位於外部函式的語意範圍內。

第二，您可以在定義區域函式之前，即進行呼叫。 Lambda 運算式則必須在定義之前，先進行宣告。 這表示在遞迴演算法中可以更輕鬆地使用區域函式，如上所示。

請注意，若為使用 Lambda 運算式的版本，則必須在定義 Lambda 運算式 `nthFactorial` 之前，將其宣告和初始化。 如果沒有這麼做的話，系統會在指派 `nthFactorial` 之前就加以參考，而導致編譯時期錯誤。
使用區域函式時，您可以更輕鬆地建立遞迴演算法。

第三，使用 Lambda 運算式時，編譯器必須一律建立匿名類別和該類別的執行個體，以儲存由關閉擷取的任何變數。 請考慮使用以下非同步範例：

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "使用 Lambda 運算式傳回方法的工作")]

此 Lambda 運算式的 closure 包含 `address`、`index` 和 `name` 變數。 如果是區域函式，實作關閉的物件可以是 `struct` 類型。 這就不需要配置。

> [!NOTE]
> 這個方法的對等區域函式也會使用關閉的類別。 不論區域函式的關閉實作為 `class` 還是 `struct` 都是實作詳細資料。 區域函式可以使用 `struct`，而 Lambda 一律會使用 `class`。

[!code-csharp[TaskLocalFunctionExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "工作傳回方法與區域函式")]

此範例中未示範的最後一個優點，在於可以使用 `yield return` 語法來產生一連串的值，以將區域函式實作為迭代器。

雖然區域函式與 Lambda 運算式看似相同，但它們實際上有不同的用途與用法。
如果您要撰寫的函式只會從其他方法的內容進行呼叫時，使用區域函式會更有效率。

