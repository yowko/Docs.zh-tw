---
title: ".NET 教學課程"
description: ".NET 平台某些重要功能的逐步導覽。"
keywords: ".NET, .NET Core, 教學課程, 程式設計語言, 不安全, 記憶體管理, 型別安全, 非同步處理"
author: cartermp
manager: wpickett
ms.author: phcart
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
translationtype: Human Translation
ms.sourcegitcommit: 2c57b5cebd63b1d94b127cd269e3b319fb24dd97
ms.openlocfilehash: 02e2fa22e36fd2f6618527ad3c89cbbd8587dfe2

---

# <a name="tour-of-net"></a>.NET 教學課程

.NET 是一般用途開發平台。  它有數種重要功能，例如多種程式設計語言、非同步和並行程式設計模型，以及原生互通性，可支援跨多重平台的眾多案例。

此文章提供 .NET 平台某些重要功能的逐步導覽。

請參閱 [.NET 架構元件](components.md)以了解 .NET 的每個架構「片段」，以及其用途。

## <a name="how-to-run-the-code-samples"></a>如何執行程式碼範例

若要了解如何設定開發環境以執行程式碼範例，請參閱[入門](getting-started.md)。  您可以從此頁面將程式碼複製並貼入您的環境中來執行它們。 

> [!NOTE]
在未來，此文件網站將能在您的瀏覽器中執行這些程式碼範例。

## <a name="programming-languages"></a>程式語言

.NET 支援多種程式設計語言。  .NET 執行階段實作[通用語言基礎結構 (CLI)](https://www.visualstudio.com/en-us/mt639507)，它的其中一個功能是指定與語言無關的執行階段和語言互通性。  這表示您可以選擇任何 .NET 語言，在 .NET 上建置 App 與服務。

Microsoft 積極地開發並支援三種 .NET 語言：C#、F# 與 Visual Basic .NET。 

* C# 很簡單、強大、型別安全且物件導向，同時保留 C 樣式語言的易讀性與簡潔性。 熟悉 C 和類似語言的任何人在適應 C# 方面很少有問題。  若要深入了解 C#，請參閱 [C# 指南](../csharp/index.md)。

* F# 是跨平台、功能優先的程式語言，也支援傳統物件導向和命令式程式設計。  若要深入了解 F#，請參閱 [F# 指南](../fsharp/index.md)。

* Visual Basic 是容易學習的語言，您可以使用該語言建置 .NET 上所執行的各種應用程式。

## <a name="automatic-memory-management"></a>自動記憶體管理

.NET 使用[記憶體回收](garbagecollection/index.md)為程式提供自動記憶體管理。  GC 採用 lazy 方法來管理記憶體，優先考慮應用程式輸送量，而不是立即收集記憶體。  若要深入了解 .NET GC，請參閱[記憶體回收 (GC) 的基本概念](garbagecollection/fundamentals.md)。

下列兩行會配置記憶體：

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

沒有類似的關鍵字可取消配置記憶體，因為當記憶體回收行程透過其排程執行回收記憶體時，就會自動取消配置。

指定範圍內的類型通常會在方法完成之後移出範圍，此時可加以收集。 不過，您可以在方法結束之前，使用 `using` 陳述式對 GC 指出特定物件超出範圍：

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

`using` 區塊完成之後，GC 就會知道先前範例中的 `stream` 物件可加以收集，並回收其記憶體。

此規則在 F# 中的語意稍有不同。  若要深入了解 F# 中的資源管理，請參閱[資源管理：`use` 關鍵字](../fsharp/language-reference/resource-management-the-use-keyword.md)

記憶體回收行程會啟用一項較不明顯、但具有深遠影響的功能，那就是記憶體安全。 確保記憶體永遠安全並不困難︰如果程式只存取已配置的記憶體 (而不是釋放的記憶體)，就是記憶體安全。 懸置的指標一律是錯誤，而追蹤其來源通常很困難。

.NET 執行階段提供其他服務，來達成記憶體安全的承諾 (GC 原本並未提供)。 它可確保程式不會從陣列結尾編製索引，也不會從物件結尾取出虛設項目欄位。

下列範例會擲回例外狀況，以作為記憶體安全的結果。

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="type-safety"></a>型別安全

物件會依照類型配置。 物件的類型會決定該物件所允許的唯一作業，以及所使用的記憶體。 `Dog` 類型可能會有 `Jump` 和 `WagTail` 方法，但不太可能會有 `SumTotal` 方法。 程式只能呼叫指定類型的宣告方法。 所有其他呼叫會導致編譯時期錯誤，或執行階段例外狀況 (如果使用動態功能或 `object`)。

.NET 語言是物件導向，具有基底和衍生類別的階層架構。 .NET 執行階段只允許符合物件階層架構的的物件轉換和呼叫。 請記住，以任何 .NET 語言所定義的每種類型都是衍生自基底 `object` 類型。

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L18-L23)]

此外也會使用型別安全，藉由確保存取子關鍵字的精確度，來協助強制執行封裝。 存取子關鍵字是控制其他程式碼存取指定類型成員的成品。 這些關鍵字通常會用於某種類型中用來管理其行為的各種資料。

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#、Visual Basic 與 F# 支援本機**型別推斷**。 型別推斷表示編譯器會從右邊的運算式推算左邊的運算式類型。 這並不會破壞或規避型別安全。 產生的類型**具有**強類型，其中包含其所指的所有項目。 讓我們重寫上一個範例中的前兩行，以引入型別推斷。 請注意，此範例的其餘部分完全相同。

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F# 提供比 C# 和 Visual Basic 中的方法內部型別推斷更進步的型別推斷功能。  若要深入了解，請參閱[型別推斷](../fsharp/language-reference/type-inference.md)。

## <a name="delegates-and-lambdas"></a>委派和 Lambda

委派與 C++ 函式指標類似，主要的差別在於委派是型別安全。 委派是 CLR 型別系統中一種已中斷連線的方法。 一般方法是附加到類別，並且只能透過靜態或執行個體呼叫慣例來直接呼叫。

委派可用於 .NET 世界中各種不同的 API 和位置，尤其是透過 Lambda 運算式，這是 LINQ 的基石。

如需詳細資訊，請參閱[委派和 Lambda](delegates-lambdas.md) 文件。

## <a name="generics"></a>泛型

泛型是 .NET Framework 2.0 中新增的功能。 簡單來說，泛型可讓程式設計師在設計其類別時引入「型別參數」，如此即可讓用戶端程式碼 (型別的使用者) 指定正確型別來取代型別參數。

新增泛型功能是為了協助程式設計師實作泛型資料結構。 在此功能之前，若要讓 `List` 型別成為泛型，您必須使用 `object` 類型的元素。 這樣做會有各種效能及語意問題，更別提可能會有難以解決的執行階段錯誤。 後者最糟的情況是當資料結構同時包含整數與字串時，而且會在使用清單的成員時擲回 `InvalidCastException`。

下列範例顯示使用 @System.Collections.Generic.List%601 型別執行個體的基本程式正在執行。

[!code-csharp[GenericsShort](../../samples/csharp/snippets/tour/GenericsShort.csx)]

如需詳細資訊，請參閱[泛型型別 (泛型) 概觀](generics.md)一文。

## <a name="async-programming"></a>非同步程式設計

非同步程式設計是 .NET 中的最高階概念，包括執行階段、Framework 程式庫和 .NET 語言建構的非同步支援。 就內部而言，它們是以物件 (例如 `Task`) 為基礎，可利用作業系統盡可能有效率地執行 I/O-bound 工作。

若要深入了解 .NET 非同步程式設計，請從[非同步概觀](async.md)開始。

## <a name="language-integrated-query-linq"></a>Language Integrated Query (LINQ)

LINQ 是一組強大的 C# 和 VB 功能，可讓您撰寫簡單的宣告式程式碼來操作資料。 資料可以是許多形式 (例如 SQL 資料庫中的記憶體內部物件或 XML 文件)，但您通常針對每個資料來源所撰寫的 LINQ 程式碼看起來大同小異！

若要深入了解及查看一些範例，請參閱 [LINQ (Language Integrated Query)](using-linq.md)。

## <a name="native-interoperability"></a>原生互通性

目前使用的每個作業系統會針對各種程式設計工作提供許多平台支援。 .NET 提供幾種方式來使用這些 API。 整體而言，這項支援稱為「原生互通性」。在本節中，我們將探討如何從 Managed .NET 程式碼存取原生 API。

執行原生互通性的主要方式是透過「平台叫用」(簡稱 P/Invoke)。 您可以在不同的 Linux 和 Windows 平台之間使用 .NET Core 的這項支援。 另一項僅適用於 Windows 的原生互通性做法稱為 "COM Interop"，可用來處理 Managed 程式碼中的 [COM 元件](https://msdn.microsoft.com/library/bwa2bx93.aspx)。 它是以 P/Invoke 基礎結構為建置基礎，但運作方式稍有不同。

Mono (以及 Xamarin) 對 Java 和 Objective-C 的互通性支援大致上很類似；也就是說，它們使用相同的原則。

如需詳細資訊，請參閱[原生互通性](native-interop.md)文件。

## <a name="unsafe-code"></a>Unsafe 程式碼

CLR 可讓您透過 `unsafe` 程式碼存取原生記憶體及執行指標算術。 特定演算法和系統互通性需要這些作業。 Unsafe 程式碼雖然功能強大，但除非是必須與系統 API 互通，或必須實作最有效率的演算法，否則不建議使用。 Unsafe 程式碼在不同的環境中執行時可能不盡相同，而且也會失去記憶體回收行程和型別安全的好處。 建議您盡可能限制和集中使用 Unsafe 程式碼，並徹底測試該程式碼。

下列範例是 `StringBuilder` 類別的 `ToString()` 方法修改後的版本。  它說明如何使用 `unsafe` 程式碼直接四處移動記憶體區塊，以有效率地實作演算法：

[!code-csharp[Unsafe](../../samples/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>後續步驟

若您對 C# 功能的教學課程感興趣，請參閱 [C# 教學課程](../csharp/tour-of-csharp/index.md)。

若您對 F# 功能的教學課程感興趣，請參閱 [F# 教學課程](../fsharp/tour.md)。

若要開始撰寫自己的程式碼，請參閱[入門](getting-started.md)。

若要了解重要的 .NET 元件，請參閱 [.NET 架構元件](components.md)。


<!--HONumber=Nov16_HO3-->


