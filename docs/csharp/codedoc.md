---
title: "使用 XML 註解記錄您的程式碼"
description: "了解如何使用 XML 文件註解記錄您的程式碼，並在編譯時期產生 XML 文件檔案。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 02/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0cb5725a70d94173c8596f818dcaa6eb2de13bcc
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="documenting-your-code-with-xml-comments"></a>使用 XML 註解記錄您的程式碼

XML 文件註解是一種特殊類型的註解，新增於任何使用者定義型別或成員的定義上方。 XML 文件註解具特殊性，因為編譯器可以處理它們以在編譯時期產生 XML 文件檔案。
編譯器所產生的 XML 檔案可以隨著 .NET 組件一起散發，因此 Visual Studio 和其他 IDE 可以使用 IntelliSense 來顯示類型或成員的快速資訊。 此外，可以透過 [DocFX](https://dotnet.github.io/docfx/) 和 [Sandcastle](https://github.com/EWSoftware/SHFB) 這類工具執行 XML 檔案來產生 API 參考網站。

編譯器會忽略 XML 文件註解 (例如所有其他註解)。

您可以執行下列其中一項動作，以在編譯時期產生 XML 檔案︰

- 如果您正在從命令列使用 .NET Core 開發應用程式，則可以將 [DocumentationFile 項目](http://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties)新增至 .csproj 專案檔的 `<PropertyGroup>` 區段。 下列範例會在根檔案名稱與專案相同的專案目錄中產生 XML 檔案：

   ```xml
   <DocumentationFile>$(MSBuildProjectName).xml</DocumentationFile>
   ```

   您也可以指定 XML 檔案的確切絕對或相對路徑和名稱。 下列範例會在與應用程式的偵錯版本相同的目錄中產生 XML 檔案︰

    ```xml
   <DocumentationFile>bin\Debug\netcoreapp1.0\App.xml</DocumentationFile>
   ```

- 如果您正在使用 Visual Studio 開發應用程式，請以滑鼠右鍵按一下專案，然後選取 [屬性]****。 在屬性對話方塊中，選取 [建置]**** 索引標籤，然後檢查 [XML 文件檔案]****。 您也可以變更編譯器寫入檔案的位置。 

- 如果您正在從命令列編譯 .NET Framework 應用程式，請在編譯時新增 [/doc 編譯器選項](language-reference/compiler-options/doc-compiler-option.md)。  

XML 文件註解使用三個正斜線 (`///`) 和 XML 格式化註解主體。 例如: 

```csharp
/// <summary>
/// This class does something.
/// </summary>
public class SomeClass
{
}
```

## <a name="walkthrough"></a>逐步解說

讓我們逐步記錄極基本的數學庫，讓新的開發人員輕鬆了解/參與以及讓協力廠商開發人員使用。

以下是簡單數學程式庫的程式碼︰

```csharp
/*
    The main Math class
    Contains all methods for performing basic math functions
*/
public class Math
{
    // Adds two integers and returns the result
    public static int Add(int a, int b)
    {
        // If any parameter is equal to the max value of an integer
        // and the other is greater than zero
        if ((a == int.MaxValue && b > 0) || (b == int.MaxValue && a > 0))
            throw new System.OverflowException();

        return a + b;
    }

    // Adds two doubles and returns the result
    public static double Add(double a, double b)
    {
        if ((a == double.MaxValue && b > 0) || (b == double.MaxValue && a > 0))
            throw new System.OverflowException();

        return a + b;
    }

    // Subtracts an integer from another and returns the result
    public static int Subtract(int a, int b)
    {
        return a - b;
    }

    // Subtracts a double from another and returns the result
    public static double Subtract(double a, double b)
    {
        return a - b;
    }

    // Multiplies two integers and returns the result
    public static int Multiply(int a, int b)
    {
        return a * b;
    }

    // Multiplies two doubles and returns the result
    public static double Multiply(double a, double b)
    {
        return a * b;
    }

    // Divides an integer by another and returns the result
    public static int Divide(int a, int b)
    {
        return a / b;
    }

    // Divides a double by another and returns the result
    public static double Divide(double a, double b)
    {
        return a / b;
    }
}
```

範例程式庫支援 `int` 和 `double` 資料型別上的四個主要算術運算 `add`、`subtract`、`multiply` 和 `divide`。

現在，您想要可以針對使用您的程式庫但無法存取原始程式碼的協力廠商開發人員，從您的程式碼建立 API 參考文件。
如前所述，XML 文件標記可以用來達成這項作業。現在已引進 C# 編譯器所支援的標準 XML 標記。

### <a name="ltsummarygt"></a>&lt;summary&gt;

`<summary>` 標記會新增類型或成員的簡短資訊。
我會將它新增至 `Math` 類別定義和第一個 `Add` 方法來示範其使用方式，請自由套用至您程式碼的其餘部分。

```csharp
/*
    The main Math class
    Contains all methods for performing basic math functions
*/
/// <summary>
/// The main Math class.
/// Contains all methods for performing basic math functions.
/// </summary>
public class Math
{
    // Adds two integers and returns the result
    /// <summary>
    /// Adds two integers and returns the result.
    /// </summary>
    public static int Add(int a, int b)
    {
        // If any parameter is equal to the max value of an integer
        // and the other is greater than zero
        if ((a == int.MaxValue && b > 0) || (b == int.MaxValue && a > 0))
            throw new System.OverflowException();

        return a + b;
    }
}
```

`<summary>` 標記十分重要，因為它的內容是 IntelliSense 或 API 參考文件中類型或成員資訊的主要來源，所以建議您包含它。

### <a name="ltremarksgt"></a>&lt;remarks&gt;

`<remarks>` 標記會補充 `<summary>` 標記所提供的類型或成員的相關資訊。 在此範例中，您只會將它新增至類別。

```csharp
/*
    The main Math class
    Contains all methods for performing basic math functions
*/
/// <summary>
/// The main Math class.
/// Contains all methods for performing basic math functions.
/// </summary>
/// <remarks>
/// This class can add, subtract, multiply and divide.
/// </remarks>
public class Math
{

}
```

### <a name="ltreturnsgt"></a>&lt;returns&gt;

`<returns>` 標記描述方法宣告的傳回值。
如前所示，下列範例說明第一個 `Add` 方法的 `<returns>` 標記。 您可以對其他方法執行相同作業。

```csharp
// Adds two integers and returns the result
/// <summary>
/// Adds two integers and returns the result.
/// </summary>
/// <returns>
/// The sum of two integers.
/// </returns>
public static int Add(int a, int b)
{
    // If any parameter is equal to the max value of an integer
    // and the other is greater than zero
    if ((a == int.MaxValue && b > 0) || (b == int.MaxValue && a > 0))
        throw new System.OverflowException();

    return a + b;
}
```

### <a name="ltvaluegt"></a>&lt;value&gt;

`<value>` 標記類似於 `<returns>` 標記，但將它用作屬性除外。
假設 `Math` 程式庫的靜態屬性稱為 `PI`，以下是使用這個標記的方式：

```csharp
/*
    The main Math class
    Contains all methods for performing basic math functions
*/
/// <summary>
/// The main Math class.
/// Contains all methods for performing basic math functions.
/// </summary>
/// <remarks>
/// This class can add, subtract, multiply and divide.
/// These operations can be performed on both integers and doubles
/// </remarks>
public class Math
{
    /// <value>Gets the value of PI.</value>
    public static double PI { get; }
}
```

### <a name="ltexamplegt"></a>&lt;example&gt;

您可以使用 `<example>` 標記，以在 XML 文件中包括範例。
這包含如何使用子 `<code>` 標記。

```csharp
// Adds two integers and returns the result
/// <summary>
/// Adds two integers and returns the result.
/// </summary>
/// <returns>
/// The sum of two integers.
/// </returns>
/// <example>
/// <code>
/// int c = Math.Add(4, 5);
/// if (c > 10)
/// {
///     Console.WriteLine(c);
/// }
/// </code>
/// </example>
public static int Add(int a, int b)
{
    // If any parameter is equal to the max value of an integer
    // and the other is greater than zero
    if ((a == int.MaxValue && b > 0) || (b == int.MaxValue && a > 0))
        throw new System.OverflowException();

    return a + b;
}
```

`code` 標記會保留分行符號以及較長範例的縮排。

### <a name="ltparagt"></a>&lt;para&gt;

您可以使用 `<para>` 標記來格式化其父標記內的內容。 `<para>` 通常用於標記內 (例如 `<remarks>` 或 `<returns>`)，以將文字分成數個段落。
您可以繼續並格式化類別定義的 `<remarks>` 標記內容。

```csharp
/*
    The main Math class
    Contains all methods for performing basic math functions
*/
/// <summary>
/// The main Math class.
/// Contains all methods for performing basic math functions.
/// </summary>
/// <remarks>
/// <para>This class can add, subtract, multiply and divide.</para>
/// <para>These operations can be performed on both integers and doubles.</para>
/// </remarks>
public class Math
{

}
```

### <a name="ltcgt"></a>&lt;c&gt;

仍然，在有關格式化的主題，您可以使用 `<c>` 標記將一部分文字標記為程式碼。
它就像 `<code>` 標記，只是會內嵌。 這適用於您想要將快速程式碼範例顯示為標記內容的一部分時。
請更新 `Math` 類別的文件。

```csharp
/*
    The main Math class
    Contains all methods for performing basic math functions
*/
/// <summary>
/// The main <c>Math</c> class.
/// Contains all methods for performing basic math functions.
/// </summary>
public class Math
{

}
```

### <a name="ltexceptiongt"></a>&lt;exception&gt;

使用 `<exception>` 標記，讓您的開發人員知道方法可以擲回特定例外狀況。
查看 `Math` 程式庫，即可看到兩個 `Add` 方法在符合特定條件時擲回例外狀況。 雖然不明顯，但如果 `b` 參數為零，則也會擲回整數 `Divide` 方法。 現在將例外狀況文件新增至這個方法。

```csharp
/*
    The main Math class
    Contains all methods for performing basic math functions
*/
/// <summary>
/// The main <c>Math</c> class.
/// Contains all methods for performing basic math functions.
/// </summary>
public class Math
{
    /// <summary>
    /// Adds two integers and returns the result.
    /// </summary>
    /// <returns>
    /// The sum of two integers.
    /// </returns>
    /// <example>
    /// <code>
    /// int c = Math.Add(4, 5);
    /// if (c > 10)
    /// {
    ///     Console.WriteLine(c);
    /// }
    /// </code>
    /// </example>
    /// <exception cref="System.OverflowException">Thrown when one parameter is max 
    /// and the other is greater than 0.</exception>
    public static int Add(int a, int b)
    {
        if ((a == int.MaxValue && b > 0) || (b == int.MaxValue && a > 0))
            throw new System.OverflowException();

        return a + b;
    }

    /// <summary>
    /// Adds two doubles and returns the result.
    /// </summary>
    /// <returns>
    /// The sum of two doubles.
    /// </returns>
    /// <exception cref="System.OverflowException">Thrown when one parameter is max 
    /// and the other is greater than zero.</exception>
    public static double Add(double a, double b)
    {
        if ((a == double.MaxValue && b > 0) || (b == double.MaxValue && a > 0))
            throw new System.OverflowException();

        return a + b;
    }

    /// <summary>
    /// Divides an integer by another and returns the result.
    /// </summary>
    /// <returns>
    /// The division of two integers.
    /// </returns>
    /// <exception cref="System.DivideByZeroException">Thrown when a division by zero occurs.</exception>
    public static int Divide(int a, int b)
    {
        return a / b;
    }

    /// <summary>
    /// Divides a double by another and returns the result.
    /// </summary>
    /// <returns>
    /// The division of two doubles.
    /// </returns>
    public static double Divide(double a, double b)
    {
        return a / b;
    }
}
```

`cref` 屬性代表可從目前編譯環境取得之例外狀況的參考。
這可以是專案或已參考組件中所定義的任何類型，如果無法解析其值，則編譯器會發出警告。

### <a name="ltseegt"></a>&lt;see&gt;

`<see>` 標記可讓您建立另一個程式碼項目之文件頁面的可按式連結。 在下一個範例中，我們將在兩個 `Add` 方法之間建立可按式連結。

```csharp
/*
    The main Math class
    Contains all methods for performing basic math functions
*/
/// <summary>
/// The main <c>Math</c> class.
/// Contains all methods for performing basic math functions.
/// </summary>
public class Math
{
    /// <summary>
    /// Adds two integers and returns the result.
    /// </summary>
    /// <returns>
    /// The sum of two integers.
    /// </returns>
    /// <example>
    /// <code>
    /// int c = Math.Add(4, 5);
    /// if (c > 10)
    /// {
    ///     Console.WriteLine(c);
    /// }
    /// </code>
    /// </example>
    /// <exception cref="System.OverflowException">Thrown when one parameter is max 
    /// and the other is greater than 0.</exception>
    /// See <see cref="Math.Add(double, double)"/> to add doubles.
    public static int Add(int a, int b)
    {
        if ((a == int.MaxValue && b > 0) || (b == int.MaxValue && a > 0))
            throw new System.OverflowException();

        return a + b;
    }

    /// <summary>
    /// Adds two doubles and returns the result.
    /// </summary>
    /// <returns>
    /// The sum of two doubles.
    /// </returns>
    /// <exception cref="System.OverflowException">Thrown when one parameter is max 
    /// and the other is greater than zero.</exception>
    /// See <see cref="Math.Add(int, int)"/> to add integers.
    public static double Add(double a, double b)
    {
        if ((a == double.MaxValue && b > 0) || (b == double.MaxValue && a > 0))
            throw new System.OverflowException();

        return a + b;
    }
}
```

`cref` 為**必要**屬性，代表可從目前編譯環境取得的類型或其成員的參考。 這可以是專案或已參考組件中所定義的任何類型。

### <a name="ltseealsogt"></a>&lt;seealso&gt;

`<seealso>` 標記的使用方式與 `<see>` 標記的使用方式相同。 唯一的差異在於它的內容一般會放在＜另請參閱＞一節中。 在這裡，我們將在整數 `Add` 方法上新增 `seealso` 標記，以參考類別中接受整數參數的其他方法：

```csharp
/*
    The main Math class
    Contains all methods for performing basic math functions
*/
/// <summary>
/// The main <c>Math</c> class.
/// Contains all methods for performing basic math functions.
/// </summary>
public class Math
{
    /// <summary>
    /// Adds two integers and returns the result.
    /// </summary>
    /// <returns>
    /// The sum of two integers.
    /// </returns>
    /// <example>
    /// <code>
    /// int c = Math.Add(4, 5);
    /// if (c > 10)
    /// {
    ///     Console.WriteLine(c);
    /// }
    /// </code>
    /// </example>
    /// <exception cref="System.OverflowException">Thrown when one parameter is max 
    /// and the other is greater than 0.</exception>
    /// See <see cref="Math.Add(double, double)"/> to add doubles.
    /// <seealso cref="Math.Subtract(int, int)"/>
    /// <seealso cref="Math.Multiply(int, int)"/>
    /// <seealso cref="Math.Divide(int, int)"/>
    public static int Add(int a, int b)
    {
        if ((a == int.MaxValue && b > 0) || (b == int.MaxValue && a > 0))
            throw new System.OverflowException();

        return a + b;
    }
}
```

`cref` 屬性代表可從目前編譯環境取得的類型或其成員的參考。
這可以是專案或已參考組件中所定義的任何類型。

### <a name="ltparamgt"></a>&lt;param&gt;

您可以使用 `<param>` 標記來描述方法的參數。 以下是雙 `Add` 方法的範例：標記所描述的屬性指定於**必要的** `name` 屬性中。

```csharp
/*
    The main Math class
    Contains all methods for performing basic math functions
*/
/// <summary>
/// The main <c>Math</c> class.
/// Contains all methods for performing basic math functions.
/// </summary>
public class Math
{
    /// <summary>
    /// Adds two doubles and returns the result.
    /// </summary>
    /// <returns>
    /// The sum of two doubles.
    /// </returns>
    /// <exception cref="System.OverflowException">Thrown when one parameter is max 
    /// and the other is greater than zero.</exception>
    /// See <see cref="Math.Add(int, int)"/> to add integers.
    /// <param name="a">A double precision number.</param>
    /// <param name="b">A double precision number.</param>
    public static double Add(double a, double b)
    {
        if ((a == double.MaxValue && b > 0) || (b == double.MaxValue && a > 0))
            throw new System.OverflowException();

        return a + b;
    }
}
```

### <a name="lttypeparamgt"></a>&lt;typeparam&gt;

您可以就像使用 `<param>` 標記一樣地使用 `<typeparam>` 標記，但針對泛型型別或方法宣告來描述泛型參數。
請繼續，並將快速泛型方法新增至 `Math` 類別，以檢查其中一個數量是否大於另一個數量。

```csharp
/*
    The main Math class
    Contains all methods for performing basic math functions
*/
/// <summary>
/// The main <c>Math</c> class.
/// Contains all methods for performing basic math functions.
/// </summary>
public class Math
{
    /// <summary>
    /// Checks if an IComparable is greater than another.
    /// </summary>
    /// <typeparam name="T">A type that inherits from the IComparable interface.</typeparam>
    public static bool GreaterThan<T>(T a, T b) where T : IComparable
    {
        return a.CompareTo(b) > 0;
    }
}
```

### <a name="ltparamrefgt"></a>&lt;paramref&gt;

您有時可能正在描述方法在 `<summary>` 標記中所執行的作業，而且您可能會想要參考參數，則 `<paramref>` 標記最適合這麼做。 讓我們更新雙 `Add` 方法的摘要。 與 `<param>` 標記類似，參數名稱指定於**必要的** `name` 屬性中。

```csharp
/*
    The main Math class
    Contains all methods for performing basic math functions
*/
/// <summary>
/// The main <c>Math</c> class.
/// Contains all methods for performing basic math functions.
/// </summary>
public class Math
{
    /// <summary>
    /// Adds two doubles <paramref name="a"/> and <paramref name="b"/> and returns the result.
    /// </summary>
    /// <returns>
    /// The sum of two doubles.
    /// </returns>
    /// <exception cref="System.OverflowException">Thrown when one parameter is max 
    /// and the other is greater than zero.</exception>
    /// See <see cref="Math.Add(int, int)"/> to add integers.
    /// <param name="a">A double precision number.</param>
    /// <param name="b">A double precision number.</param>
    public static double Add(double a, double b)
    {
        if ((a == double.MaxValue && b > 0) || (b == double.MaxValue && a > 0))
            throw new System.OverflowException();

        return a + b;
    }
}
```

### <a name="lttypeparamrefgt"></a>&lt;typeparamref&gt;

您可以就像使用 `<paramref>` 標記一樣地使用 `<typeparamref>` 標記，但針對泛型型別或方法宣告來描述泛型參數。
您可以使用先前建立的相同泛型方法。

```csharp
/*
    The main Math class
    Contains all methods for performing basic math functions
*/
/// <summary>
/// The main <c>Math</c> class.
/// Contains all methods for performing basic math functions.
/// </summary>
public class Math
{
    /// <summary>
    /// Checks if an IComparable <typeparamref name="T"/> is greater than another.
    /// </summary>
    /// <typeparam name="T">A type that inherits from the IComparable interface.</typeparam>
    public static bool GreaterThan<T>(T a, T b) where T : IComparable
    {
        return a.CompareTo(b) > 0;
    }
}
```

### <a name="ltlistgt"></a>&lt;list&gt;

您可以使用 `<list>` 標記，將文件資訊格式化為已排序清單、未排序清單或資料表。
您將建立 `Math` 程式庫所支援的未排序數學運算清單。

```csharp
/*
    The main Math class
    Contains all methods for performing basic math functions
*/
/// <summary>
/// The main <c>Math</c> class.
/// Contains all methods for performing basic math functions.
/// <list type="bullet">
/// <item>
/// <term>Add</term>
/// <description>Addition Operation</description>
/// </item>
/// <item>
/// <term>Subtract</term>
/// <description>Subtraction Operation</description>
/// </item>
/// <item>
/// <term>Multiply</term>
/// <description>Multiplication Operation</description>
/// </item>
/// <item>
/// <term>Divide</term>
/// <description>Division Operation</description>
/// </item>
/// </list>
/// </summary>
public class Math
{

}
```

您可以分別將 `type` 屬性變更為 `number` 或 `table`，以建立排序過的清單或表格。

### <a name="putting-it-all-together"></a>整體回顧

您已遵循本教學課程，並已在必要時將標記套用至程式碼，則程式碼現在看起來應該如下︰

```csharp
/*
    The main Math class
    Contains all methods for performing basic math functions
*/
/// <summary>
/// The main <c>Math</c> class.
/// Contains all methods for performing basic math functions.
/// <list type="bullet">
/// <item>
/// <term>Add</term>
/// <description>Addition Operation</description>
/// </item>
/// <item>
/// <term>Subtract</term>
/// <description>Subtraction Operation</description>
/// </item>
/// <item>
/// <term>Multiply</term>
/// <description>Multiplication Operation</description>
/// </item>
/// <item>
/// <term>Divide</term>
/// <description>Division Operation</description>
/// </item>
/// </list>
/// </summary>
/// <remarks>
/// <para>This class can add, subtract, multiply and divide.</para>
/// <para>These operations can be performed on both integers and doubles.</para>
/// </remarks>
public class Math
{
    // Adds two integers and returns the result
    /// <summary>
    /// Adds two integers <paramref name="a"/> and <paramref name="b"/> and returns the result.
    /// </summary>
    /// <returns>
    /// The sum of two integers.
    /// </returns>
    /// <example>
    /// <code>
    /// int c = Math.Add(4, 5);
    /// if (c > 10)
    /// {
    ///     Console.WriteLine(c);
    /// }
    /// </code>
    /// </example>
    /// <exception cref="System.OverflowException">Thrown when one parameter is max 
    /// and the other is greater than 0.</exception>
    /// See <see cref="Math.Add(double, double)"/> to add doubles.
    /// <seealso cref="Math.Subtract(int, int)"/>
    /// <seealso cref="Math.Multiply(int, int)"/>
    /// <seealso cref="Math.Divide(int, int)"/>
    /// <param name="a">An integer.</param>
    /// <param name="b">An integer.</param>
    public static int Add(int a, int b)
    {
        // If any parameter is equal to the max value of an integer
        // and the other is greater than zero
        if ((a == int.MaxValue && b > 0) || (b == int.MaxValue && a > 0))
            throw new System.OverflowException();

        return a + b;
    }

    // Adds two doubles and returns the result
    /// <summary>
    /// Adds two doubles <paramref name="a"/> and <paramref name="b"/> and returns the result.
    /// </summary>
    /// <returns>
    /// The sum of two doubles.
    /// </returns>
    /// <example>
    /// <code>
    /// double c = Math.Add(4.5, 5.4);
    /// if (c > 10)
    /// {
    ///     Console.WriteLine(c);
    /// }
    /// </code>
    /// </example>
    /// <exception cref="System.OverflowException">Thrown when one parameter is max 
    /// and the other is greater than 0.</exception>
    /// See <see cref="Math.Add(int, int)"/> to add integers.
    /// <seealso cref="Math.Subtract(double, double)"/>
    /// <seealso cref="Math.Multiply(double, double)"/>
    /// <seealso cref="Math.Divide(double, double)"/>
    /// <param name="a">A double precision number.</param>
    /// <param name="b">A double precision number.</param>
    public static double Add(double a, double b)
    {
        // If any parameter is equal to the max value of an integer
        // and the other is greater than zero
        if ((a == double.MaxValue && b > 0) || (b == double.MaxValue && a > 0))
            throw new System.OverflowException();

        return a + b;
    }

    // Subtracts an integer from another and returns the result
    /// <summary>
    /// Subtracts <paramref name="b"/> from <paramref name="a"/> and returns the result.
    /// </summary>
    /// <returns>
    /// The difference between two integers.
    /// </returns>
    /// <example>
    /// <code>
    /// int c = Math.Subtract(4, 5);
    /// if (c > 1)
    /// {
    ///     Console.WriteLine(c);
    /// }
    /// </code>
    /// </example>
    /// See <see cref="Math.Subtract(double, double)"/> to subtract doubles.
    /// <seealso cref="Math.Add(int, int)"/>
    /// <seealso cref="Math.Multiply(int, int)"/>
    /// <seealso cref="Math.Divide(int, int)"/>
    /// <param name="a">An integer.</param>
    /// <param name="b">An integer.</param>
    public static int Subtract(int a, int b)
    {
        return a - b;
    }

    // Subtracts a double from another and returns the result
    /// <summary>
    /// Subtracts a double <paramref name="b"/> from another double <paramref name="a"/> and returns the result.
    /// </summary>
    /// <returns>
    /// The difference between two doubles.
    /// </returns>
    /// <example>
    /// <code>
    /// double c = Math.Subtract(4.5, 5.4);
    /// if (c > 1)
    /// {
    ///     Console.WriteLine(c);
    /// }
    /// </code>
    /// </example>
    /// See <see cref="Math.Subtract(int, int)"/> to subtract integers.
    /// <seealso cref="Math.Add(double, double)"/>
    /// <seealso cref="Math.Multiply(double, double)"/>
    /// <seealso cref="Math.Divide(double, double)"/>
    /// <param name="a">A double precision number.</param>
    /// <param name="b">A double precision number.</param>
    public static double Subtract(double a, double b)
    {
        return a - b;
    }

    // Multiplies two integers and returns the result
    /// <summary>
    /// Multiplies two integers <paramref name="a"/> and <paramref name="b"/> and returns the result.
    /// </summary>
    /// <returns>
    /// The product of two integers.
    /// </returns>
    /// <example>
    /// <code>
    /// int c = Math.Multiply(4, 5);
    /// if (c > 100)
    /// {
    ///     Console.WriteLine(c);
    /// }
    /// </code>
    /// </example>
    /// See <see cref="Math.Multiply(double, double)"/> to multiply doubles.
    /// <seealso cref="Math.Add(int, int)"/>
    /// <seealso cref="Math.Subtract(int, int)"/>
    /// <seealso cref="Math.Divide(int, int)"/>
    /// <param name="a">An integer.</param>
    /// <param name="b">An integer.</param>
    public static int Multiply(int a, int b)
    {
        return a * b;
    }

    // Multiplies two doubles and returns the result
    /// <summary>
    /// Multiplies two doubles <paramref name="a"/> and <paramref name="b"/> and returns the result.
    /// </summary>
    /// <returns>
    /// The product of two doubles.
    /// </returns>
    /// <example>
    /// <code>
    /// double c = Math.Multiply(4.5, 5.4);
    /// if (c > 100.0)
    /// {
    ///     Console.WriteLine(c);
    /// }
    /// </code>
    /// </example>
    /// See <see cref="Math.Multiply(int, int)"/> to multiply integers.
    /// <seealso cref="Math.Add(double, double)"/>
    /// <seealso cref="Math.Subtract(double, double)"/>
    /// <seealso cref="Math.Divide(double, double)"/>
    /// <param name="a">A double precision number.</param>
    /// <param name="b">A double precision number.</param>
    public static double Multiply(double a, double b)
    {
        return a * b;
    }

    // Divides an integer by another and returns the result
    /// <summary>
    /// Divides an integer <paramref name="a"/> by another integer <paramref name="b"/> and returns the result.
    /// </summary>
    /// <returns>
    /// The quotient of two integers.
    /// </returns>
    /// <example>
    /// <code>
    /// int c = Math.Divide(4, 5);
    /// if (c > 1)
    /// {
    ///     Console.WriteLine(c);
    /// }
    /// </code>
    /// </example>
    /// <exception cref="System.DivideByZeroException">Thrown when <paramref name="b"/> is equal to 0.</exception>
    /// See <see cref="Math.Divide(double, double)"/> to divide doubles.
    /// <seealso cref="Math.Add(int, int)"/>
    /// <seealso cref="Math.Subtract(int, int)"/>
    /// <seealso cref="Math.Multiply(int, int)"/>
    /// <param name="a">An integer dividend.</param>
    /// <param name="b">An integer divisor.</param>
    public static int Divide(int a, int b)
    {
        return a / b;
    }

    // Divides a double by another and returns the result
    /// <summary>
    /// Divides a double <paramref name="a"/> by another double <paramref name="b"/> and returns the result.
    /// </summary>
    /// <returns>
    /// The quotient of two doubles.
    /// </returns>
    /// <example>
    /// <code>
    /// double c = Math.Divide(4.5, 5.4);
    /// if (c > 1.0)
    /// {
    ///     Console.WriteLine(c);
    /// }
    /// </code>
    /// </example>
    /// See <see cref="Math.Divide(int, int)"/> to divide integers.
    /// <seealso cref="Math.Add(double, double)"/>
    /// <seealso cref="Math.Subtract(double, double)"/>
    /// <seealso cref="Math.Multiply(double, double)"/>
    /// <param name="a">A double precision dividend.</param>
    /// <param name="b">A double precision divisor.</param>
    public static double Divide(double a, double b)
    {
        return a / b;
    }
}
```

從您的程式碼中，您可以產生具有可按式交叉參考的詳細文件網站，但接著您會面臨另一個問題，您的程式碼已變成難以閱讀。
如果開發人員想要參與這個程式碼，因而需要仔細檢查太多資訊，則這會是個夢魘。 還好有 XML 標記可協助您處理這個問題︰

### <a name="ltincludegt"></a>&lt;include&gt;

`<include>` 標記可讓您參考個別 XML 檔案中描述原始程式碼中類型和成員的註解，這與直接在原始程式碼檔中放置文件註解相反。

您現在要將所有 XML 標記移至名為 `docs.xml` 的個別 XML 檔案。 請放心以您想要的名稱來命名檔案。

```xml
<docs>
    <members name="math">
        <Math>
            <summary>
            The main <c>Math</c> class.
            Contains all methods for performing basic math functions.
            </summary>
            <remarks>
            <para>This class can add, subtract, multiply and divide.</para>
            <para>These operations can be performed on both integers and doubles.</para>
            </remarks>
        </Math>
        <AddInt>
            <summary>
            Adds two integers <paramref name="a"/> and <paramref name="b"/> and returns the result.
            </summary>
            <returns>
            The sum of two integers.
            </returns>
            <example>
            <code>
            int c = Math.Add(4, 5);
            if (c > 10)
            {
                Console.WriteLine(c);
            }
            </code>
            </example>
            <exception cref="System.OverflowException">Thrown when one parameter is max 
            and the other is greater than 0.</exception>
            See <see cref="Math.Add(double, double)"/> to add doubles.
            <seealso cref="Math.Subtract(int, int)"/>
            <seealso cref="Math.Multiply(int, int)"/>
            <seealso cref="Math.Divide(int, int)"/>
            <param name="a">An integer.</param>
            <param name="b">An integer.</param>
        </AddInt>
        <AddDouble>
            <summary>
            Adds two doubles <paramref name="a"/> and <paramref name="b"/> and returns the result.
            </summary>
            <returns>
            The sum of two doubles.
            </returns>
            <example>
            <code>
            double c = Math.Add(4.5, 5.4);
            if (c > 10)
            {
                Console.WriteLine(c);
            }
            </code>
            </example>
            <exception cref="System.OverflowException">Thrown when one parameter is max 
            and the other is greater than 0.</exception>
            See <see cref="Math.Add(int, int)"/> to add integers.
            <seealso cref="Math.Subtract(double, double)"/>
            <seealso cref="Math.Multiply(double, double)"/>
            <seealso cref="Math.Divide(double, double)"/>
            <param name="a">A double precision number.</param>
            <param name="b">A double precision number.</param>
        </AddDouble>
        <SubtractInt>
            <summary>
            Subtracts <paramref name="b"/> from <paramref name="a"/> and returns the result.
            </summary>
            <returns>
            The difference between two integers.
            </returns>
            <example>
            <code>
            int c = Math.Subtract(4, 5);
            if (c > 1)
            {
                Console.WriteLine(c);
            }
            </code>
            </example>
            See <see cref="Math.Subtract(double, double)"/> to subtract doubles.
            <seealso cref="Math.Add(int, int)"/>
            <seealso cref="Math.Multiply(int, int)"/>
            <seealso cref="Math.Divide(int, int)"/>
            <param name="a">An integer.</param>
            <param name="b">An integer.</param>
        </SubtractInt>
        <SubtractDouble>
            <summary>
            Subtracts a double <paramref name="b"/> from another double <paramref name="a"/> and returns the result.
            </summary>
            <returns>
            The difference between two doubles.
            </returns>
            <example>
            <code>
            double c = Math.Subtract(4.5, 5.4);
            if (c > 1)
            {
                Console.WriteLine(c);
            }
            </code>
            </example>
            See <see cref="Math.Subtract(int, int)"/> to subtract integers.
            <seealso cref="Math.Add(double, double)"/>
            <seealso cref="Math.Multiply(double, double)"/>
            <seealso cref="Math.Divide(double, double)"/>
            <param name="a">A double precision number.</param>
            <param name="b">A double precision number.</param>
        </SubtractDouble>
        <MultiplyInt>
            <summary>
            Multiplies two integers <paramref name="a"/> and <paramref name="b"/> and returns the result.
            </summary>
            <returns>
            The product of two integers.
            </returns>
            <example>
            <code>
            int c = Math.Multiply(4, 5);
            if (c > 100)
            {
                Console.WriteLine(c);
            }
            </code>
            </example>
            See <see cref="Math.Multiply(double, double)"/> to multiply doubles.
            <seealso cref="Math.Add(int, int)"/>
            <seealso cref="Math.Subtract(int, int)"/>
            <seealso cref="Math.Divide(int, int)"/>
            <param name="a">An integer.</param>
            <param name="b">An integer.</param>
        </MultiplyInt>
        <MultiplyDouble>
            <summary>
            Multiplies two doubles <paramref name="a"/> and <paramref name="b"/> and returns the result.
            </summary>
            <returns>
            The product of two doubles.
            </returns>
            <example>
            <code>
            double c = Math.Multiply(4.5, 5.4);
            if (c > 100.0)
            {
                Console.WriteLine(c);
            }
            </code>
            </example>
            See <see cref="Math.Multiply(int, int)"/> to multiply integers.
            <seealso cref="Math.Add(double, double)"/>
            <seealso cref="Math.Subtract(double, double)"/>
            <seealso cref="Math.Divide(double, double)"/>
            <param name="a">A double precision number.</param>
            <param name="b">A double precision number.</param>
        </MultiplyDouble>
        <DivideInt>
            <summary>
            Divides an integer <paramref name="a"/> by another integer <paramref name="b"/> and returns the result.
            </summary>
            <returns>
            The quotient of two integers.
            </returns>
            <example>
            <code>
            int c = Math.Divide(4, 5);
            if (c > 1)
            {
                Console.WriteLine(c);
            }
            </code>
            </example>
            <exception cref="System.DivideByZeroException">Thrown when <paramref name="b"/> is equal to 0.</exception>
            See <see cref="Math.Divide(double, double)"/> to divide doubles.
            <seealso cref="Math.Add(int, int)"/>
            <seealso cref="Math.Subtract(int, int)"/>
            <seealso cref="Math.Multiply(int, int)"/>
            <param name="a">An integer dividend.</param>
            <param name="b">An integer divisor.</param>
        </DivideInt>
        <DivideDouble>
            <summary>
            Divides a double <paramref name="a"/> by another double <paramref name="b"/> and returns the result.
            </summary>
            <returns>
            The quotient of two doubles.
            </returns>
            <example>
            <code>
            double c = Math.Divide(4.5, 5.4);
            if (c > 1.0)
            {
                Console.WriteLine(c);
            }
            </code>
            </example>
            See <see cref="Math.Divide(int, int)"/> to divide integers.
            <seealso cref="Math.Add(double, double)"/>
            <seealso cref="Math.Subtract(double, double)"/>
            <seealso cref="Math.Multiply(double, double)"/>
            <param name="a">A double precision dividend.</param>
            <param name="b">A double precision divisor.</param>
        </DivideDouble>
    </members>
</docs>
```

在上述 XML 中，每個成員的文件註解都會直接顯示在執行動作之後所命名的標記內。 您可以選擇自己的策略。 現在，您的 XML 註解位於在不同的檔案中，請查看如何使用 `<include>` 標記讓您的程式碼更容易閱讀：

```csharp
/*
    The main Math class
    Contains all methods for performing basic math functions
*/
/// <include file='docs.xml' path='docs/members[@name="math"]/Math/*'/>
public class Math
{
    // Adds two integers and returns the result
    /// <include file='docs.xml' path='docs/members[@name="math"]/AddInt/*'/>
    public static int Add(int a, int b)
    {
        // If any parameter is equal to the max value of an integer
        // and the other is greater than zero
        if ((a == int.MaxValue && b > 0) || (b == int.MaxValue && a > 0))
            throw new System.OverflowException();

        return a + b;
    }

    // Adds two doubles and returns the result
    /// <include file='docs.xml' path='docs/members[@name="math"]/AddDouble/*'/>
    public static double Add(double a, double b)
    {
        // If any parameter is equal to the max value of an integer
        // and the other is greater than zero
        if ((a == double.MaxValue && b > 0) || (b == double.MaxValue && a > 0))
            throw new System.OverflowException();

        return a + b;
    }

    // Subtracts an integer from another and returns the result
    /// <include file='docs.xml' path='docs/members[@name="math"]/SubtractInt/*'/>
    public static int Subtract(int a, int b)
    {
        return a - b;
    }

    // Subtracts a double from another and returns the result
    /// <include file='docs.xml' path='docs/members[@name="math"]/SubtractDouble/*'/>
    public static double Subtract(double a, double b)
    {
        return a - b;
    }

    // Multiplies two integers and returns the result
    /// <include file='docs.xml' path='docs/members[@name="math"]/MultiplyInt/*'/>
    public static int Multiply(int a, int b)
    {
        return a * b;
    }

    // Multiplies two doubles and returns the result
    /// <include file='docs.xml' path='docs/members[@name="math"]/MultiplyDouble/*'/>
    public static double Multiply(double a, double b)
    {
        return a * b;
    }

    // Divides an integer by another and returns the result
    /// <include file='docs.xml' path='docs/members[@name="math"]/DivideInt/*'/>
    public static int Divide(int a, int b)
    {
        return a / b;
    }

    // Divides a double by another and returns the result
    /// <include file='docs.xml' path='docs/members[@name="math"]/DivideDouble/*'/>
    public static double Divide(double a, double b)
    {
        return a / b;
    }
}
```

目前您已經準備好了：我們的程式碼又再次為可讀，而且未遺失文件資訊。 

`filename` 屬性代表包含文件的 XML 檔案名稱。

`path` 屬性代表存在於所指定 `filename` 中之 `tag name` 的 [XPath](https://msdn.microsoft.com/library/ms256115.aspx) 查詢。

`name` 屬性代表標記中位在註解前面的名稱規範。

可用來取代 `name` 的 `id` 屬性代表位在註解前面之標記的識別碼。

### <a name="user-defined-tags"></a>使用者定義標記

以上所述的所有標記都代表 C# 編譯器所辨識的標記。 不過，使用者可以定義自己的標記。
Sandcastle 這類工具會支援 [`<event>`](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm)、[`<note>`](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) 甚至支援 [documenting namespaces](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm) (記錄命名空間) 這類額外標記。
自訂或內部文件產生工具也可以與標準標記搭配使用，而且可以支援從 HTML 到 PDF 的多個輸出格式。

## <a name="recommendations"></a>建議

有許多原因，建議您記錄程式碼。 接下來是一些最佳做法、一般使用案例，以及在 C# 程式碼中使用 XML 文件標記時應該知道的事項。

* 為保持一致性，應該記錄所有公開可見的類型和其成員。 如果您必須執行它，則請執行。
* 也可以使用 XML 註解記錄私用成員。 不過，這樣會公開您程式庫的內部 (可能是機密) 運作。
* 類型和其成員最少應該具有 `<summary>` 標記，因為 IntelliSense 需要其內容。
* 應該使用結尾為句號的完整句子來撰寫文件文字。
* 完全支援部分類別，而且文件資訊將會串連為該類型的單一項目。
* 編譯器會驗證 `<exception>`、`<include>`、`<param>`、`<see>`、`<seealso>` 和 `<typeparam>` 標記的語法。
- 編譯器會驗證包含程式碼其他部分的檔案路徑和參考的參數。

## <a name="see-also"></a>請參閱
[XML 文件註解 (C# 程式設計手冊)](programming-guide/xmldoc/xml-documentation-comments.md)

[建議使用的文件註解標記 (C# 程式設計手冊)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

