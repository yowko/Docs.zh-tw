---
title: ".NET 入門"
description: ".NET 入門"
keywords: .NET, .NET Core
author: richlander
manager: wpickett
ms.date: 10/05/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
translationtype: Human Translation
ms.sourcegitcommit: be774ae1291def36baafffbf2f717cf98565cd60
ms.openlocfilehash: fba870a93784b579da1065a07d82974951ac7e28

---

# <a name="net-primer"></a>.NET 入門

> 請參閱[＜.NET Core 使用者入門＞教學課程](../core/getting-started.md)，以了解如何建立簡單的 .NET Core 應用程式。 只需要幾分鐘，您就可以啟動並執行您的第一個應用程式。

.NET 是一般用途開發平台。 它可用於使用一般用途方案的任何應用程式類型或工作負載。 它包含幾項對許多開發人員而言具吸引力的重要功能，包括自動記憶體管理和現代程式語言，可讓您更輕鬆且有效率地建置高品質應用程式。 .NET 支援具有許多便利功能的高層級程式設計環境，同時提供原生記憶體和 API 的低層級存取。

您可以使用以指定平台基礎的開放 [.NET 標準](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md)為基礎的多項 .NET 實作。 這些實作分別針對不同的應用程式類型 (例如傳統型、行動、遊戲、雲端) 進行最佳化，並支援許多晶片 (例如 x86/x64、ARM) 和作業系統 (例如 Windows、Linux、iOS、Android、macOS)。 開放原始碼也是 .NET 生態系統很重要的一環，具有多項 .NET 實作，並有許多經 OSI 核准授權的程式庫可用。

若要查明 Microsoft 和其他產品可用的所有不同 .NET 版本，請參閱 [.NET 實作概觀](../about/products.md)文件。

本入門將協助您了解 .NET 平台的一些重要概念，並指出每個指定主題的更多資源。 本文結束時，您應該具備足夠的資訊，能夠辨識 .NET 平台的重要詞彙和概念，並了解如何進一步擴充相關知識。 

## <a name="a-stroll-through-net"></a>.NET 概觀

如同任何成熟和進階的應用程式開發架構，.NET 具有許多強大的功能，除了讓開發人員的工作更輕鬆之外，主要是為了撰寫出更強大且易懂的程式碼。 本節將概述最重要之功能的基本概念，並指出需要更詳細討論的地方。 完成此概觀之後，您應該具備足夠的資訊，能夠閱讀 GitHub 儲存機制上的範例及其他程式碼，並了解運作狀況。

*   [程式設計語言](#programming-languages)
*   [自動記憶體管理](#automatic-memory-management)
*   [型別安全](#type-safety)
*   [委派和 Lambda](#delegates-and-lambdas)
*   [泛型型別 (泛型)](#generic-types-generics)
*   [Language-Integrated Query (LINQ)](#language-integrated-query-linq)
*   [非同步程式設計](#async-programming)
*   [原生互通性](#native-interoperability)
*   [不安全的程式碼](#unsafe-code)

### <a name="programming-languages"></a>程式語言

身為開發人員，您可以選擇任何支援 .NET 的程式語言來建立應用程式。 由於 .NET 提供語言獨立性和互通性，因此不論開發時使用的語言為何，您都可以與其他 .NET 應用程式和元件互動。

可讓您開發適用於 .NET 平台之應用程式的語言會遵守[通用語言基礎結構 (CLI) 規格](https://www.visualstudio.com/en-us/mt639507)。

.NET 支援的 Microsoft 語言包括 C#、F# 和 Visual Basic。 

* C# 很簡單、強大、型別安全且物件導向，同時保留 C 樣式語言的易讀性與簡潔性。 熟悉 C 和類似語言的任何人在適應 C# 方面很少有問題。

* F# 是跨平台、功能優先的程式語言，也支援傳統物件導向和命令式程式設計。

* Visual Basic 是容易學習的語言，您可以使用該語言建置 .NET 上所執行的各種應用程式。

> [!NOTE]
> 在 .NET Core 的目前版本中，只有 C# 受到所有 Microsoft 工具的完整支援。  F# 受到 .NET Core SDK 的支援，但不包括 Visual Studio 工具。  未來將推出 SDK 和 Visual Studio 工具的 Visual Basic 支援。

### <a name="automatic-memory-management"></a>自動記憶體管理

記憶體回收是眾所皆知的 .NET 功能。 開發人員不需要主動管理記憶體，不過有些機制提供記憶體回收行程 (GC) 的更多資訊。 C# 包含 `new` 關鍵字以依照特定類型配置記憶體，並包含 `using` 關鍵字以提供物件的使用範圍。 GC 採用 lazy 方法來管理記憶體，優先考慮應用程式輸送量，而不是立即收集記憶體。

下列兩行會配置記憶體：

```cs
var title = ".NET Primer";
var list = new List<string>;

```

沒有類似的關鍵字可取消配置記憶體，因為當記憶體回收行程透過其排程執行回收記憶體時，就會自動取消配置。

方法變數通常會在方法完成之後移出範圍，此時可加以收集。 不過，您可以在方法結束之前，使用 `using` 陳述式對 GC 指出特定物件超出範圍。

```cs
using(FileStream stream = GetFileStream(context))
{
    //operations on the stream
}

```

`using` 區塊完成之後，GC 就會知道上述範例中的 `stream` 物件可用，因此可加以收集並回收其記憶體。

記憶體回收行程會啟用一項較不明顯、但具有深遠影響的功能，那就是記憶體安全。 確保記憶體永遠安全並不困難︰如果程式只存取已配置的記憶體 (而不是釋放的記憶體)，就是記憶體安全。 懸置的指標一律是錯誤，而追蹤其來源通常很困難。

.NET 執行階段提供其他服務，來達成記憶體安全的承諾 (GC 原本並未提供)。 它可確保程式不會從陣列結尾編製索引，也不會從物件結尾取出虛設項目欄位。

下列範例會擲回例外狀況，以作為記憶體安全的結果。

```cs
int[] numbers = new int[42];
int number = numbers[42]; // will throw (indexes are 0-based)

```

### <a name="type-safety"></a>型別安全

物件會依照類型配置。 物件的類型會決定該物件所允許的唯一作業，以及所使用的記憶體。 `Dog` 類型可能會有 `Jump` 和 `WagTail` 方法，但不太可能會有 `SumTotal` 方法。 程式只能呼叫指定類型的宣告方法。 所有其他呼叫會導致編譯時期錯誤，或執行階段例外狀況 (如果使用動態功能或 `object`)。

.NET 語言是物件導向，具有基底和衍生類別的階層架構。 .NET 執行階段只允許符合物件階層架構的的物件轉換和呼叫。 請記住，以任何 .NET 語言所定義的每種類型都是衍生自基底 `object` 類型。

```cs
Dog dog = Dog.AdoptDog(); // Returns a Dog type
Pet pet = (Pet)dog; // Dog derives from Pet
pet.ActCute();
Car car = (Car)dog; // will throw - no relationship between Car and Dog
object temp = (object)dog; // legal - a Dog is an object
car = (Car)temp; // will throw - the runtime isn't fooled
car.Accelerate() // the dog won't like this, nor will the program get this far

```

此外也會使用型別安全，藉由確保存取子關鍵字的精確度，來協助強制執行封裝。 存取子關鍵字是控制其他程式碼存取指定類型成員的成品。 這些關鍵字通常會用於某種類型中用來管理其行為的各種資料。

```cs
Dog dog = Dog._nextDogToBeAdopted; // will throw - this is a private field

```

有些 .NET 語言支援**型別推斷**。 型別推斷表示編譯器會從右邊的運算式推算左邊的運算式類型。 這並不會破壞或規避型別安全。 產生的類型**具有**強類型，其中包含其所指的所有項目。 讓我們重寫上一個範例中的前兩行，以引入型別推斷。 您會發現，此範例的其餘部分完全相同。

```cs
  var dog = Dog.AdoptDog();
  var pet = (Pet)dog;
  pet.ActCute();
  Car car = (Car)dog; // will throw - no relationship between Car and Dog
  object temp = (object)dog; // legal - a Dog is an object
  car = (Car)temp; // will throw - the runtime isn't fooled
  car.Accelerate() // the dog won't like this, nor will the program get this far

```

### <a name="delegates-and-lambdas"></a>委派和 Lambda

委派與 C++ 函式指標類似，主要的差別在於委派是型別安全。 委派是 CLR 型別系統中一種已中斷連線的方法。 一般方法是附加到類別，並且只能透過靜態或執行個體呼叫慣例來直接呼叫。

委派可用於 .NET 世界中各種不同的 API 和位置，尤其是透過 Lambda 運算式，這是 LINQ 的基石。

如需詳細資訊，請參閱[委派和 Lambda](delegates-lambdas.md) 文件。

### <a name="generic-types-generics"></a>泛型型別 (泛型)

泛型型別 (通常也稱為「泛型」) 是 .NET Framework 2.0 中新增的功能。 簡單來說，泛型可讓程式設計人員在設計其類別時引入「型別參數」，如此即可讓用戶端程式碼 (類型的使用者) 指定正確類型來取代型別參數。

新增泛型功能是為了協助程式設計人員實作泛型資料結構。 在此功能之前，若要讓 _List_ 類型成為泛型，您必須使用 _object_ 類型的項目。 這樣做會有各種效能及語意問題，更別提可能會有難以解決的執行階段錯誤。 後者最糟的情況是在資料結構同時包含整數和字串時，而且會在使用清單的成員時擲回 _InvalidCastException_。

下列範例示範使用 @System.Collections.Generic.List%601 類型執行個體的基本程式執行。

```cs
using System;
using System.Collections.Generic;

namespace GenericsSampleShort {
    public static void Main(string[] args){
        // List<string> is the client way of specifying the actual type for the type parameter T
        List<string> listOfStrings = new List<string> { "First", "Second", "Third" };

        // listOfStrings can accept only strings, both on read and write.
        listOfStrings.Add("Fourth");

        // Below will throw a compile-time error, since the type parameter
        // specifies this list as containing only strings.
        listOfStrings.Add(1);

    }
}

```

如需詳細資訊，請參閱[泛型型別 (泛型) 概觀](generics.md)一文。

### <a name="async-programming"></a>非同步程式設計

非同步程式設計是 .NET 中的最高階概念，包括執行階段、Framework 程式庫和 .NET 語言建構的非同步支援。 就內部而言，它們是以物件 (例如 `Task`) 為基礎，可利用作業系統盡可能有效率地執行 I/O-bound 工作。

若要深入了解 .NET 非同步程式設計，請從[非同步概觀](async.md)開始。

### <a name="language-integrated-query-linq"></a>Language Integrated Query (LINQ)

LINQ 是一組強大的 C# 和 VB 功能，可讓您撰寫簡單的宣告式程式碼來操作資料。 資料可以是許多形式 (例如 SQL 資料庫中的記憶體內部物件或 XML 文件)，但您通常針對每個資料來源所撰寫的 LINQ 程式碼看起來大同小異！

若要深入了解及查看一些範例，請參閱 [LINQ (Language Integrated Query)](using-linq.md)。

### <a name="native-interoperability"></a>原生互通性

目前使用的每個作業系統會針對各種程式設計工作提供許多平台支援。 .NET 提供幾種方式來使用這些 API。 整體而言，這項支援稱為「原生互通性」。在本節中，我們將探討如何從 Managed .NET 程式碼存取原生 API。

執行原生互通性的主要方式是透過「平台叫用」(簡稱 P/Invoke)。 您可以在不同的 Linux 和 Windows 平台之間使用 .NET Core 的這項支援。 另一項僅適用於 Windows 的原生互通性做法稱為 "COM Interop"，可用來處理 Managed 程式碼中的 [COM 元件](https://msdn.microsoft.com/library/bwa2bx93.aspx)。 它是以 P/Invoke 基礎結構為建置基礎，但運作方式稍有不同。

Mono (以及 Xamarin) 對 Java 和 Objective-C 的互通性支援大致上很類似；也就是說，它們使用相同的原則。

如需詳細資訊，請參閱[原生互通性](native-interop.md)文件。

### <a name="unsafe-code"></a>Unsafe 程式碼

CLR 可讓您透過 `unsafe` 程式碼存取原生記憶體及執行指標算術。 特定演算法和系統互通性需要這些作業。 Unsafe 程式碼雖然功能強大，但除非是必須與系統 API 互通，或必須實作最有效率的演算法，否則不建議使用。 Unsafe 程式碼在不同的環境中執行時可能不盡相同，而且也會失去記憶體回收行程和型別安全的好處。 建議您盡可能限制和集中使用 Unsafe 程式碼，並徹底測試該程式碼。

[StringBuilder 類別](https://github.com/dotnet/coreclr/blob/master/src/mscorlib/src/System/Text/StringBuilder.cs#L327)中的 `ToString()` 方法說明使用 `unsafe` 程式碼時，如何藉由直接四處移動記憶體區塊，以有效率地實作演算法：

```cs
public override String ToString() {
          Contract.Ensures(Contract.Result<String>() != null);

          VerifyClassInvariant();

          if (Length == 0)
              return String.Empty;

          string ret = string.FastAllocateString(Length);
          StringBuilder chunk = this;
          unsafe {
              fixed (char* destinationPtr = ret)
              {
                  do
                  {
                      if (chunk.m_ChunkLength > 0)
                      {
                          // Copy these into local variables so that they are stable even in the presence of ----s (hackers might do this)
                          char[] sourceArray = chunk.m_ChunkChars;
                          int chunkOffset = chunk.m_ChunkOffset;
                          int chunkLength = chunk.m_ChunkLength;

                          // Check that we will not overrun our boundaries.
                          if ((uint)(chunkLength + chunkOffset) <= ret.Length && (uint)chunkLength <= (uint)sourceArray.Length)
                          {
                              fixed (char* sourcePtr = sourceArray)
                                  string.wstrcpy(destinationPtr + chunkOffset, sourcePtr, chunkLength);
                          }
                          else
                          {
                              throw new ArgumentOutOfRangeException("chunkLength", Environment.GetResourceString("ArgumentOutOfRange_Index"));
                          }
                      }
                      chunk = chunk.m_ChunkPrevious;
                  } while (chunk != null);
              }
          }
          return ret;
      }

```

## <a name="notes"></a>備註

文件中使用「.NET 執行階段」一詞來表示 .NET 的多項實作，例如 CLR、Mono、IL2CPP 等等。 只有在必要時，才會使用更特定的名稱。

本文件實際上不在回顧過去，而在描述 .NET 平台的現況。 .NET 功能是否一直可用或最近才引入並不重要，重要的是它值得強調及討論。



<!--HONumber=Nov16_HO1-->


