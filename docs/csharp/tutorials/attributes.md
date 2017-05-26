---
title: "屬性 | C#"
description: "了解 C# 中屬性的運作方式。"
keywords: ".NET, .NET Core, C#, 屬性"
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f03e8ac38bc0f3b0d527c0cdcb5f01b40bbb9682
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---

# <a name="using-attributes-in-c"></a>在 C 中使用屬性# #

屬性提供以宣告方式將資訊與程式碼相關聯的方法。 它們也可提供可重複使用的元素，以套用至各種不同的目標。

以 `[Obsolete]` 屬性為例。 它可以套用至類別、結構、方法及建構函式等。 它_宣告_元素已過時。 然後是由 C# 編譯器來尋找此屬性，並執行一些動作做為回應。

在本教學課程中，將介紹如何將屬性加入您的程式碼、如何建立及使用您自己的屬性，以及如何使用一些內建到 .NET Core 的屬性。

## <a name="prerequisites"></a>必要條件
您必須設定電腦以執行 .NET Core。 您可以在 [.NET Core (英文)](https://www.microsoft.com/net/core) 頁面找到安裝指示。
您可以在 Windows、Ubuntu Linux、macOS 或是 Docker 容器中執行此應用程式。 您將必須安裝慣用的程式碼編輯器。 以下說明使用 [Visual Studio Code (英文)](https://code.visualstudio.com/)，這是開放原始碼的跨平台編輯器。 不過，您可以使用您熟悉的任何工具。

## <a name="create-the-application"></a>建立應用程式

現在您已安裝完所有工具，請建立新的 .NET Core 應用程式。 若要使用命令列產生器，請在您慣用的殼層中執行下列命令︰

`dotnet new console`

此命令會建立最基本的 .NET Core 專案檔案。 您將必須執行 `dotnet restore` 以還原編譯此專案所需的相依性。

若要執行這個程式，請使用 `dotnet run`。 您應該會在主控台看到 "Hello, World" 輸出。

## <a name="how-to-add-attributes-to-code"></a>如何將屬性加入至程式碼

在 C# 中，屬性是繼承自 `Attribute` 基底類別的類別。 繼承自 `Attribute` 的任何類別都能在其他程式碼片段上做為一種「標記」。
比方說，有一種稱為 `ObsoleteAttribute` 的屬性。 這用來表示程式碼已經過時，而且不應再使用。 您可以將此屬性放在類別上，例如透過使用方括弧。

[!code-csharp[過時的屬性範例](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]  

請注意，此類別雖稱為 `ObsoleteAttribute`，但在程式碼中只需使用 `[Obsolete]`。 這是 C# 遵循的慣例。
您也可以選擇使用完整名稱 `[ObsoleteAttribute]`。

將類別標示為過時的時候，最好提供一些像是它*為什麼*過時及/或應改用*什麼*的資訊。 要這樣做，請傳遞一個字串參數到 Obsolete 屬性。

[!code-csharp[使用參數的 Obsolete 屬性範例](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

字串以引數的方式傳遞至 `ObsoleteAttribute` 建構函式，如同您撰寫 `var attr = new ObsoleteAttribute("some string")` 一般。

傳遞到屬性建構函式的參數僅限於簡單型別/常值︰`bool, int, double, string, Type, enums, etc` 和這些型別的陣列。
您不能使用運算式或變數。 您可以自由使用位置或具名參數。

## <a name="how-to-create-your-own-attribute"></a>如何建立您自己的屬性

建立屬性很簡單，只要繼承自 `Attribute` 基底類別。

[!code-csharp[建立您自己的屬性](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

之後就能在程式碼基底的其他位置使用 `[MySpecial]` (或 `[MySpecialAttribute]`) 做為屬性。

[!code-csharp[使用您自己的屬性](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

.NET 基底類別庫中的屬性 (如 `ObsoleteAttribute`) 會觸發編譯器中的特定行為。 不過，您所建立的任何屬性僅做為中繼資料，不會在執行的屬性類別內產生任何程式碼。 您可以在程式碼中的其他位置對該中繼資料採取行動 (本教學課程稍後有詳細說明)。

這裡要注意的是「陷阱」。 如上所述，使用屬性時，只有特定型別可做為引數傳遞。 不過，在建立屬性型別時，C# 編譯器不會阻止您建立這些參數。 在下列範例中，我使用編譯良好的建構函式建立了屬性。

[!code-csharp[屬性中使用的有效建構函式](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

不過，您將無法使用這個建構函式搭配屬性語法。

[!code-csharp[使用屬性建構函式的無效嘗試](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

上述程式碼會造成編譯器錯誤，例如：`Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`

## <a name="how-to-restrict-attribute-usage"></a>如何限制屬性使用方式

屬性可用在許多「目標」上。 上述範例顯示它們使用於類別，但也可以用在：

* Assembly
* 類別
* 建構函式
* 委派
* 列舉
* 事件
* 欄位
* GenericParameter
* 介面
* 方法
* 模組
* 參數
* 屬性
* ReturnValue
* 結構

當您建立屬性類別時，根據預設，C# 將允許您在任何可能的屬性目標中使用該屬性。 如果您想要將您的屬性限制在特定目標，您可以在屬性類別中使用 `AttributeUsageAttribute` 來完成。 沒錯，屬性中的屬性！

[!code-csharp[使用您自己的屬性](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

如果您嘗試將上述屬性放在類別或結構以外的項目中，就會發生如下的編譯器錯誤：`Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`

[!code-csharp[使用您自己的屬性](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a>如何使用附加至程式碼元素的屬性

屬性是做為中繼資料。 在無外力介入的情況下，它們不會實際執行任何動作。

為了尋找屬性並對其採取行動，通常需要[反射](../programming-guide/concepts/reflection.md)。 我在本教學課程中不會深入介紹「反射」，但基本概念是「反射」可讓您在 C# 中撰寫檢查其他程式碼的程式碼。

比方說，您可以使用「反射」來取得類別的相關資訊︰ 

[!code-csharp[使用反射取得型別資訊](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

該程式碼會印出類似以下的內容：`The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`

一旦您擁有 `TypeInfo` 物件 (或 `MemberInfo`、`FieldInfo` 等)，就可以使用 `GetCustomAttributes` 方法。 這會傳回 `Attribute` 物件的集合。
您也可以使用 `GetCustomAttribute` 並指定一個「屬性」型別。

以下是在 `MyClass` 的 `MemberInfo` 執行個體上使用 `GetCustomAttributes` 的範例 (我們之前已看到其中有一個 `[Obsolete]` 屬性)。

[!code-csharp[使用反射取得型別資訊](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

該命令將列印至主控台︰`Attribute on MyClass: ObsoleteAttribute`。 嘗試將其他屬性加入 `MyClass`。

務必注意的是，這些 `Attribute` 物件會延遲具現化。 也就是說，在您使用 `GetCustomAttribute` 或 `GetCustomAttributes` 之前，它們將不會具現化。
它們也會每次具現化。 在一個資料列中呼叫 `GetCustomAttributes` 兩次，將會傳回兩個不同的 `ObsoleteAttribute` 執行個體。

## <a name="common-attributes-in-the-base-class-library-bcl"></a>基底類別庫 (BCL) 中的通用屬性

許多工具和架構都會使用屬性。 NUnit 使用 NUnit 測試執行器使用的屬性 (例如 `[Test]` 和 `[TestFixture]`)。 ASP.NET MVC 使用 `[Authorize]` 之類的屬性，並提供動作篩選架構來執行關於 MVC 動作的交叉關注。 [PostSharp](https://www.postsharp.net) 使用屬性語法以允許 C# 中的層面導向程式設計。

以下是幾個值得注意的屬性，內建於 .NET Core 基底類別庫中︰

* `[Obsolete]`. 此屬性使用於上述範例中，且存在於 `System` 命名空間。 提供有關變更的程式碼基底的宣告式文件會很有用。 訊息可以字串的形式提供，使用另一個布林值參數可以從編譯器警告提升至編譯器錯誤。

* `[Conditional]`. 此屬性位於 `System.Diagnostics` 命名空間。 這個屬性可以套用至方法 (或屬性類別)。 您必須傳遞字串給建構函式。
如果該字串符合 `#define` 指示詞，C# 編譯器會移除對該方法的任何呼叫 (但非方法本身)。 這通常用於偵錯 (診斷) 用途。

* `[CallerMemberName]`. 這個屬性可以用於參數，並存在 `System.Runtime.CompilerServices` 命名空間中。 這個屬性可用來插入呼叫另一個方法之方法的名稱。 在各種 UI 架構中實作 INotifyPropertyChanged 時，這通常做為消除 'magic strings' 的方法。 範例如下：

[!code-csharp[實作 INotifyPropertyChanged 時使用 CallerMemberName](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

在上述程式碼中，您不必使用常值 `"Name"` 字串。 這有助於避免打字錯誤相關的問題，也可使重構/重新命名更順暢。

## <a name="summary"></a>總結

屬性能為 C# 提供宣告式能力。 但它們是做為中繼資料的一種程式碼，無法自行運作。

