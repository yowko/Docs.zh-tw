---
title: "C 中的繼承#"
description: "了解如何使用 C# 程式庫和應用程式中的繼承。"
keywords: "繼承 (C#), 基底類別, 衍生類別, 抽象基底類別"
author: rpetrusha
manager: wpickett
ms.author: ronpet
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: aeb68c74-0ea0-406f-9fbe-2ce02d47ef31
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c14a2ecfa4b9c9522278098d54aad258b5feb1dc
ms.lasthandoff: 03/13/2017

---
# <a name="inheritance-in-c-and-net"></a>C# 和 .NET 中的繼承 #

## <a name="introduction"></a>簡介 ##

本教學課程將介紹 C# 中的繼承。 繼承是一種物件導向程式設計語言的功能，可讓您定義基底類別，提供特定功能 (資料和行為)，以及定義繼承或覆寫該功能的衍生類別。

## <a name="prerequisites"></a>必要條件 ##

本教學課程假設您已安裝 .NET Core。 如需安裝指示，請參閱[.NET Core 安裝指南 (英文)](https://www.microsoft.com/net/core)。 您也需要程式碼編輯器。 本教學課程使用 [Visual Studio Code (英文)](https://code.visualstudio.com)，不過您可以使用自選的任何程式碼編輯器。

## <a name="running-the-examples"></a>執行範例 ##

若要建立和執行本教學課程中的範例，請您從命令列使用 [DotNet](../../core/tools/dotnet.md) 公用程式。 每個範例都依照下列步驟執行︰

1. 建立可儲存範例的目錄。

1. 在命令提示字元處輸入 [dotnet new console](../../core/tools/dotnet-new.md) 命令，以建立新的 .NET Core 專案。

1. 將範例程式碼複製並貼到您的程式碼編輯器。

1. 從命令列輸入 [dotnet restore](../../core/tools/dotnet-restore.md)命令來載入或還原專案的相依性。

1. 輸入 [dotnet run](../../core/tools/dotnet-run.md) 命令來編譯和執行範例。

## <a name="background-what-is-inheritance"></a>背景︰什麼是繼承？ ##

「繼承」**是物件導向程式設計的其中一個基本屬性。 它可讓您定義子類別，重複使用 (繼承)、擴充或修改父類別行為。 其成員可供繼承的類別稱為「基底類別」**。 繼承基底類別成員的類別則稱為「衍生類別」**。

C# 和 .NET 只支援「單一繼承」**。 也就是說，類別只能繼承自單一類別。 不過，繼承可以轉移，這可讓您定義一組型別的繼承階層。 換句話說，型別 `D` 可繼承自型別 `C`，其繼承自型別 `B`，而該型別的繼承來源為基底類別型別 `A`。 因為繼承可以轉移，所以型別 `D` 可以使用型別 `A` 的成員。

基底類別的所有成員不一定都由衍生類別繼承。 不會繼承的成員如下︰

- [靜態建構函式](../programming-guide/classes-and-structs/static-constructors.md)，其會初始化類別的靜態資料。

- [執行個體建構函式](../programming-guide/classes-and-structs/constructors.md)，您呼叫它來建立類別的新執行個體。 每個類別都必須定義自己的建構函式。

- [解構函式](../programming-guide/classes-and-structs/destructors.md)，由執行階段的記憶體回收行程呼叫以終結類別的執行個體。

由衍生類別繼承基底類別的所有其他成員時，是否可以看見它們，取決於其存取範圍。 成員存取範圍會影響其在衍生類別的可見性，如下所示︰

- [私用](../language-reference/keywords/private.md)成員只有以巢狀方式置於其基底類別時，才會顯示在衍生類別中。 否則，不會顯示在衍生類別中。 在下列範例中，`A.B` 是衍生自 `A` 的巢狀類別，而 `C` 則衍生自 `A`。 私用 `A.value` 欄位會顯示在 A.B 中。 不過，如果您移除 `C.GetValue` 方法中的註解，並嘗試編譯這個範例，它會產生編譯器錯誤 CS0122：「'A.value' 的保護層級導致無法對其進行存取」。

   [!CODE [Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/private.cs#1)]

- [受保護](../language-reference/keywords/protected.md)成員只會顯示在衍生類別中。

- [內部](../language-reference/keywords/protected.md)成員只會顯示在和基底類別位於相同組件的衍生類別中。 和基底類別位於不同組件的衍生類別中不會顯示它們。

- [公用](../language-reference/keywords/protected.md)成員會顯示在衍生類別中，它也是衍生類別公用介面的一部分。 公用繼承成員都可以呼叫，如同在衍生類別中定義一般。 在下列範例中，類別 `A` 定義名為 `Method1` 的方法，而類別 `B` 則繼承自 `A` 類別。 範例接著會將 `Method1` 視為 `B` 上的執行個體方法來呼叫。

[!CODE [Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/basics.cs#1)]

衍生類別也可以提供替代實作來「覆寫」**繼承的成員 。 基底類別中的成員必須標示有 [virtual](../language-reference/keywords/virtual.md) 關鍵字，才能覆寫成員。 根據預設，基底類別成員未標記為 `virtual`，因此無法覆寫。 如下列範例所示，嘗試覆寫非虛擬成員會產生編譯器錯誤 CS0506：「<member>無法覆寫繼承的成員<member>，因為其未標記為 virtual、abstract 或 override」。

   ```csharp
   public class A
   {
      public void Method1()
      {
         // Do something.
      }
   }

   public class B : A
   {
      public override void Method1()  // Generates CS0506.
      {
         // Do something else.
      }
   }
   ```

在某些情況下，衍生類別「必須」**覆寫基底類別實作。 標示有 [abstract](../language-reference/keywords/abstract.md) 關鍵字的基底類別成員都需要以衍生類別覆寫。 嘗試編譯下列範例會產生編譯器錯誤 CS0534：「<class> 未實作繼承的抽象成員 <member>」，因為類別 `B` 不會為 `A.Method1` 提供任何實作 。

   ```csharp
   public abstract class A
   {
      public abstract void Method1();
   }

   public class B : A                  // Generates CS0534.
   {
      public void Method3()
      {
         // Do something.
      }
   }
   ```

繼承只適用於類別和介面。 其他型別分類 (結構、委派及列舉) 均不支援繼承。 因此如下所示，嘗試編譯程式碼會產生編譯器錯誤 CS0527：「介面清單中的型別 'ValueType' 不是介面」。 錯誤訊息指出，雖然您可以定義結構實作的介面，但不支援繼承。

   ```csharp
   using System;

   public struct ValueStructure : ValueType       // Generates CS0527.
   {
   }
   ```

## <a name="implicit-inheritance"></a>隱含繼承 ##

除了透過單一繼承而繼承自的任何型別以外，@System.Object 或從中衍生的型別都會是 .NET 型別系統中所有型別的隱含繼承來源。 這樣可確保任何型別都可以使用一般功能。

為了說明隱含繼承表示的意思，讓我們定義只有空的類別定義的新類別 `SimpleClass`︰

[!CODE [Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#1)]

我們接下來可以使用反映 (可讓我們檢查型別的中繼資料以取得該型別的相關資訊) 來取得一份屬於 `SimpleClass` 型別的成員清單。 雖然我們尚未在 `SimpleClass` 類別中定義任何成員，但此範例的輸出指出它實際上有九個成員。 其中之一是 C# 編譯器為 `SimpleClass` 型別自動提供的無參數 (或預設) 建構函式。 當中八七個成員都屬於 @System.Object，該型別是 .NET 型別系統中所有類別與介面最終的隱含繼承來源。

[!CODE [Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass.cs#2)]

隱含繼承自 @System.Object 類別讓以下方法可以使用 `SimpleClass` 類別：

- 公用 `ToString` 方法會將 `SimpleClass` 物件轉換為其字串表示，亦即完整型別名稱。 在此情況下，`ToString` 方法會傳回字串 "SimpleClass"。

- 測試兩個物件是否相等的三種方法︰ 公用執行個體 `Equals(Object)` 方法、公用靜態 `Equals(Object, Object)` 方法以及公用靜態 `ReferenceEquals(Object, Object)` 方法。 根據預設，這些方法會測試參考是否相等。也就是說，兩個物件必須都參考相同的物件才會相等。

- 公用 `GetHashCode` 方法會計算出一個值，其允許在雜湊集合中使用該型別的執行個體。

- 公用 `GetType` 方法會傳回代表 `SimpleClass` 型別的 @System.Type 物件。

- 受保護的 @System.Object.Finalize 方法設計為在記憶體回收行程回收物件的記憶體之前釋放 Unmanaged 的資源。

- 受保護的 @System.Object.MemberwiseClone 方法會建立目前物件的淺層複製 (Shallow Clone)。

因為隱含繼承，所以我們能呼叫從 `SimpleClass`物件繼承的任何成員，如同 `SimpleClass` 類別中定義的實際成員一般。 例如，下列範例呼叫 `SimpleClass.ToString` 方法，其 `SimpleClass` 繼承自@System.Object。

[!CODE [Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/simpleclass2.cs#1)]

下表列出您可以在 C# 中建立型別分類和其隱含繼承自的類別。 每個基底型別都有一組不同的成員可透過繼承來使用以隱含地衍生型別。

| 型別分類 | 隱含繼承自... |
| :--- | :---: | ---: |
| Class - 類別 | @System.Object |
| struct | @System.ValueType, @System.Object |
| enum | @System.Enum、System.ValueType、@System.Object |
| 委派 | @System.MulticastDelegate, @System.Delegate, @System.Object |

## <a name="inheritance-and-an-is-a-relationship"></a>繼承和「是」關聯性 ##

在正常情況下，繼承用來表示基底類別與一或多個衍生類別之間的「是」關聯性，其中的衍生類別是基底類別的特殊版本；衍生類別是基底類別的一種型別。 例如，`Publication` 類別代表任何類型的發行物，而 `Book` 和 `Magazine` 類別代表特定發行物型別。

   [!NOTE] 類別或結構可以再實作另一個介面。 介面實作通常以單一繼承的因應措施或搭配結構使用繼承的方式呈現，但其目的在表達介面與其實作型別之間和繼承不同的關聯性 (「可以執行」關聯性)。 介面會定義一組其實作型別可以使用的功能子集 (例如測試相等、比較或排序物件，或支援區分文化特性剖析和格式化的能力)。

請注意，「是」也在表達型別與其特定具現化型別之間的關聯性。 在下列範例中，`Automobile` 類別有三個唯一的唯讀屬性︰ `Moke`為汽車製造商、`Model`為汽車種類以及 `Year`為其製造年份。 此 `Automobile` 類別還有一個建構函式，會將其引數指派給屬性值，並會覆寫 @System.Object.ToString 方法以產生可唯一識別 `Automobile` 執行個體的字串，而不是 `Automobile` 類別。

[!CODE [Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#1)]

在此情況下，我們不應該仰賴繼承來表示特定的車輛廠牌和款式。 例如，我們不需要定義 `Packard` 型別來表示 Packard Motor 汽車公司製造的汽車。 相反地，我們可以建立 `Automobile` 物件，將適當的值傳遞至它的類別建構函式，如下列範例所示。

[!CODE [Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/is-a.cs#2)]

以繼承為基礎的是關聯性，最適合用於基底類別，以及會對基底類別新增額外成員或其需要的額外功能是基底類別所沒有的衍生類別。

## <a name="designing-the-base-class-and-derived-classes"></a>設計基底類別和衍生類別 ##

讓我們來看設計基底類別和其衍生類別的流程。 在本節中，我們會定義基底類別 `Publication`，其代表任何類型的發行物，例如書籍、雜誌、報紙、期刊、文章等等。我們也會定義衍生自 `Book` 類別的類別 `Publication`。 我們可以輕鬆地擴充該範例來定義其他衍生類別，例如 `Magazine`、`Journal`、`Newspaper` 及 `Article`。

### <a name="the-base-publication-class"></a>基底 `Publication` 類別 ###

在設計 `Publication` 類別時，我們需要做出幾個設計決策︰

- 基底 `Publication` 類別中包含哪些成員，以及 `Publication` 成員是否提供方法實作，或 `Publication` 是否為抽象基底類別，可做為其衍生類別的範本。

   在此情況下，`Publication` 類別會提供方法實作。 [設計抽象基底類別和其衍生類別](#abstract)一節包含的範例會使用抽象基底類別，來定義衍生類別必須覆寫的方法。 衍生類別可隨意提供適用於衍生型別的任何實作。

   能夠重複使用程式碼 (也就是，多個衍生類別共用基底類別方法的宣告和實作，而不需要加以覆寫) 是非抽象基底類別的一項優點。 因此，如果 `Publication` 的程式碼可能會和一些或大部分特殊 `Publication` 型別共用，我們就應該將成員加入其中。 如果無法有效地完成，我們就不得不在衍生類別中大量提供相同的成員實作，而不是在基底類別中提供單一實作。 在多個位置中有重複的程式碼需要維護，是造成錯誤的潛在來源。

   為了能盡可能重複使用程式碼和建立邏輯與直覺式繼承階層，我們希望只將所有獲大部分發行物通用的資料與功能納入 `Publication` 類別中。 衍生類別接著實作其所代表特定發行物類型的唯一成員。

- 擴充類別階層的程度。 我們想要開發有三種類別以上的階層，還是只想要一個基底類別和一或多個衍生類別？ 例如，`Publication` 可以是 `Periodical` 的基底類別，而後者又是 `Magazine`、`Journal` 及 `Newspaper` 的基底類別。

   針對本範例，我們將使用有 `Publication` 類別和單一衍生類別 `Book` 的簡單階層。 我們可以輕鬆地擴充範例，以建立一些衍生自 `Publication` (例如 `Magazine` 和 `Article`) 的其他類別。

- 將基底類別具現化是否適當。 如果不適當，我們應該對該類別套用 [abstract](../language-reference/keywords/abstract.md) 關鍵字。 如果直接呼叫其類別建構函式，嘗試具現化標示有 `abstract` 關鍵字的類別，C# 編譯器會產生錯誤 CS0144：「無法建立抽象類別或介面的執行個體」。 如果使用反映嘗試具現化該類別，反映方法會擲回 @System.MemberAccessException。 否則，可以呼叫其類別建構函式具現化 `Publication` 類別。

   根據預設，可以呼叫其類別建構函式具現化基底類別。 請注意，我們不必明確地定義類別建構函式。 如果基底類別的原始程式碼中尚未存在建構函式，C# 編譯器會自動提供預設 (無參數) 建構函式。

   針對本範例，我們將 `Publication` 類別標記為 [abstract](../language-reference/keywords/abstract.md)，使它無法具現化。

- 衍生類別是否必須繼承特定成員的基底類別實作，或是有覆寫基底類別實作的選項。 我們都必須使用 [virtual](../language-reference/keywords/virtual.md) 關鍵字，以允許衍生類別覆寫基底類別方法。 根據預設，「不」**可覆寫基底類別中定義的方法。

- 衍生類別是否代表繼承階層中的最後一個類別，且本身無法用來做為額外衍生類別的基底類別。 根據預設，任何類別可以做為基底類別。 我們可以套用 [sealed](../language-reference/keywords/sealed.md) 關鍵字 ，指出類別不可以做為任何其他類別的基底類別。 嘗試衍生自密封類別會產生編譯器錯誤 CS0509：「無法衍生自密封型別 <typeName>」。

   針對本範例，我們會將衍生類別標記為 `sealed`。

下列範例示範 `Publication` 類別的原始程式碼，以及由 `Publication.PublicationType` 屬性所傳回的 `PublicationType` 列舉。 除了其繼承自 @System.Object 的成員以外，`Publication` 類別還會定義下列的唯一成員，以及定義成員覆寫︰

[!CODE [Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#1)]

- 建構函式

  因為 `Publication` 類別是 `abstract`，所以它無法從程式碼直接具現化，如下所示︰

  ```csharp
  var publication = new Publication("Tiddlywinks for Experts", "Fun and Games",
                                    PublicationType.Book);
  ```

  不過，其執行個體建構函式可以從衍生類別建構函式直接呼叫，如 `Book` 類別的原始程式碼所示。

- 兩個發行物相關的屬性

  `Title` 是唯讀 @System.String 屬性，其值是透過呼叫 `Publication` 建構函式提供，該值會儲存在名為 `pubTitle` 的私用欄位中。

  `Pages` 是可讀寫 @System.Int32 屬性，指出發行物的總頁數。 該值會儲存在名為 `totalPages` 的私用欄位中。 它必須為正數，否則會擲回 @System.ArgumentOutOfRangeException。

- 發行者相關的成員

  `Publisher` 和 `Type` 這兩個唯讀屬性會傳回私用 `pubName` 和 `pubType` 欄位的值。 這些值就是原先呼叫 `Publication` 類別建構函式所提供的值。

- 與發佈相關的成員

  `Publish` 和 `GetPublicationDate` 這兩個方法可設定和傳回發行日期。 當呼叫 `Publish` 方法並將傳遞給它的日期指派為私用 `datePublished` 欄位的引數時，它會將私用 `published` 旗標設定為 `true`。 如果 `published` 旗標是 `false`，`GetPublicationDate` 方法會傳回字串 "NYP"，如果是 `true`，則會傳回 `datePublished` 欄位的值。

- 著作權相關的成員

  `Copyright` 方法會將著作權所有人的名稱和著作權年份做為引數，並將它們指派給私用 `copyrName` 和 `copyrDate` 欄位。 您可以從 `CopyrightName` 與 `CopyrightDate` 屬性來擷取值。

- 覆寫 `ToString` 方法

  如果某型別不會覆寫 @System.Object.ToString 方法，它會傳回該型別的完整名稱，該名稱很少用來區分不同的執行個體。 `Publication` 類別會覆寫 @System.Object.ToString 以傳回 `Title` 屬性的值。

下圖說明基底 `Publication` 類別和其隱含繼承的 @System.Object 類別之間的關聯性。

![物件和發行物類別](media/publication-class.jpg)

### <a name="the-book-class"></a>`Book` 類別 ###

`Book` 類別代表特殊的發行物型別：書籍。 下列範例顯示 `Book` 類別的原始程式碼。

[!CODE [Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/base-and-derived.cs#2)]

除了其繼承自 `Publication` 的成員以外，`Book` 類別還會定義下列的唯一成員，以及定義成員覆寫︰

- 兩個建構函式

  這兩個 `Book` 建構函式共用三個常見參數。 *title* 和 *publisher* 這兩個會對應至 `Publication` 建構函式的參數。 第三個為 *author*，其會儲存至私用 `authorName` 欄位。 一個建構函式包含 *isbn* 參數，其會儲存至私用 `id` 欄位。

  第一個建構函式會使用 [this](../language-reference/keywords/this.md) 關鍵字來呼叫另一個建構函式。 這是定義建構函式的常見模式。呼叫參數個數最多的建構函式時，參數個數較少的建構函式會提供預設值。

  第二個建構函式使用 [base](../language-reference/keywords/base.md) 關鍵字，來將標題和發行者名稱傳遞給基底類別建構函式。 如果您在原始程式碼中沒有明確呼叫基底類別建構函式，C# 編譯器會自動呼叫基底類別的預設或無參數建構函式。

- 唯讀 `ISBN` 屬性，會傳回 `Book` 物件的國際標準書號，一組有 10 或 13 位數的唯一數字。 ISBN 會做為引數提供給其中一個 `Book` 建構函式，並會儲存在私用 `id` 欄位。

- 唯讀 `Author` 屬性。 作者名稱會做為引數提供給那兩個 `Book` 建構函式，並會儲存在私用 `authorName` 欄位。

- 兩個價格相關的唯讀屬性，`Price` 和 `Currency`。 其值將在 `SetPrice` 方法呼叫中做為引數提供。 該價格會儲存在私用欄位 `bookPrice` 中。 `Currency` 屬性是三位數的 ISO 貨幣符號 (例如 USD 代表美元)，而且會儲存在私用 `ISOCurrencySymbol` 欄位。 ISO 貨幣符號可從 @System.Globalization.RegionInfo.ISOCurrencySymbol 屬性擷取。

- `SetPrice` 方法會設定 `bookPrice` 和 `ISOCurrencySymbol` 欄位的值。 這些都是 `Price` 和 `Currency` 屬性所傳回的值。

- 覆寫 `ToString` 方法 (繼承自`Publication`) 和@System.Object.Equals(System.Object) 與 @System.Object.GetHashCode 方法 (繼承自@System.Object)。

  除非遭到覆寫，否則 @System.Object.Equals(System.Object) 方法不會測試參考是否相等。 也就是說，如果兩個物件變數都參考相同的物件，才會將兩者視為相等。 換句話說，在 `Book` 類別的情況下，如果兩個 `Book` 物件都有相同的 ISBN，兩者應該相等。

  當您覆寫 @System.Object.Equals(System.Object) 方法時，您也必須覆寫 @System.Object.GetHashCode 方法，執行階段會將傳回的值用來儲存雜湊集合中的項目，以讓擷取有效率。 雜湊碼應會傳回和相等測試一致的值。 因為我們已經覆寫 @System.Object.Equals(System.Object) 以傳回 `true`，所以如果兩個 `Book` 物件的 ISBN 屬性相等，我們會呼叫 `ISBN` 屬性所傳回字串的 @System.String.GetHashCode 方法計算出的雜湊碼。

下圖說明 `Book` 類別和其 `Publication` 基底類別之間的關聯性。

![發行物和書籍類別](media/book-class.jpg)

我們現在可以具現化 `Book` 物件，叫用其唯一與繼承成員，然後將它做為引數傳遞給預期參數為型別 `Publication` 或型別 `Book` 的方法，如下列範例所示。

[!CODE [Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/use-publication.cs#1)]

## <a name="abstract"></a>設計抽象基底類別和其衍生類別 ##

在上述範例中，我們定義的基底類別會為一些方法提供實作，以允許衍生類別共用程式碼。 不過，在許多情況下，基底類別不需要提供實作。 相反地，基底類別是抽象類別「」**。它會做為範本，定義每個衍生類別都必須實作的成員。 通常在抽象基底類別中，每個衍生型別都會有該型別的唯一實作。

例如，每個封閉的二維幾何圖形都包括兩個屬性：面積 (其為圖形內部範圍) 以及周長或圖形邊緣的距離。 不過，計算這些屬性的方式，完全取決於特定圖形。 例如，計算圓形的周長 (圓周) 的公式，就和計算三角形周長的公式相當不同。

下列範例定義一個名為 `Shape` 的基底類別，其中定義兩個屬性︰`Area` 和 `Perimeter`。 請注意，除了標示有 [abstract](../language-reference/keywords/abstract.md) 關鍵字的類別，每個執行個體成員也都標示 [abstract](../language-reference/keywords/abstract.md) 關鍵字。 在此情況下，`Shape` 也會覆寫 @System.Object.ToString 方法以傳回型別的名稱，而不是其完整名稱。 此外，它會定義兩個靜態成員 `GetArea` 和 `GetPerimeter`，讓呼叫端能夠輕鬆地擷取任何衍生類別執行個體的面積和周長。 當我們將衍生類別的執行個體傳遞給上述任一種方法時，執行階段都會呼叫衍生類別的方法覆寫。

[!CODE [Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#1)]

我們接著可以從代表特定圖形的 `Shape` 衍生一些類別。 下列範例定義三個類別：`Triangle`、`Rectangle` 和 `Circle`。 每個都使用該特定圖形的唯一公式來計算的面積和周長。 某些衍生類別也定義其所代表圖形特有的屬性，例如 `Rectangle.Diagonal` 和 `Circle.Diameter`。

[!CODE [Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#2)]

下列範例使用衍生自 `Shape` 的物件。 具現化衍生自 `Shape` 的物件陣列，並呼叫會包裝所傳回 `Shape` 屬性值的 `Shape` 類別靜態方法。 請注意，執行階段會從衍生型別的覆寫屬性擷取值。 範例也會將陣列中的每個 `Shape` 物件轉換為其衍生型別，而且如果轉換成功，就會擷取 `Shape` 的那個特定子類別的屬性。 

[!CODE [Inheritance](../../../samples/snippets/csharp/tutorials/inheritance/shape.cs#3)]

## <a name="see-also"></a>請參閱 ##

[類別與物件](../tour-of-csharp/classes-and-objects.md)</br>
[繼承 (C# 程式設計指南)](../programming-guide/classes-and-structs/inheritance.md)

