---
title: 屬性化程式設計模型概觀 (MEF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: baa66f11404e2cee83b4d4b32ba02544c9438d7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="attributed-programming-model-overview-mef"></a>屬性化程式設計模型概觀 (MEF)
在 Managed Extensibility Framework (MEF) 中， *「程式設計模型」* (Programming Model) 是定義 MEF 藉以運作之一組概念性物件的特定方法。 這些概念性物件包含組件、匯入和匯出。 MEF 使用這些物件，但不會指定這些物件的表示方式。 因此，各種程式設計模型都有可能，包括自訂的程式設計模型在內。  
  
 MEF 中所用的預設程式設計模型為 *「屬性化程式設計模型」*(Attributed Programming Model)。 在屬性化程式設計模型中，組件、匯入、匯出和其他物件是以裝飾一般 .NET Framework 類別的屬性來定義。 本主題說明如何使用屬性化程式設計模型所提供的屬性來建立 MEF 應用程式。  
  
<a name="import_and_export_basics"></a>   
## <a name="import-and-export-basics"></a>匯入和匯出基本概念  
 *「匯出」* (Export) 是一個值，組件會將這個值提供給容器中的其他組件； *「匯入」* (Import) 是組件向容器表達的一項需求，會透過可用的匯出來填入。 在屬性化程式設計模型中，匯入和匯出的宣告方式是以 `Import` 和 `Export` 屬性裝飾類別或成員。 `Export` 屬性 (Attribute) 可裝飾類別、欄位、屬性 (Property) 或方法，而 `Import` 屬性 (Attribute) 可裝飾欄位、屬性 (Property) 或建構函式參數。  
  
 為了讓匯入與匯出相符，匯入和匯出必須具有相同的 *「合約」*(Contract)。 合約是由一個字串 (稱為 *「合約名稱」*(Contract Name))，以及所匯出或匯入之物件的類型 (稱為 *「合約類型」*(Contract Type)) 所組成。 只有在合約名稱與合約類型都相符時，才會將匯出視為滿足特定匯入。  
  
 您可以隱含或明確指定上述其中一個或兩個合約參數。 下列程式碼顯示宣告基本匯入的類別。  
  
```vb  
Public Class MyClass1  
    <Import()>  
    Public Property MyAddin As IMyAddin  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import]  
    public IMyAddin MyAddin { get; set; }  
}  
```  
  
 在這個匯入中， `Import` 屬性未附加合約類型或合約名稱參數。 因此，系統會從裝飾的屬性來推斷這兩個參數。 在此範例中，合約類型為 `IMyAddin`，而合約名稱是從合約類型建立的唯一字串。 (換句話說，合約名稱只會與其名稱也是從 `IMyAddin`類型推斷的匯出相符)。  
  
 以下顯示與前述匯入相符的匯出。  
  
```vb  
<Export(GetType(IMyAddin))>  
Public Class MyLogger  
    Implements IMyAddin  
  
End Class  
```  
  
```csharp  
[Export(typeof(IMyAddin))]  
public class MyLogger : IMyAddin { }  
```  
  
 在這個匯出中，合約類型為 `IMyAddin` ，因為已將合約類型指定為 `Export` 屬性的參數。 所匯出的類型必須與合約類型相同、衍生自合約類型，或是實作合約類別 (如果是介面的話)。 在這個匯出中，實際類型 `MyLogger` 實作介面 `IMyAddin`。 合約名稱是從合約類型推斷而來，表示這個匯出符合前述匯入。  
  
> [!NOTE]
>  匯出和匯入通常應該在公用類別或成員上宣告。 其他宣告也受到支援，但匯出或匯入私用、受保護或內部成員會破壞組件的隔離模型，因此不建議這麼做。  
  
 合約類型必須完全相符，才會將匯出和匯入視為相符。 請考慮下列匯出。  
  
```vb  
<Export()> 'WILL NOT match the previous import!  
Public Class MyLogger  
    Implements IMyAddin  
  
End Class  
```  
  
```csharp  
[Export] //WILL NOT match the previous import!  
public class MyLogger : IMyAddin { }  
```  
  
 在這個匯出中，合約類型為 `MyLogger` ，而不是 `IMyAddin`。 即使 `MyLogger` 實作 `IMyAddin`，並因而轉換成 `IMyAddin` 物件，由於合約類型不同，這個匯出仍不符合前述匯入。  
  
 一般而言，您不一定要指定合約名稱，且大多數合約應該會以合約類型和中繼資料來定義。 但在特定情況下，您必須直接指定合約名稱。 最常見的情況就是在類別匯出數個共用常見類型 (例如基本類型) 的值時。 合約名稱可以指定為 `Import` 或 `Export` 屬性的第一個參數。 下列程式碼顯示指定 `MajorRevision`之合約名稱的匯入和匯出。  
  
```vb  
Public Class MyExportClass  
  
    'This one will match  
    <Export("MajorRevision")>  
    Public ReadOnly Property MajorRevision As Integer  
        Get  
            Return 4  
        End Get  
    End Property  
  
    <Export("MinorRevision")>  
    Public ReadOnly Property MinorRevision As Integer  
        Get  
            Return 16  
        End Get  
    End Property  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import("MajorRevision")]  
    public int MajorRevision { get; set; }  
}  
  
public class MyExportClass  
{   
    [Export("MajorRevision")] //This one will match.  
    public int MajorRevision = 4;  
  
    [Export("MinorRevision")]  
    public int MinorRevision = 16;  
}  
```  
  
 如果未指定合約類型，仍會從匯入或匯出的類型來推斷。 不過，即使明確指定合約名稱，合約類型也必須完全相符，才會將匯入與匯出視為相符。 例如，如果 `MajorRevision` 欄位是字串，則推斷的合約類型不符合，且即使匯出和匯入具有相同的合約名稱，也不會相符。  
  
### <a name="importing-and-exporting-a-method"></a>匯入及匯出方法  
 `Export` 屬性 (Attribute) 也可使用與裝飾類別、屬性 (Property) 或函式的相同方式，來裝飾方法。 方法匯出由於無法推斷類型，因此必須指定合約類型或合約名稱。 指定的類型可以是自訂委派或泛型類型 (例如 `Func`)。 下列類別會匯出名為 `DoSomething`的方法。  
  
```vb  
Public Class MyAddin  
  
    'Explicitly specifying a generic type  
    <Export(GetType(Func(Of Integer, String)))>  
    Public Function DoSomething(ByVal TheParam As Integer) As String  
        Return Nothing 'Function body goes here  
    End Function  
  
End Class  
```  
  
```csharp  
public class MyAddin  
{  
    //Explicitly specifying a generic type.  
    [Export(typeof(Func<int, string>)]  
    public string DoSomething(int TheParam);  
}  
```  
  
 在這個類別中， `DoSomething` 方法使用單一 `int` 參數並傳回 `string`。 若要符合這個匯出，匯入端組件必須宣告適當的成員。 下列類別會匯入 `DoSomething` 方法。  
  
```vb  
Public Class MyClass1  
  
    'Contract name must match!  
    <Import()>  
    Public Property MajorRevision As Func(Of Integer, String)  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import] //Contract name must match!  
    public Func<int, string> DoSomething { get; set; }  
}  
```  
  
 如需如何使用 `Func<T, T>` 物件的詳細資訊，請參閱 <xref:System.Func%602>。  
  
<a name="types_of_imports"></a>   
## <a name="types-of-imports"></a>匯入類型  
 MEF 支援數種匯入類型，包括動態匯入、延遲匯入、必要條件匯入和選擇性匯入。  
  
### <a name="dynamic-imports"></a>動態匯入  
 在某些情況下，匯入端類別可能需要符合具有特定合約名稱之任何類型的匯出。 在此情況下，類別可宣告 *「動態匯入」*(Dynamic Import)。 下列匯入符合具有合約名稱 "TheString" 的所有匯出。  
  
```vb  
Public Class MyClass1  
  
    <Import("TheString")>  
    Public Property MyAddin  
  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import("TheString")]  
    public dynamic MyAddin { get; set; }  
}  
```  
  
 當合約類型是從 `dynamic` 關鍵字推斷而來時，會符合所有合約類型。 在此範例中，匯入 **一律** 應指定要符合的合約名稱 (如果未指定合約名稱，則會將匯入視為不符合任何匯出)。以下兩個匯出皆符合前述匯入。  
  
```vb  
<Export("TheString", GetType(IMyAddin))>  
Public Class MyLogger  
    Implements IMyAddin  
  
End Class  
  
<Export("TheString")>  
Public Class MyToolbar  
  
End Class  
```  
  
```csharp  
[Export("TheString", typeof(IMyAddin))]  
public class MyLogger : IMyAddin { }  
  
[Export("TheString")]  
public class MyToolbar { }  
```  
  
 顯然地，匯入端類別必須能夠處理任何類型的物件。  
  
### <a name="lazy-imports"></a>延遲匯入  
 在某些情況下，匯入端類別可能需要間接參考所匯入的物件，以避免立即具現化該物件。 在此情況下，類別會使用 *的合約類型來宣告* 「延遲匯入」 `Lazy<T>`(Lazy Import)。 下列匯入端屬性會宣告延遲匯入。  
  
```vb  
Public Class MyClass1  
  
    <Import()>  
    Public Property MyAddin As Lazy(Of IMyAddin)  
  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import]  
    public Lazy<IMyAddin> MyAddin { get; set; }  
}  
```  
  
 對組合引擎來說， `Lazy<T>` 的合約類型與 `T`的合約類型會視為相同。 因此，前述匯入會符合下列匯出。  
  
```vb  
<Export(GetType(IMyAddin))>  
Public Class MyLogger  
    Implements IMyAddin  
  
End Class  
```  
  
```csharp  
[Export(typeof(IMyAddin))]  
public class MyLogger : IMyAddin { }  
```  
  
 您可以在延遲匯入的 `Import` 屬性中指定合約名稱與合約類型，方法如稍早的＜匯入和匯出基本概念＞一節所述。  
  
### <a name="prerequisite-imports"></a>必要條件匯入  
 所匯出的 MEF 組件通常是由組合引擎所建立，不論是為了回應直接要求，或是為了應需要填入相符的匯入。 根據預設，建立組件時，組合引擎會使用沒有參數的建構函式。 若要讓引擎使用不同的建構函式，您可以使用 `ImportingConstructor` 屬性來標記引擎。  
  
 每個組件都只能有一個建構函式供組合引擎使用。 不提供預設建構函式和 `ImportingConstructor` 屬性，或是提供多個 `ImportingConstructor` 屬性，都會產生錯誤。  
  
 為了填入以 `ImportingConstructor` 屬性標記之建構函式的參數，所有參數都會自動以匯入的形式宣告。 這種方法很方便用於宣告在組件初始設定期間使用的匯入。 下列類別使用 `ImportingConstructor` 來宣告匯入。  
  
```vb  
Public Class MyClass1  
  
    Private _theAddin As IMyAddin  
  
    'Default constructor will NOT be used  
    'because the ImportingConstructor  
    'attribute is present.  
    Public Sub New()  
  
    End Sub  
  
    'This constructor will be used.  
    'An import with contract type IMyAddin  
    'is declared automatically.  
    <ImportingConstructor()>  
    Public Sub New(ByVal MyAddin As IMyAddin)  
        _theAddin = MyAddin  
    End Sub  
  
End Class  
```  
  
```csharp  
public class MyClass   
{  
    private IMyAddin _theAddin;  
  
    //Default constructor will NOT be  
    //used because the ImportingConstructor  
    //attribute is present.  
    public MyClass() { }  
  
    //This constructor will be used.  
    //An import with contract type IMyAddin is   
    //declared automatically.  
    [ImportingConstructor]   
    public MyClass(IMyAddin MyAddin)   
    {  
        _theAddin = MyAddin;  
    }  
}  
```  
  
 根據預設， `ImportingConstructor` 屬性會針對所有參數匯入使用推斷的合約類型與合約名稱。 您可以覆寫此預設值，方法是以 `Import` 屬性裝飾參數，然後明確地定義合約類型與合約名稱。 下列程式碼示範使用此語法匯入衍生類別 (而不是父類別) 的建構函式。  
  
```vb  
<ImportingConstructor()>  
Public Sub New(<Import(GetType(IMySubAddin))> ByVal MyAddin As IMyAddin)  
  
End Sub  
```  
  
```csharp  
[ImportingConstructor]   
public MyClass([Import(typeof(IMySubAddin))]IMyAddin MyAddin)   
{  
    _theAddin = MyAddin;  
}  
```  
  
 特別要提的是，處理集合參數時應小心。 例如，如果您在具有 `ImportingConstructor` 類型之參數的建構函式上指定 `IEnumerable<int>`，則匯入會符合 `IEnumerable<int>`類型的單一匯出，而不是 `int`類型的一組匯出。 若要符合 `int`類型的一組匯出，您必須以 `ImportMany` 屬性裝飾參數。  
  
 由 `ImportingConstructor` 屬性以匯入形式宣告的參數也會標記為 *「必要條件匯入」*(Prerequisite Import)。 MEF 通常會允許匯出和匯入形成 *「循環」*(Cycle)。 例如，物件 A 會匯入物件 B，而物件 B 會匯入物件 A，這就是循環。在一般情況下，循環並不是問題，組合容器可以正常建構這兩個物件。  
  
 當某個組件的建構函式需要匯入的值時，該物件就不能參與循環。 如果物件 A 要求要等物件 B 建構後才能建構自己，而物件 B 會匯入物件 A，這個循環就無法解決而引發組合錯誤。 因此，在建構函式參數上宣告的匯入是必要條件性匯入，也就是說，必須先填入這些匯入，才能從需要這些匯入的物件使用任何匯出。  
  
### <a name="optional-imports"></a>選擇性匯入  
 `Import` 屬性指定要讓組件正常運作必須達到的需求。 如果無法完成匯入，則組合該組件會失敗，而組件會無法使用。  
  
 您可以使用 *屬性，將匯入指定為* 「選擇性」 `AllowDefault` (Optional) 匯入。 在此情況下，即使匯入不符合任何可用的匯出，組合也會成功，並且匯入端屬性會設定為其屬性類型的預設值 (如果是物件屬性則為 `null`，如果是布林值屬性則為 `false`，如果是數值屬性則為零)。下列類別使用選擇性匯入。  
  
```vb  
Public Class MyClass1  
  
    <Import(AllowDefault:=True)>  
    Public Property thePlugin As Plugin  
  
    'If no matching export is available,  
    'thePlugin will be set to null.  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [Import(AllowDefault = true)]  
    public Plugin thePlugin { get; set; }  
  
    //If no matching export is avaliable,  
    //thePlugin will be set to null.  
}  
```  
  
### <a name="importing-multiple-objects"></a>匯入多個物件  
 `Import` 屬性必須剛好符合一個匯出，才能順利組合。 其他情況將會產生組合錯誤。 若要匯入多個與同一個合約相符的匯出，請使用 `ImportMany` 屬性。 以這個屬性標記的匯入一律會是選擇性匯入。 例如，即使沒有相符的匯出，組合也不會失敗。 下列類別會匯入 `IMyAddin`類型之任意數目的匯出。  
  
```vb  
Public Class MyClass1  
  
    <ImportMany()>  
    Public Property MyAddin As IEnumerable(Of IMyAddin)  
  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [ImportMany]  
    public IEnumerable<IMyAddin> MyAddin { get; set; }  
}  
```  
  
 使用一般的 `IEnumerable<T>` 語法和方法，即可存取所匯入的陣列。 另外，也可以改用一般陣列 (`IMyAddin[]`)。  
  
 搭配 `Lazy<T>` 語法一起使用時，這個模式非常重要。 例如，您可以使用 `ImportMany`、 `IEnumerable<T>`和 `Lazy<T>`匯入任意數目之物件的間接參考，然後只具現化成為必要的物件。 下列類別示範這個模式。  
  
```vb  
Public Class MyClass1  
  
    <ImportMany()>  
    Public Property MyAddin As IEnumerable(Of Lazy(Of IMyAddin))  
  
End Class  
```  
  
```csharp  
public class MyClass  
{  
    [ImportMany]  
    public IEnumerable<Lazy<IMyAddin>> MyAddin { get; set; }  
}  
```  
  
<a name="avoiding_discovery"></a>   
## <a name="avoiding-discovery"></a>避免探索  
 在某些情況下，您可能不想讓組件被當做目錄的一部分來探索。 例如，您可能想讓組件成為用於繼承的基底類別，而不直接使用。 有兩種方法可達成這個目標。 第一種方法是在組件類別上使用 `abstract` 關鍵字。 抽象類別絕不會提供匯出，但是可以提供繼承的匯出給衍生自抽象類別的類別。  
  
 如果無法將類別變成抽象類別，您可以使用 `PartNotDiscoverable` 屬性加以裝飾。 使用這個屬性裝飾的組件將不會包含在任何目錄中。 下列範例示範這些模式。 目錄會探索到`DataOne` 。 由於 `DataTwo` 是抽象的，因此不會被探索到。 由於 `DataThree` 使用 `PartNotDiscoverable` 屬性，因此不會被探索到。  
  
```vb  
<Export()>  
Public Class DataOne  
    'This part will be discovered   
    'as normal by the catalog.  
End Class  
  
<Export()>  
Public MustInherit Class DataTwo  
    'This part will not be discovered  
    'by the catalog.  
End Class  
  
<PartNotDiscoverable()>  
<Export()>  
Public Class DataThree  
    'This part will also not be discovered  
    'by the catalog.  
End Class  
```  
  
```csharp  
[Export]  
public class DataOne  
{  
    //This part will be discovered  
    //as normal by the catalog.  
}  
  
[Export]  
public abstract class DataTwo  
{  
    //This part will not be discovered  
    //by the catalog.  
}  
  
[PartNotDiscoverable]  
[Export]  
public class DataThree  
{  
    //This part will also not be discovered  
    //by the catalog.  
}  
```  
  
<a name="metadata_and_metadata_views"></a>   
## <a name="metadata-and-metadata-views"></a>中繼資料和中繼資料檢視  
 匯出可以提供有關本身的其他資訊，也稱為 *「中繼資料」*(Metadata)。 中繼資料可用來將所匯出物件的屬性傳送至匯入端組件。 匯入端組件可使用此資料來決定要使用的匯出，或是蒐集匯出相關資訊，而不必建構匯出。 因此，匯入必須是延遲匯入才能使用中繼資料。  
  
 為了使用中繼資料，您通常會宣告一個稱為 *「中繼資料檢視」*(Metadata View) 的介面，該介面會宣告可以使用哪些中繼資料。 中繼資料檢視介面必須只有屬性，而這些屬性必須具有 `get` 存取子。 下列介面是中繼資料檢視範例。  
  
```vb  
Public Interface IPluginMetadata  
  
    ReadOnly Property Name As String  
  
    <DefaultValue(1)>  
    ReadOnly Property Version As Integer  
  
End Interface  
```  
  
```csharp  
public interface IPluginMetadata  
{  
    string Name { get; }  
  
    [DefaultValue(1)]    
    int Version { get; }  
}  
```  
  
 您也可以使用泛型集合 `IDictionary<string, object>`做為中繼資料檢視，但是這樣會享受不到類型檢查的好處，應該加以避免。  
  
 一般而言，中繼資料檢視中具名的所有屬性都是必要屬性，未提供這些屬性的匯出將會視為不相符。 `DefaultValue` 屬性 (Attribute) 指定某個屬性 (Property) 是選擇性的。 如果未納入該屬性 (Property)，則會指派指定的預設值做為 `DefaultValue`的參數。 以下是以中繼資料裝飾的兩個不同類別。 這兩個類別都符合前述中繼資料檢視。  
  
```vb  
<Export(GetType(IPlugin))>  
<ExportMetadata("Name", "Logger")>  
<ExportMetadata("Version", 4)>  
Public Class MyLogger  
    Implements IPlugin  
  
End Class  
  
'Version is not required because of the DefaultValue  
<Export(GetType(IPlugin))>  
<ExportMetadata("Name", "Disk Writer")>  
Public Class DWriter  
    Implements IPlugin  
  
End Class  
```  
  
```csharp  
[Export(typeof(IPlugin)),  
    ExportMetadata("Name", "Logger"),  
    ExportMetadata("Version", 4)]  
public class Logger : IPlugin  
{  
}  
  
[Export(typeof(IPlugin)),  
    ExportMetadata("Name", "Disk Writer")]   
    //Version is not required because of the DefaultValue  
public class DWriter : IPlugin  
{  
}  
```  
  
 中繼資料會在 `Export` 屬性後面以 `ExportMetadata` 屬性表示。 每項中繼資料都是由名稱/值組所組成。 中繼資料的名稱部分必須符合中繼資料檢視中適當屬性 (Property) 的名稱，並為該屬性指派值。  
  
 匯入者可指定要使用的中繼資料檢視 (如果有的話)。 具有中繼資料的匯入會以延遲匯入的形式宣告，並以中繼資料介面做為 `Lazy<T,T>`的第二個類型參數。 下列類別會匯入具有中繼資料的前述組件。  
  
```vb  
Public Class Addin  
  
    <Import()>  
    Public Property plugin As Lazy(Of IPlugin, IPluginMetadata)  
End Class  
```  
  
```csharp  
public class Addin  
{  
    [Import]  
    public Lazy<IPlugin, IPluginMetadata> plugin;  
}  
```  
  
 在許多情況下，您會想要將中繼資料與 `ImportMany` 屬性結合，以便剖析多個可用的匯入，然後只選擇並具現化某個匯入，或者是篩選集合中符合特定條件的項目。 下列類別只會具現化 `IPlugin` 值為 "Logger" 的 `Name` 物件。  
  
```vb  
Public Class User  
  
    <ImportMany()>  
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))  
  
    Public Function InstantiateLogger() As IPlugin  
  
        Dim logger As IPlugin  
        logger = Nothing  
  
        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins  
            If (Plugin.Metadata.Name = "Logger") Then  
                logger = Plugin.Value  
            End If  
        Next  
        Return logger  
    End Function  
  
End Class  
```  
  
```csharp  
public class User  
{  
    [ImportMany]  
    public IEnumerable<Lazy<IPlugin, IPluginMetadata>> plugins;  
  
    public IPlugin InstantiateLogger ()  
    {  
        IPlugin logger = null;  
  
        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)  
        {  
            if (plugin.Metadata.Name = "Logger") logger = plugin.Value;  
        }  
        return logger;  
    }  
}  
```  
  
<a name="import_and_export_inheritance"></a>   
## <a name="import-and-export-inheritance"></a>匯入及匯出繼承  
 如果類別繼承自某個組件，則該類別也可能會變成組件。 子類別一律會繼承匯入。 因此，組件的子類別一律會是組件，因為其具有和父類別相同的匯入。  
  
 子類別不會繼承以 `Export` 屬性宣告的匯出。 不過，組件可以使用 `InheritedExport` 屬性來匯出自己。 組件的子類別會繼承並提供同一個匯出，包括合約名稱與合約類型。 與 `Export` 屬性不同的是， `InheritedExport` 只能在類別層級套用，而不能在成員層級套用。 因此，永遠無法繼承成員層級的匯出。  
  
 下列四個類別示範匯入和匯出的繼承原則。 `NumTwo` 繼承自 `NumOne`，因此 `NumTwo` 會匯入 `IMyData`。 由於不會繼承一般匯出，因此 `NumTwo` 不會匯出任何項目。 `NumFour` 繼承自 `NumThree`。 由於 `NumThree` 使用 `InheritedExport`，因此 `NumFour` 有一個具有合約類型 `NumThree`的匯出。 由於絕不會繼承成員層級的匯出，因此不會匯出 `IMyData` 。  
  
```vb  
<Export()>  
Public Class NumOne  
    <Import()>  
    Public Property MyData As IMyData  
End Class  
  
Public Class NumTwo  
    Inherits NumOne  
  
    'Imports are always inherited, so NumTwo will  
    'Import IMyData  
  
    'Ordinary exports are not inherited, so  
    'NumTwo will NOT export anything.  As a result it  
    'will not be discovered by the catalog!  
  
End Class  
  
<InheritedExport()>  
Public Class NumThree  
  
    <Export()>  
    Public Property MyData As IMyData  
  
    'This part provides two exports, one of  
    'contract type NumThree, and one of   
    'contract type IMyData.  
  
End Class  
  
Public Class NumFour  
    Inherits NumThree  
  
    'Because NumThree used InheritedExport,  
    'this part has one export with contract   
    'type NumThree.  
  
    'Member-level exports are never inherited,  
    'so IMyData is not exported.  
  
End Class  
```  
  
```csharp  
[Export]  
public class NumOne  
{  
    [Import]  
    public IMyData MyData { get; set; }  
}  
  
public class NumTwo : NumOne  
{  
    //Imports are always inherited, so NumTwo will   
    //import IMyData.  
  
    //Ordinary exports are not inherited, so   
    //NumTwo will NOT export anything. As a result it   
    //will not be discovered by the catalog!  
}  
  
[InheritedExport]  
public class NumThree  
{  
    [Export]  
    Public IMyData MyData { get; set; }  
  
    //This part provides two exports, one of  
    //contract type NumThree, and one of  
    //contract type IMyData.  
}  
  
public class NumFour : NumThree  
{  
    //Because NumThree used InheritedExport,  
    //this part has one export with contract  
    //type NumThree.  
  
    //Member-level exports are never inherited,  
    //so IMyData is not exported.  
}  
```  
  
 如果 `InheritedExport` 屬性有相關聯的中繼資料，也會繼承該中繼資料 (如需詳細資訊，請參閱稍早的＜中繼資料和中繼資料檢視＞一節)。子類別無法修改所繼承的中繼資料。 不過，子類別可以藉由重新宣告具有相同合約名稱與合約類型 (但使用新的中繼資料) 的 `InheritedExport`，以新的中繼資料來取代繼承的中繼資料。 下列類別示範這個原則。 `MegaLogger` 組件繼承自 `Logger` 並包含 `InheritedExport` 屬性。 由於 `MegaLogger` 重新宣告名為 Status 的新中繼資料，因此不會從 `Logger`繼承 Name 和 Version 中繼資料。  
  
```vb  
<InheritedExport(GetType(IPlugin))>  
<ExportMetadata("Name", "Logger")>  
<ExportMetadata("Version", 4)>  
Public Class Logger  
    Implements IPlugin  
  
    'Exports with contract type IPlugin  
    'and metadata "Name" and "Version".  
End Class  
  
Public Class SuperLogger  
    Inherits Logger  
  
    'Exports with contract type IPlugin and   
    'metadata "Name" and "Version", exactly the same  
    'as the Logger class.  
  
End Class  
  
<InheritedExport(GetType(IPlugin))>  
<ExportMetadata("Status", "Green")>  
Public Class MegaLogger  
    Inherits Logger  
  
    'Exports with contract type IPlugin and   
    'metadata "Status" only. Re-declaring   
    'the attribute replaces all metadata.  
  
End Class  
```  
  
```csharp  
[InheritedExport(typeof(IPlugin)),  
    ExportMetadata("Name", "Logger"),  
    ExportMetadata("Version", 4)]  
public class Logger : IPlugin  
{  
    //Exports with contract type IPlugin and   
    //metadata "Name" and "Version".  
}  
  
public class SuperLogger : Logger  
{  
    //Exports with contract type IPlugin and   
    //metadata "Name" and "Version", exactly the same  
    //as the Logger class.  
}  
  
[InheritedExport(typeof(IPlugin)),  
    ExportMetadata("Status", "Green")]  
public class MegaLogger : Logger        {  
    //Exports with contract type IPlugin and   
    //metadata "Status" only. Re-declaring   
    //the attribute replaces all metadata.  
}  
```  
  
 當您重新宣告 `InheritedExport` 屬性以覆寫中繼資料時，請確定合約類型相同。 (在上述範例中，合約類型是 `IPlugin`)。如果合約類型不同，則第二個屬性會從組件建立第二個獨立的匯出，而不是覆寫原有的匯出。 一般而言，這表示當您覆寫 `InheritedExport` 屬性時，您必須明確指定合約類型，如上述範例所示。  
  
 由於無法直接具現化介面，因此通常無法以 `Export` 或 `Import` 屬性裝飾介面。 不過，您可以在介面層級以 `InheritedExport` 屬性裝飾介面，然後該匯出與所有相關聯的中繼資料就會由任何實作端類別所繼承。 但是，介面本身無法當做組件使用。  
  
<a name="custom_export_attributes"></a>   
## <a name="custom-export-attributes"></a>自訂匯出屬性  
 您可以擴充基本的匯出屬性 `Export` 和 `InheritedExport`，以納入中繼資料做為屬性 (Attribute) 的屬性 (Property)。 要將類似的中繼資料套用至許多組件，或是建立中繼資料屬性的繼承樹時，這個做法會很有用。  
  
 自訂屬性可以指定合約類型、合約名稱或其他任何中繼資料。 若要定義自訂屬性，必須以 `ExportAttribute` 屬性裝飾從 `InheritedExportAttribute`(或 `MetadataAttribute` ) 繼承的類別。 下列類別會定義自訂屬性。  
  
```vb  
<MetadataAttribute()>  
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=false)>  
Public Class MyAttribute  
    Inherits ExportAttribute  
  
    Public Property MyMetadata As String  
  
    Public Sub New(ByVal myMetadata As String)  
        MyBase.New(GetType(IMyAddin))  
  
        myMetadata = myMetadata  
    End Sub  
  
End Class  
```  
  
```csharp  
[MetadataAttribute]  
[AttributeUsage(AttributeTargets.Class, AllowMultiple=false)]  
public class MyAttribute : ExportAttribute  
{  
    public MyAttribute(string myMetadata)   
        : base(typeof(IMyAddin))  
    {  
        MyMetadata = myMetadata;  
    }  
  
    public string MyMetadata { get; private set; }  
}  
```  
  
 這個類別使用合約類型 `MyAttribute` 和某個名為 `IMyData` 的中繼資料，定義名為 `MyMetadata`的自訂屬性。 類別中以 `MetadataAttribute` 屬性 (Attribute) 標記的所有屬性 (Property)，都會視為在自訂屬性 (Attribute) 中定義的中繼資料。 下列兩個宣告的用法是相同的。  
  
```vb  
<Export(GetType(IMyAddin))>  
<ExportMetadata("MyMetadata", "theData")>  
Public Property myAddin As MyAddin  
  
<MyAttribute("theData")>  
Public Property myAddin As MyAddin  
```  
  
```csharp  
[Export(typeof(IMyAddin)),   
    ExportMetadata("MyMetadata", "theData")]  
public MyAddin myAddin { get; set; }  
```  
  
```  
[MyAttribute("theData")]  
public MyAddin myAddin { get; set; }  
```  
  
 在第一個宣告中，已明確定義合約類型和中繼資料。 在第二個宣告中，合約類型和中繼資料隱含在自訂的屬性中。 特別是在必須將大量相同的中繼資料套用至許多組件 (例如，作者或著作權資訊) 的情況下，使用自訂屬性可以節省許多時間，而且避免一再執行重複的動作。 另外，還可以建立自訂屬性的繼承樹，以允許更多變化。  
  
 若要在自訂屬性中建立選擇性中繼資料，您可以使用 `DefaultValue` 屬性。 當這個屬性 (Attribute) 套用至自訂屬性 (Attribute) 類別中的某個屬性 (Property) 時，會將裝飾的屬性 (Property) 指定為匯出者不一定要提供的選擇性屬性 (Property)。 如果未提供屬性 (Property) 的值，則會將屬性類型的預設值 (通常是 `null`、 `false`或 0) 指派給該屬性。  
  
<a name="creation_policies"></a>   
## <a name="creation-policies"></a>建立原則  
 當組件指定匯入並執行組合時，組合容器會嘗試尋找相符的匯出。 如果匯入成功符合匯出，便會將匯入端成員設定為所匯出物件的執行個體。 這個執行個體的來源是由匯出端組件的 *「建立原則」*(Creation Policy) 所控制。  
  
 兩個可能的建立原則為 *「共用」* (Shared) 和 *「非共用」*(Non-Shared)。 具有共用建立原則的組件會在具有該合約之組件的容器中供每個匯入共用。 當組合引擎在找到相符項而必須設定匯入端屬性時，會具現化新的組件複本 (如果尚未存在任何複本)，或是提供現有的複本。 這表示可能有許多物件參考同一個組件。 這類組件不應該依賴可能會由多個位置變更的內部狀態。 此原則適用於靜態組件、提供服務的組件，以及耗用大量記憶體或其他資源的組件。  
  
 每次找到其中一個匯出的相符匯入，都會建立具有非共用建立原則的組件。 因此，系統會為容器中每個符合該組件之其中一個匯出合約的匯入，各具現化一個新的複本。 這些複本的內部狀態不會受到共用。 此原則適用於其中每個匯入都需要專屬內部狀態的組件。  
  
 匯入和匯出都可以指定組件的建立原則，其值包含 `Shared`、 `NonShared`或 `Any`。 對於匯入和匯出而言，預設值皆為 `Any` 。 指定 `Shared` 或 `NonShared` 的匯出，只會符合指定相同值或是指定 `Any`的匯入。 同樣地，指定 `Shared` 或 `NonShared` 的匯入，只會符合指定相同值或是指定 `Any`的匯出。 就像是合約名稱或合約類型不同的匯入和匯出不會相符一樣，建立原則不相容的匯入和匯出也不會視為相符。 如果匯入和匯出都指定 `Any`，或是因未指定建立原則而預設為 `Any`，則建立原則會預設為共用。  
  
 下列範例示範指定建立原則的匯入和匯出。 `PartOne` 未指定建立原則，因此預設值為 `Any`。 `PartTwo` 未指定建立原則，因此預設值為 `Any`。 由於匯入和匯出都預設為 `Any`，因此會共用 `PartOne` 。 `PartThree` 指定 `Shared` 建立原則，因此 `PartTwo` 和 `PartThree` 會共用相同的 `PartOne`複本。 `PartFour` 指定 `NonShared` 建立原則，因此 `PartFour` 在 `PartFive`中不會共用。 `PartSix` 指定 `NonShared` 建立原則。 `PartFive` 和 `PartSix` 將收到個別的 `PartFour`複本。 `PartSeven` 指定 `Shared` 建立原則。 由於沒有具有 `PartFour` 建立原則的已匯出 `Shared`，因此 `PartSeven` 匯入不符合任何項目，並且不會被填入。  
  
```vb  
<Export()>  
Public Class PartOne  
    'The default creation policy for an export is Any.  
End Class  
  
Public Class PartTwo  
  
    <Import()>  
    Public Property partOne As PartOne  
  
    'The default creation policy for an import is Any.  
    'If both policies are Any, the part will be shared.  
  
End Class  
  
Public Class PartThree  
  
    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>  
    Public Property partOne As PartOne  
  
    'The Shared creation policy is explicitly specified.  
    'PartTwo and PartThree will receive references to the  
    'SAME copy of PartOne.  
  
End Class  
  
<Export()>  
<PartCreationPolicy(CreationPolicy.NonShared)>  
Public Class PartFour  
    'The NonShared creation policy is explicitly specified.  
End Class  
  
Public Class PartFive  
  
    <Import()>  
    Public Property partFour As PartFour  
  
    'The default creation policy for an import is Any.  
    'Since the export's creation policy was explictly  
    'defined, the creation policy for this property will  
    'be non-shared.  
  
End Class  
  
Public Class PartSix  
  
    <Import(RequiredCreationPolicy:=CreationPolicy.NonShared)>  
    Public Property partFour As PartFour  
  
    'Both import and export specify matching creation   
    'policies.  PartFive and PartSix will each receive   
    'SEPARATE copies of PartFour, each with its own  
    'internal state.  
  
End Class  
  
Public Class PartSeven  
  
    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>  
    Public Property partFour As PartFour  
  
    'A creation policy mismatch.  Because there is no   
    'exported PartFour with a creation policy of Shared,  
    'this import does not match anything and will not be  
    'filled.  
  
End Class  
```  
  
```csharp  
[Export]  
public class PartOne  
{  
    //The default creation policy for an export is Any.  
}  
  
public class PartTwo  
{  
    [Import]  
    public PartOne partOne { get; set; }  
  
    //The default creation policy for an import is Any.  
    //If both policies are Any, the part will be shared.  
}  
  
public class PartThree  
{  
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]  
    public PartOne partOne { get; set; }  
  
    //The Shared creation policy is explicitly specified.  
    //PartTwo and PartThree will receive references to the  
    //SAME copy of PartOne.  
}  
  
[Export]  
[PartCreationPolicy(CreationPolicy.NonShared)]  
public class PartFour  
{  
    //The NonShared creation policy is explicitly specified.  
}  
  
public class PartFive  
{  
    [Import]  
    public PartFour partFour { get; set; }  
  
    //The default creation policy for an import is Any.  
    //Since the export's creation policy was explictly  
    //defined, the creation policy for this property will  
    //be non-shared.  
}  
  
public class PartSix  
{  
    [Import(RequiredCreationPolicy = CreationPolicy.NonShared)]  
    public PartFour partFour { get; set; }  
  
    //Both import and export specify matching creation   
    //policies.  PartFive and PartSix will each receive   
    //SEPARATE copies of PartFour, each with its own  
    //internal state.  
}  
  
public class PartSeven  
{  
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]  
    public PartFour partFour { get; set; }  
  
    //A creation policy mismatch.  Because there is no   
    //exported PartFour with a creation policy of Shared,  
    //this import does not match anything and will not be  
    //filled.  
}  
```  
  
<a name="life_cycle_and_disposing"></a>   
## <a name="life-cycle-and-disposing"></a>生命週期和處置  
 由於組件裝載於組合容器中，因此其生命週期可能比一般物件更複雜。 組件可以實作兩個與生命週期相關的重要介面： `IDisposable` 和 `IPartImportsSatisfiedNotification`。  
  
 如同一般的 .NET Framework 物件，需要在關閉時執行工作的組件，或是需要釋放資源的組件，都應該實作 `IDisposable`。 但是，由於容器會建立和維護對組件的參考，因此只有擁有組件的容器應該對組件呼叫 `Dispose` 方法。 容器本身會實作 `IDisposable`，而且在 `Dispose` 清除過程中，它會對所擁有的全部組件呼叫 `Dispose` 。 因此，只要不再需要組合容器和其擁有的所有組件，便應該處置該組合容器。  
  
 對於存留期很長的組合容器而言，長期讓具有非共用建立原則的組件耗用記憶體可能會帶來問題。 這些非共用的組件可能會建立多次，並且在處置容器本身之前，都不會處置這些組件。 為了解決這個問題，容器提供了 `ReleaseExport` 方法。 在非共用的匯出上呼叫這個方法，可從組合容器中移除該匯出並進行處置。 移除的匯出唯一使用的組件，以及樹狀目錄中的下層組件，也會一併遭到移除和處置。 如此一來，不需處置組合容器本身，即可回收資源。  
  
 `IPartImportsSatisfiedNotification` 包含一個名為 `OnImportsSatisfied`的方法。 當組合完成且組件的匯入可開始使用時，組合容器會對任何實作介面的組件呼叫這個方法。 組合引擎會建立組件，以填入其他組件的匯入。 設定組件的匯入之前，您無法在組件建構函式中執行任何依賴或操作匯入值的初始設定，除非已使用 `ImportingConstructor` 屬性指定這些值做為必要條件。 這通常是比較好的方法，但在某些情況下，可能無法插入建構函式。 在這些情況下，您可以在 `OnImportsSatisfied`中執行初始設定，並且組件應該實作 `IPartImportsSatisfiedNotification`。  
  
## <a name="see-also"></a>另請參閱  
 [Channel 9 影片： Managed 的 Extensibility Framework 的應用程式開啟](http://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)  
 [Channel 9 影片： Managed 的 Extensibility Framework (MEF) 2.0](http://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
