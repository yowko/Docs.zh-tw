---
title: Managed Extensibility Framework (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Managed Extensibility Framework, overview
- MEF, overview
ms.assetid: 6c61b4ec-c6df-4651-80f1-4854f8b14dde
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fa91b6f2866ba2dee6963d7258fe193ce058f61
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457177"
---
# <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

本主題提供 .NET Framework 4 中所引入 Managed Extensibility Framework 的概觀。

<a name="what_is_mef"></a>
## <a name="what-is-mef"></a>什麼是 MEF？

Managed Extensibility Framework 或 MEF 是用來建立輕量型可擴充應用程式的程式庫。 它可讓應用程式開發人員探索和使用擴充功能，而不需要任何組態。 它也可以讓擴充功能開發人員輕鬆地封裝程式碼，並避免易損壞的硬式相依性。 MEF 不只允許在應用程式內重複使用擴充功能，也允許跨應用程式重複使用擴充功能。

<a name="the_problem_of_extensibility"></a>
## <a name="the-problem-of-extensibility"></a>擴充性問題
 假設您是必須提供擴充性支援的大型應用程式架構設計人員。 您的應用程式必須包含大量的較小元件，而且會負責建立和執行元件。

 問題最簡單的解決方式是包含元件做為應用程式中的原始程式碼，並直接從程式碼呼叫它們。 以下為一些明顯的缺點。 最重要的是，您需要修改原始程式碼才能新增元件，舉例來說，在 Web 應用程式中可能可以接受的限制，在用戶端應用程式中卻是無法作用的限制。 同樣有問題的地方在於，因為元件可能由協力廠商所開發，所以您可能無法存取元件的原始碼，且基於相同的原因，您也不允許協力廠商存取您元件的原始碼。

 稍微複雜一點的方法是提供擴充點或介面，以允許應用程式與其元件之間的去耦合。 在此模型中，您可能會提供元件可以實作的介面，以及提供 API 讓它與您的應用程式互動。 這樣可以解決需要原始程式碼存取權的問題，但仍有其困難度。

 因為應用程式沒有任何能力可以自行探索元件，所以還是必須明確告知可用以及應該載入的元件。 這通常是透過在組態檔中明確地註冊可用的元件來達成。 這就表示，確保元件正確已成為維護問題，特別是當它是使用者，而不是預期進行更新的開發人員時。

 此外，元件無法彼此通訊，但透過應用程式本身嚴格定義的通道除外。 如果應用程式架構設計人員不需要進行特定通訊，通常是不可能辦到的。

 最後，元件開發人員必須接受哪一個組件包含他們所實作之介面的硬式相依性。 這樣很難在多個應用程式中使用元件，也可能會在建立元件的測試架構時產生問題。

<a name="what_mef_provides"></a>
## <a name="what-mef-provides"></a>MEF 提供的內容
 MEF 提供方法以透過「組合」  隱含地探索可用元件，而不是明確地註冊可用元件。 MEF 元件 (稱為「組件」  ) 會以宣告方式指定其相依性 (稱為「匯入」  ) 及其提供的功能 (稱為「匯出」  )。 建立組件時，MEF 組合引擎可滿足具有從其他組件取得之內容的匯入。

 這種方法解決前一節所討論的問題。 因為 MEF 組件是以宣告方式指定其功能，所以可以在執行階段找到它們，這表示應用程式可以使用組件，而不需要硬式編碼參考或易損壞的組態檔。 MEF 允許應用程式透過它們的中繼資料來探索和檢查組件 (part)，而不需要具現化應用程式，或甚至載入其組件 (assembly)。 因此，不需要仔細地指定何時以及應該如何載入擴充功能。

 除了它所提供的匯出之外，組件可以指定其匯入 (將會填入其他組件)。 這不只可讓組件之間進行通訊，而且十分簡單，並允許進行不錯的程式碼分解。 例如，許多元件通用的服務可以分解為個別的組件，而且可以輕鬆地修改或取代。

 因為 MEF 模型不需要對特定應用程式組件產生硬式相依性，所以允許在不同的應用程式之間重複使用擴充功能。 這也能讓您輕鬆地開發測試載入器 (與應用程式無關) 以測試擴充功能元件。

 使用 MEF 所撰寫的可延伸應用程式會宣告可填入擴充功能元件的匯入，也可以宣告匯出以向擴充功能公開應用程式服務。 每個擴充功能元件都會宣告匯出，也可能會宣告匯入。 如此一來，擴充功能元件本身是可自動擴充的。

<a name="where_is_mef_available"></a>
## <a name="where-is-mef-available"></a>MEF 可在哪裡使用？
 MEF 是 .NET Framework 4 不可或缺的部分，而且只要使用.NET Framework 就可以使用 MEF。 在使用 Windows Forms、WPF 或任何其他技術的用戶端應用程式中，還是在使用 ASP.NET 的伺服器應用程式中，您都可以使用 MEF。

<a name="mef_and_maf"></a>
## <a name="mef-and-maf"></a>MEF 和 MAF
 舊版 .NET Framework 已引入管理增益集架構 (MAF)，設計為允許應用程式隔離和管理擴充功能。 MAF 的焦點在層次上略高於 MEF，專注於擴充功能隔離以及組件載入和卸載，而 MEF 的焦點在於可搜尋性、擴充性和可攜性。 這兩個架構可以順利地交互操作，而且兩者皆可為單一應用程式所用。

<a name="simplecalculator_an_example_application"></a>

## <a name="simplecalculator-an-example-application"></a>SimpleCalculator：應用程式範例

了解 MEF 用途的最簡單方式是建置一個簡單的 MEF 應用程式。 在這個範例中，您建置一個十分簡單的計算機 (名稱為 SimpleCalculator)。 SimpleCalculator 的目標是建立一個接受基本算術命令 (格式為 "5+3" 或 "6-2") 的主控台應用程式，並傳回正確的答案。 使用 MEF，您可以新增運算子，而不需要變更應用程式程式碼。

若要下載這個範例的完整程式碼，請參閱 [SimpleCalculator 範例](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e) \(英文\)。

> [!NOTE]
> SimpleCalculator 的目的是示範 MEF 的概念和語法，不一定會提供其實際使用案例。 許多從 MEF 功能獲得最多益處的應用程式，比 SimpleCalculator 更為複雜。 如需更多範例，請參閱 GitHub 上的 [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) \(英文\)。

- 若要開始，請在 Visual Studio 中建立新的主控台應用程式專案，並且將它命名為 `SimpleCalculator`。

- 將參考加入 MEF 所在的 System.ComponentModel.Composition 組件。

- 開啟 Module1.vb 或 Program.cs，然後針對 System.ComponentModel.Composition 和 System.ComponentModel.Composition.Hosting 加入 `Imports` 或 `using` 陳述式。 這兩個命名空間都包含開發可延伸應用程式所需的 MEF 類型。

- 如果您使用 Visual Basic，請將 `Public` 關鍵字新增至宣告 `Module1` 模組的行。

<a name="composition_container_and_catalogs"></a>

## <a name="composition-container-and-catalogs"></a>組合容器和目錄

MEF 組合模型的核心是「組合容器」  ，其中包含所有可用的組件並執行組合。 組合會將匯入往上對應至匯出。 最常見的組合容器類型是 <xref:System.ComponentModel.Composition.Hosting.CompositionContainer>，而且您會將它用於 SimpleCalculator。

如果您使用 Visual Basic，請在 Module1.vb 中新增名稱為 `Program` 的公用類別。

將下列的行新增至 Module1.vb 或 Program.cs 中的 `Program` 類別：

```vb
Dim _container As CompositionContainer
```

```csharp
private CompositionContainer _container;
```

為了要探索可供組合容器使用的組件，組合容器會利用「目錄」  。 目錄是可從某個來源探索到可用組件的物件。 MEF 提供目錄 (catalog)，以從提供的類型、組件 (assembly) 或目錄 (directory) 探索組件 (part)。 應用程式開發人員可以輕鬆地建立新的目錄，以從其他來源 (例如 Web 服務) 探索組件。

將下列建構函式加入 `Program` 類別：

```vb
Public Sub New()
    'An aggregate catalog that combines multiple catalogs
     Dim catalog = New AggregateCatalog()

    'Adds all the parts found in the same assembly as the Program class
    catalog.Catalogs.Add(New AssemblyCatalog(GetType(Program).Assembly))

    'Create the CompositionContainer with the parts in the catalog
    _container = New CompositionContainer(catalog)

    'Fill the imports of this object
    Try
        _container.ComposeParts(Me)
    Catch ex As Exception
        Console.WriteLine(ex.ToString)
    End Try
End Sub
```

```csharp
private Program()
{
    //An aggregate catalog that combines multiple catalogs
    var catalog = new AggregateCatalog();
    //Adds all the parts found in the same assembly as the Program class
    catalog.Catalogs.Add(new AssemblyCatalog(typeof(Program).Assembly));

    //Create the CompositionContainer with the parts in the catalog
    _container = new CompositionContainer(catalog);

    //Fill the imports of this object
    try
    {
        this._container.ComposeParts(this);
    }
    catch (CompositionException compositionException)
    {
        Console.WriteLine(compositionException.ToString());
   }
}
```

<xref:System.ComponentModel.Composition.AttributedModelServices.ComposeParts%2A> 呼叫會告知組合容器撰寫一組特定的組件，在此情況下是目前的 `Program` 執行個體。 不過，此時不會發生任何事，因為 `Program` 沒有要填入的匯入。

<a name="imports_and_exports_with_attributes"></a>
## <a name="imports-and-exports-with-attributes"></a>含屬性的匯入和匯出
 首先，您讓 `Program` 匯入計算機。 這允許使用者介面考量 (例如將進入 `Program` 的主控台輸入和輸出) 與計算機的邏輯分隔。

 將下列程式碼加入 `Program` 類別：

```vb
<Import(GetType(ICalculator))>
Public Property calculator As ICalculator
```

```csharp
[Import(typeof(ICalculator))]
public ICalculator calculator;
```

 請注意，`calculator` 物件的宣告不是異常，而是它使用 <xref:System.ComponentModel.Composition.ImportAttribute> 屬性裝飾。 這個屬性會將某個項目宣告為匯入；也就是撰寫物件時，組合引擎將會填入它。

 每個匯入都有「合約」  ，其會決定將與其相符的匯出。 合約可以是明確指定的字串，也可以由 MEF 透過指定類型自動產生，在此情況下為 `ICalculator` 介面。 任何已宣告相符合約的匯出都滿足此匯入。 請注意，`calculator` 物件的類型事際上是 `ICalculator` 時，這不是必要項目。 合約與匯入中物件的類型無關 (在此情況下，您可以遺漏 `typeof(ICalculator)`。 除非您明確地指定合約，否則 MEF 將會自動假設合約是根據匯入的類型。)

 請將這個非常簡單的介面加入模組或 `SimpleCalculator` 命名空間：

```vb
Public Interface ICalculator
    Function Calculate(ByVal input As String) As String
End Interface
```

```csharp
public interface ICalculator
{
    String Calculate(String input);
}
```

 既然您已定義 `ICalculator`，您需要實作它的類別。 將下列類別加入模組或 `SimpleCalculator` 命名空間：

```vb
<Export(GetType(ICalculator))>
Public Class MySimpleCalculator
   Implements ICalculator

End Class
```

```csharp
[Export(typeof(ICalculator))]
class MySimpleCalculator : ICalculator
{

}
```

 以下是符合 `Program` 中匯入的匯出。 若要讓匯出符合匯入，匯出必須具有相同的合約。 按照以 `typeof(MySimpleCalculator)` 為根據的合約，匯出會產生不相符的情況，而且不會填入匯入；合約必須完全相符。

 因為組合容器將會填入這個組件 (assembly) 中可用的所有組件 (part)，所以將可以使用 `MySimpleCalculator` 組件 (part)。 `Program` 的建構函式對 `Program` 物件執行組合時，其匯入將會填入針對該用途所建立的 `MySimpleCalculator` 物件。

 使用者介面層 (`Program`) 不需要知道任何其他項目。 因此，您可以在 `Main` 方法中填入其餘的使用者介面邏輯。

 將下列程式碼加入 `Main` 方法：

```vb
Sub Main()
    Dim p As New Program()
    Dim s As String
    Console.WriteLine("Enter Command:")
    While (True)
        s = Console.ReadLine()
        Console.WriteLine(p.calculator.Calculate(s))
    End While
End Sub
```

```csharp
static void Main(string[] args)
{
    Program p = new Program(); //Composition is performed in the constructor
    String s;
    Console.WriteLine("Enter Command:");
    while (true)
    {
        s = Console.ReadLine();
        Console.WriteLine(p.calculator.Calculate(s));
    }
}
```

 此程式碼只會讀取一行輸入，並針對結果呼叫 `Calculate` 的 `ICalculator` 函式，以將結果寫回主控台。 這是 `Program` 中您需要的所有程式碼。 所有其餘的工作將在組件中進行。

<a name="further_imports_and_importmany"></a>
## <a name="further-imports-and-importmany"></a>進一步匯入和 ImportMany
 為了讓 SimpleCalculator 可延伸，它需要匯入作業的清單。 一般 <xref:System.ComponentModel.Composition.ImportAttribute> 屬性只會填入一個 <xref:System.ComponentModel.Composition.ExportAttribute>。 如果有多個可用，組合引擎就會產生錯誤。 若要建立可以填入任意數目匯出的匯入，您可以使用 <xref:System.ComponentModel.Composition.ImportManyAttribute> 屬性。

 將下列作業屬性加入至 `MySimpleCalculator` 類別：

```vb
<ImportMany()>
Public Property operations As IEnumerable(Of Lazy(Of IOperation, IOperationData))
```

```csharp
[ImportMany]
IEnumerable<Lazy<IOperation, IOperationData>> operations;
```

 <xref:System.Lazy%602> 是 MEF 所提供的類型，用於保留要匯出的間接參考。 在這裡，除了匯出的物件本身之外，您也會取得「匯出中繼資料」  或描述所匯出物件的資訊。 每個 <xref:System.Lazy%602> 都會包含代表實際作業的 `IOperation` 物件以及代表其中繼資料的 `IOperationData` 物件。

 將下列簡單的介面加入模組或 `SimpleCalculator` 命名空間：

```vb
Public Interface IOperation
    Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer
End Interface

Public Interface IOperationData
    ReadOnly Property Symbol As Char
End Interface
```

```csharp
public interface IOperation
{
     int Operate(int left, int right);
}

public interface IOperationData
{
    Char Symbol { get; }
}
```

 在此情況下，每個運算的中繼資料都是代表該運算的符號 (例如 +、-、* 等)。 若要使用加法運算，請將下列類別加入模組或 `SimpleCalculator` 命名空間：

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "+"c)>
Public Class Add
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left + right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '+')]
class Add: IOperation
{
    public int Operate(int left, int right)
    {
        return left + right;
    }
}
```

 <xref:System.ComponentModel.Composition.ExportAttribute> 屬性的運作與以前一樣。 <xref:System.ComponentModel.Composition.ExportMetadataAttribute> 屬性會將中繼資料 (以名稱/值組的形式) 附加至該匯出。 雖然 `Add` 類別實作 `IOperation`，但是未明確地定義可實作 `IOperationData` 的類別。 相反地，類別由 MEF 所隱含建立，其屬性以提供的中繼資料名稱為基礎。 (這是在 MEF 存取中繼資料的數種方式中的一種。)

 MEF 中的組合是「遞迴的」  。 您已明確地撰寫 `Program` 物件，這樣會匯入結果為 `ICalculator` 類型的 `MySimpleCalculator`。 `MySimpleCalculator` 接著會匯入 `IOperation` 物件的集合，而且將會在建立 `MySimpleCalculator` 時填入該匯入，與 `Program` 匯入同時。 如果 `Add` 類別已宣告進一步的匯入，則也必須予以填入，以此類推。 任何未填入的匯入都會導致組合錯誤。 (不過，可能會將匯入宣告為選擇性，或指派預設值給它們。)

<a name="calculator_logic"></a>
## <a name="calculator-logic"></a>計算機邏輯
 這些組件都就緒之後，剩下的就是計算機邏輯本身。 在 `MySimpleCalculator` 類別中加入下列程式碼，以實作 `Calculate` 方法：

```vb
Public Function Calculate(ByVal input As String) As String Implements ICalculator.Calculate
    Dim left, right As Integer
    Dim operation As Char
    Dim fn = FindFirstNonDigit(input) 'Finds the operator
    If fn < 0 Then
        Return "Could not parse command."
    End If
    operation = input(fn)
    Try
        left = Integer.Parse(input.Substring(0, fn))
        right = Integer.Parse(input.Substring(fn + 1))
    Catch ex As Exception
        Return "Could not parse command."
    End Try
    For Each i As Lazy(Of IOperation, IOperationData) In operations
        If i.Metadata.symbol = operation Then
            Return i.Value.Operate(left, right).ToString()
        End If
    Next
    Return "Operation not found!"
End Function
```

```csharp
public String Calculate(String input)
{
    int left;
    int right;
    Char operation;
    int fn = FindFirstNonDigit(input); //finds the operator
    if (fn < 0) return "Could not parse command.";

    try
    {
        //separate out the operands
        left = int.Parse(input.Substring(0, fn));
        right = int.Parse(input.Substring(fn + 1));
    }
    catch
    {
        return "Could not parse command.";
    }

    operation = input[fn];

    foreach (Lazy<IOperation, IOperationData> i in operations)
    {
        if (i.Metadata.Symbol.Equals(operation)) return i.Value.Operate(left, right).ToString();
    }
    return "Operation Not Found!";
}
```

 初始步驟會將輸入字串剖析為左運算元、右運算元和一個運算子字元。 在 `foreach` 迴圈中，會檢查 `operations` 集合的每個成員。 這些物件的類型為 <xref:System.Lazy%602>，而且分別可以使用 <xref:System.Lazy%602.Metadata%2A> 屬性和 <xref:System.Lazy%601.Value%2A> 屬性來存取它們的中繼資料值和所匯出的物件。 在此情況下，如果發現 `Symbol` 物件的 `IOperationData` 屬性為相符項，則計算機會呼叫 `Operate` 物件的 `IOperation` 方法，並傳回結果。

 若要完成計算機，您也需要可傳回字串中第一個非數字字元位置的 Helper 方法。 將下列 Helper 方法加入 `MySimpleCalculator` 類別：

```vb
Private Function FindFirstNonDigit(ByVal s As String) As Integer
    For i = 0 To s.Length
        If (Not (Char.IsDigit(s(i)))) Then Return i
    Next
    Return -1
End Function
```

```csharp
private int FindFirstNonDigit(String s)
{
    for (int i = 0; i < s.Length; i++)
    {
        if (!(Char.IsDigit(s[i]))) return i;
    }
    return -1;
}
```

 您現在應該可以編譯和執行專案。 在 Visual Basic 中，請確定您已將 `Public` 關鍵字加入 `Module1`。 在主控台視窗中輸入加法運算 (例如 "5+3")，而計算機將會傳回結果。 任何其他運算子都會導致「找不到運算！」 訊息。

<a name="extending_simplecalculator_using_a_new_class"></a>
## <a name="extending-simplecalculator-using-a-new-class"></a>使用新類別擴充 SimpleCalculator
 計算機作用之後，要加入新的運算十分簡單。 將下列類別加入模組或 `SimpleCalculator` 命名空間：

```vb
<Export(GetType(IOperation))>
<ExportMetadata("Symbol", "-"c)>
Public Class Subtract
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left - right
    End Function
End Class
```

```csharp
[Export(typeof(IOperation))]
[ExportMetadata("Symbol", '-')]
class Subtract : IOperation
{
    public int Operate(int left, int right)
    {
        return left - right;
    }
}
```

 編譯並執行專案。 輸入減法運算 (例如 "5-3")。 計算機現在支援減法和加法。

<a name="extending_simplecalculator_using_a_new_assembly"></a>
## <a name="extending-simplecalculator-using-a-new-assembly"></a>使用新組件擴充 SimpleCalculator
 將類別加入原始程式碼相當簡單，但是 MEF 可讓您搜尋應用程式專屬組件來源的外部。 若要示範此情況，您需要修改 SimpleCalculator 來搜尋目錄 (和其專屬組件 (assembly)) 中的組件 (part)，方法是加入 <xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog>。

 將名為 `Extensions` 的新目錄加入至 SimpleCalculator 專案。 請務必在專案層級加入它，而非方案層級。 然後將新的類別庫專案加入至名為 `ExtendedOperations` 的方案。 新的專案將會編譯成不同的組件。

 開啟 ExtendedOperations 專案的專案屬性設計工具，然後按一下 [編譯]  或 [建置]  索引標籤。變更**建置輸出路徑**或**輸出路徑**，使其指向 SimpleCalculator 專案目錄中的 Extensions 目錄 (..\SimpleCalculator\Extensions\\)。

 在 Module1.vb 或 Program.cs 中，將下列行加入 `Program` 建構函式：

```vb
catalog.Catalogs.Add(New DirectoryCatalog("C:\SimpleCalculator\SimpleCalculator\Extensions"))
```

```csharp
catalog.Catalogs.Add(new DirectoryCatalog("C:\\SimpleCalculator\\SimpleCalculator\\Extensions"));
```

 請將範例路徑取代為 Extensions 目錄的路徑 。 (這個絕對路徑僅供偵錯用途。 在生產應用程式中，您將會使用相對路徑。)<xref:System.ComponentModel.Composition.Hosting.DirectoryCatalog> 現在會將 Extensions 目錄之任何組件 (assembly) 中找到的任何組件 (part) 加入組合容器。

 在 ExtendedOperations 專案中，加入 SimpleCalculator 和 System.ComponentModel.Composition 的參考。 在 ExtendedOperations 類別檔案中，針對 System.ComponentModel.Composition 加入 `Imports` 或 `using` 陳述式。 在 Visual Basic 中，也會針對 SimpleCalculator 加入 `Imports` 陳述式。 然後將下列類別加入 ExtendedOperations 類別檔案：

```vb
<Export(GetType(SimpleCalculator.IOperation))>
<ExportMetadata("Symbol", "%"c)>
Public Class Modulo
    Implements IOperation

    Public Function Operate(ByVal left As Integer, ByVal right As Integer) As Integer Implements IOperation.Operate
        Return left Mod right
    End Function
End Class
```

```csharp
[Export(typeof(SimpleCalculator.IOperation))]
[ExportMetadata("Symbol", '%')]
public class Mod : SimpleCalculator.IOperation
{
    public int Operate(int left, int right)
    {
        return left % right;
    }
}
```

 請注意，為了讓合約相符，<xref:System.ComponentModel.Composition.ExportAttribute> 屬性的類型必須與 <xref:System.ComponentModel.Composition.ImportAttribute> 相同。

 編譯並執行專案。 測試新的 Mod (%) 運算子。

<a name="conclusion"></a>
## <a name="conclusion"></a>結論
 本主題涵蓋 MEF 的基本概念。

- 組件、目錄和組合容器

     組件和組合容器是 MEF 應用程式的基本建置組塊。 組件是匯入或匯出值 (隨本身變化且包含本身) 的任何物件。 目錄提供來自特定來源的組件集合。 組合容器會使用目錄所提供的組件來執行組合 (將匯入繫結至匯出)。

- 匯入和匯出

     匯入和匯出是元件用來進行通訊的方式。 元件可以透過匯入來指定需要特定的值或物件，而透過匯出則可以指定值的可用性。 每個匯入都會透過其合約與匯出清單進行比對。

<a name="where_do_i_go_now"></a>
## <a name="where-do-i-go-now"></a>現在我該怎麼做？
 若要下載這個範例的完整程式碼，請參閱 [SimpleCalculator 範例](https://code.msdn.microsoft.com/windowsdesktop/Simple-Calculator-MEF-1152654e) \(英文\)。

 如需詳細資訊和更多程式碼範例，請參閱 [Managed Extensibility Framework](https://github.com/MicrosoftArchive/mef) \(英文\)。 如需 MEF 類型的清單，請參閱 <xref:System.ComponentModel.Composition?displayProperty=nameWithType> 命名空間。
