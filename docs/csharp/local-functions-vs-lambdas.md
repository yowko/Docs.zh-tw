---
title: "區域函式與 Lambda 運算式的比較"
description: "區域函式可能比 Lambda 運算式更適用的原因"
keywords: "C#, .NET, .NET Core, 最新功能, 新功能, 區域函式, Lambda 運算式"
author: BillWagner
ms.author: wiwagn
ms.date: 10/27/2016
ms.topic: article
ms.prod: visual-studio-dev-15
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 368d1752-3659-489a-97b4-f15d87e49ae3
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4b2fdc86a3b2485f6177112a584291558fb76984
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---

### <a name="local-functions-compared-to-lambda-expressions"></a>區域函式與 Lambda 運算式的比較

在某些使用案例中，您可以建立並使用 Lambda 運算式，而不需要建立區域函式。 以下是採取上述做法的非同步方法範例：

[!code-csharp[TaskLambdaExample](../../samples/snippets/csharp/new-in-7/AsyncWork.cs#36_TaskLambdaExample "使用 Lambda 運算式傳回方法的工作")]

雖然如此，仍然有許多建議使用區域函式，而不建議定義和呼叫 Lambda 運算式的原因。

首先，使用 Lambda 運算式時，編譯器必須建立匿名類別和該類別的執行個體，以存放由 closure 擷取的任何變數。 此 Lambda 運算式的 closure 包含 `address`、`index` 和 `name` 變數。 

第二，Lambda 運算式是由具現化委派並叫用該委派的方式所實作。 區域函式則是以方法呼叫的形式來實作。
Lambda 運算式所需的具現化代表額外的記憶體配置，這可能會在具時效性的程式碼路徑中成為影響效能的因素。
區域函式不會造成這項額外負荷。

第三，您可在定義區域函式之前，即進行呼叫。 Lambda 運算式則必須在定義之前，先進行宣告。 這表示在遞迴演算法中可以更輕鬆地使用區域函式：

[!code-csharp[LocalFunctionFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#37_LocalFunctionFactorial "使用區域函式的遞迴階乘")]

針對使用 Lambda 運算式的實作版本進行對比：

[!code-csharp[26_LambdaFactorial](../../samples/snippets/csharp/new-in-7/MathUtilities.cs#38_LambdaFactorial "使用 Lambda 運算式的遞迴階乘")]

請注意，若為使用 Lambda 運算式的版本，則必須在定義 Lambda 運算式 `nthFactorial` 之前，將其宣告和初始化。 如果沒有這麼做的話，系統會在指派 `nthFactorial` 之前就加以參考，而導致編譯時期錯誤。
使用區域函式時，您可以更輕鬆地建立遞迴演算法。 

雖然區域函式與 Lambda 運算式看似相同，但它們實際上有不同的用途與用法。
如果您要撰寫的函式只會從其他方法的內容進行呼叫時，使用區域函式會更有效率。


