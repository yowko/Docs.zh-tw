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
ms.openlocfilehash: 09eb37fd2c1bf77e981a2eb7952b1fff5110e977
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357296"
---
# <a name="attributed-programming-model-overview-mef"></a><span data-ttu-id="31e32-102">屬性化程式設計模型概觀 (MEF)</span><span class="sxs-lookup"><span data-stu-id="31e32-102">Attributed Programming Model Overview (MEF)</span></span>

<span data-ttu-id="31e32-103">在 Managed Extensibility Framework (MEF) 中， *「程式設計模型」* (Programming Model) 是定義 MEF 藉以運作之一組概念性物件的特定方法。</span><span class="sxs-lookup"><span data-stu-id="31e32-103">In the Managed Extensibility Framework (MEF), a *programming model* is a particular method of defining the set of conceptual objects on which MEF operates.</span></span> <span data-ttu-id="31e32-104">這些概念性物件包含組件、匯入和匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-104">These conceptual objects include parts, imports, and exports.</span></span> <span data-ttu-id="31e32-105">MEF 使用這些物件，但不會指定這些物件的表示方式。</span><span class="sxs-lookup"><span data-stu-id="31e32-105">MEF uses these objects, but does not specify how they should be represented.</span></span> <span data-ttu-id="31e32-106">因此，各種程式設計模型都有可能，包括自訂的程式設計模型在內。</span><span class="sxs-lookup"><span data-stu-id="31e32-106">Therefore, a wide variety of programming models are possible, including customized programming models.</span></span>

<span data-ttu-id="31e32-107">MEF 中所用的預設程式設計模型為 *「屬性化程式設計模型」*(Attributed Programming Model)。</span><span class="sxs-lookup"><span data-stu-id="31e32-107">The default programming model used in MEF is the *attributed programming model*.</span></span> <span data-ttu-id="31e32-108">在屬性化程式設計模型中，組件、匯入、匯出和其他物件是以裝飾一般 .NET Framework 類別的屬性來定義。</span><span class="sxs-lookup"><span data-stu-id="31e32-108">In the attributed programming model parts, imports, exports, and other objects are defined with attributes that decorate ordinary .NET Framework classes.</span></span> <span data-ttu-id="31e32-109">本主題說明如何使用屬性化程式設計模型所提供的屬性來建立 MEF 應用程式。</span><span class="sxs-lookup"><span data-stu-id="31e32-109">This topic explains how to use the attributes provided by the attributed programming model to create a MEF application.</span></span>

<a name="import_and_export_basics"></a>

## <a name="import-and-export-basics"></a><span data-ttu-id="31e32-110">匯入和匯出基本概念</span><span class="sxs-lookup"><span data-stu-id="31e32-110">Import and Export Basics</span></span>

<span data-ttu-id="31e32-111">*「匯出」* (Export) 是一個值，組件會將這個值提供給容器中的其他組件； *「匯入」* (Import) 是組件向容器表達的一個需求，會透過可用的匯出來填入。</span><span class="sxs-lookup"><span data-stu-id="31e32-111">An *export* is a value that a part provides to other parts in the container, and an *import* is a requirement that a part expresses to the container, to be filled from the available exports.</span></span> <span data-ttu-id="31e32-112">在屬性化程式設計模型中，匯入和匯出的宣告方式是以 `Import` 和 `Export` 屬性裝飾類別或成員。</span><span class="sxs-lookup"><span data-stu-id="31e32-112">In the attributed programming model, imports and exports are declared by decorating classes or members with the `Import` and `Export` attributes.</span></span> <span data-ttu-id="31e32-113">`Export` 屬性 (Attribute) 可裝飾類別、欄位、屬性 (Property) 或方法，而 `Import` 屬性 (Attribute) 可裝飾欄位、屬性 (Property) 或建構函式參數。</span><span class="sxs-lookup"><span data-stu-id="31e32-113">The `Export` attribute can decorate a class, field, property, or method, while the `Import` attribute can decorate a field, property, or constructor parameter.</span></span>

<span data-ttu-id="31e32-114">為了讓匯入與匯出相符，匯入和匯出必須具有相同的 *「合約」*(Contract)。</span><span class="sxs-lookup"><span data-stu-id="31e32-114">In order for an import to be matched with an export, the import and export must have the same *contract*.</span></span> <span data-ttu-id="31e32-115">合約是由一個字串 (稱為 *「合約名稱」*(Contract Name))，以及所匯出或匯入之物件的類型 (稱為 *「合約類型」*(Contract Type)) 所組成。</span><span class="sxs-lookup"><span data-stu-id="31e32-115">The contract consists of a string, called the *contract name*, and the type of the exported or imported object, called the *contract type*.</span></span> <span data-ttu-id="31e32-116">只有在合約名稱與合約類型都相符時，才會將匯出視為滿足特定匯入。</span><span class="sxs-lookup"><span data-stu-id="31e32-116">Only if both the contract name and contract type match is an export considered to fulfill a particular import.</span></span>

<span data-ttu-id="31e32-117">您可以隱含或明確指定上述其中一個或兩個合約參數。</span><span class="sxs-lookup"><span data-stu-id="31e32-117">Either or both of the contract parameters can be implicit or explicit.</span></span> <span data-ttu-id="31e32-118">下列程式碼顯示宣告基本匯入的類別。</span><span class="sxs-lookup"><span data-stu-id="31e32-118">The following code shows a class that declares a basic import.</span></span>

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

<span data-ttu-id="31e32-119">在這個匯入中， `Import` 屬性未附加合約類型或合約名稱參數。</span><span class="sxs-lookup"><span data-stu-id="31e32-119">In this import, the `Import` attribute has neither a contract type nor a contract name parameter attached.</span></span> <span data-ttu-id="31e32-120">因此，系統會從裝飾的屬性來推斷這兩個參數。</span><span class="sxs-lookup"><span data-stu-id="31e32-120">Therefore, both will be inferred from the decorated property.</span></span> <span data-ttu-id="31e32-121">在此範例中，合約類型為 `IMyAddin`，而合約名稱是從合約類型建立的唯一字串。</span><span class="sxs-lookup"><span data-stu-id="31e32-121">In this case, the contract type will be `IMyAddin`, and the contract name will be a unique string created from the contract type.</span></span> <span data-ttu-id="31e32-122">(換句話說，合約名稱只會與其名稱也是從 `IMyAddin`類型推斷的匯出相符)。</span><span class="sxs-lookup"><span data-stu-id="31e32-122">(In other words, the contract name will match only exports whose names are also inferred from the type `IMyAddin`.)</span></span>

<span data-ttu-id="31e32-123">以下顯示與前述匯入相符的匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-123">The following shows an export that matches the previous import.</span></span>

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

<span data-ttu-id="31e32-124">在這個匯出中，合約類型為 `IMyAddin` ，因為已將合約類型指定為 `Export` 屬性的參數。</span><span class="sxs-lookup"><span data-stu-id="31e32-124">In this export, the contract type is `IMyAddin` because it is specified as a parameter of the `Export` attribute.</span></span> <span data-ttu-id="31e32-125">所匯出的類型必須與合約類型相同、衍生自合約類型，或是實作合約類別 (如果是介面的話)。</span><span class="sxs-lookup"><span data-stu-id="31e32-125">The exported type must be either the same as the contract type, derive from the contract type, or implement the contract type if it is an interface.</span></span> <span data-ttu-id="31e32-126">在這個匯出中，實際類型 `MyLogger` 實作介面 `IMyAddin`。</span><span class="sxs-lookup"><span data-stu-id="31e32-126">In this export, the actual type `MyLogger` implements the interface `IMyAddin`.</span></span> <span data-ttu-id="31e32-127">合約名稱是從合約類型推斷而來，表示這個匯出符合前述匯入。</span><span class="sxs-lookup"><span data-stu-id="31e32-127">The contract name is inferred from the contract type, which means that this export will match the previous import.</span></span>

> [!NOTE]
> <span data-ttu-id="31e32-128">匯出和匯入通常應該在公用類別或成員上宣告。</span><span class="sxs-lookup"><span data-stu-id="31e32-128">Exports and imports should usually be declared on public classes or members.</span></span> <span data-ttu-id="31e32-129">其他宣告也受到支援，但匯出或匯入私用、受保護或內部成員會破壞組件的隔離模型，因此不建議這麼做。</span><span class="sxs-lookup"><span data-stu-id="31e32-129">Other declarations are supported, but exporting or importing a private, protected, or internal member breaks the isolation model for the part and is therefore not recommended.</span></span>

<span data-ttu-id="31e32-130">合約類型必須完全相符，才會將匯出和匯入視為相符。</span><span class="sxs-lookup"><span data-stu-id="31e32-130">The contract type must match exactly for the export and import to be considered a match.</span></span> <span data-ttu-id="31e32-131">請考慮下列匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-131">Consider the following export.</span></span>

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

<span data-ttu-id="31e32-132">在這個匯出中，合約類型為 `MyLogger` ，而不是 `IMyAddin`。</span><span class="sxs-lookup"><span data-stu-id="31e32-132">In this export, the contract type is `MyLogger` instead of `IMyAddin`.</span></span> <span data-ttu-id="31e32-133">即使 `MyLogger` 實作 `IMyAddin`，並因而轉換成 `IMyAddin` 物件，由於合約類型不同，這個匯出仍不符合前述匯入。</span><span class="sxs-lookup"><span data-stu-id="31e32-133">Even though `MyLogger` implements `IMyAddin`, and therefore could be cast to an `IMyAddin` object, this export will not match the previous import because the contract types are not the same.</span></span>

<span data-ttu-id="31e32-134">一般而言，您不一定要指定合約名稱，且大多數合約應該會以合約類型和中繼資料來定義。</span><span class="sxs-lookup"><span data-stu-id="31e32-134">In general, it is not necessary to specify the contract name, and most contracts should be defined in terms of the contract type and metadata.</span></span> <span data-ttu-id="31e32-135">但在特定情況下，您必須直接指定合約名稱。</span><span class="sxs-lookup"><span data-stu-id="31e32-135">However, under certain circumstances, it is important to specify the contract name directly.</span></span> <span data-ttu-id="31e32-136">最常見的情況就是在類別匯出數個共用常見類型 (例如基本類型) 的值時。</span><span class="sxs-lookup"><span data-stu-id="31e32-136">The most common case is when a class exports several values that share a common type, such as primitives.</span></span> <span data-ttu-id="31e32-137">合約名稱可以指定為 `Import` 或 `Export` 屬性的第一個參數。</span><span class="sxs-lookup"><span data-stu-id="31e32-137">The contract name can be specified as the first parameter of the `Import` or `Export` attribute.</span></span> <span data-ttu-id="31e32-138">下列程式碼顯示指定 `MajorRevision`之合約名稱的匯入和匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-138">The following code shows an import and an export with a specified contract name of `MajorRevision`.</span></span>

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

<span data-ttu-id="31e32-139">如果未指定合約類型，仍會從匯入或匯出的類型來推斷。</span><span class="sxs-lookup"><span data-stu-id="31e32-139">If the contract type is not specified, it will still be inferred from the type of the import or export.</span></span> <span data-ttu-id="31e32-140">不過，即使明確指定合約名稱，合約類型也必須完全相符，才會將匯入與匯出視為相符。</span><span class="sxs-lookup"><span data-stu-id="31e32-140">However, even if the contract name is specified explicitly, the contract type must also match exactly for the import and export to be considered a match.</span></span> <span data-ttu-id="31e32-141">例如，如果 `MajorRevision` 欄位是字串，則推斷的合約類型不符合，且即使匯出和匯入具有相同的合約名稱，也不會相符。</span><span class="sxs-lookup"><span data-stu-id="31e32-141">For example, if the `MajorRevision` field was a string, the inferred contract types would not match and the export would not match the import, despite having the same contract name.</span></span>

### <a name="importing-and-exporting-a-method"></a><span data-ttu-id="31e32-142">匯入及匯出方法</span><span class="sxs-lookup"><span data-stu-id="31e32-142">Importing and Exporting a Method</span></span>

<span data-ttu-id="31e32-143">`Export` 屬性 (Attribute) 也可使用與裝飾類別、屬性 (Property) 或函式的相同方式，來裝飾方法。</span><span class="sxs-lookup"><span data-stu-id="31e32-143">The `Export` attribute can also decorate a method, in the same way as a class, property, or function.</span></span> <span data-ttu-id="31e32-144">方法匯出由於無法推斷類型，因此必須指定合約類型或合約名稱。</span><span class="sxs-lookup"><span data-stu-id="31e32-144">Method exports must specify a contract type or contract name, as the type cannot be inferred.</span></span> <span data-ttu-id="31e32-145">指定的類型可以是自訂委派或泛型類型 (例如 `Func`)。</span><span class="sxs-lookup"><span data-stu-id="31e32-145">The specified type can be either a custom delegate or a generic type, such as `Func`.</span></span> <span data-ttu-id="31e32-146">下列類別會匯出名為 `DoSomething`的方法。</span><span class="sxs-lookup"><span data-stu-id="31e32-146">The following class exports a method named `DoSomething`.</span></span>

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
    [Export(typeof(Func<int, string>))]
    public string DoSomething(int TheParam);
}
```

<span data-ttu-id="31e32-147">在這個類別中， `DoSomething` 方法使用單一 `int` 參數並傳回 `string`。</span><span class="sxs-lookup"><span data-stu-id="31e32-147">In this class, the `DoSomething` method takes a single `int` parameter and returns a `string`.</span></span> <span data-ttu-id="31e32-148">若要符合這個匯出，匯入端組件必須宣告適當的成員。</span><span class="sxs-lookup"><span data-stu-id="31e32-148">To match this export, the importing part must declare an appropriate member.</span></span> <span data-ttu-id="31e32-149">下列類別會匯入 `DoSomething` 方法。</span><span class="sxs-lookup"><span data-stu-id="31e32-149">The following class imports the `DoSomething` method.</span></span>

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

<span data-ttu-id="31e32-150">如需如何使用 `Func<T, T>` 物件的詳細資訊，請參閱 <xref:System.Func%602>。</span><span class="sxs-lookup"><span data-stu-id="31e32-150">For more information about how to use of the `Func<T, T>` object, see <xref:System.Func%602>.</span></span>

<a name="types_of_imports"></a>

## <a name="types-of-imports"></a><span data-ttu-id="31e32-151">匯入類型</span><span class="sxs-lookup"><span data-stu-id="31e32-151">Types of Imports</span></span>

<span data-ttu-id="31e32-152">MEF 支援數種匯入類型，包括動態匯入、延遲匯入、先決條件匯入和選擇性匯入。</span><span class="sxs-lookup"><span data-stu-id="31e32-152">MEF support several import types, including dynamic, lazy, prerequisite, and optional.</span></span>

### <a name="dynamic-imports"></a><span data-ttu-id="31e32-153">動態匯入</span><span class="sxs-lookup"><span data-stu-id="31e32-153">Dynamic Imports</span></span>

<span data-ttu-id="31e32-154">在某些情況下，匯入端類別可能需要符合具有特定合約名稱之任何類型的匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-154">In some cases, the importing class may want to match exports of any type that have a particular contract name.</span></span> <span data-ttu-id="31e32-155">在此情況下，類別可宣告 *「動態匯入」*(Dynamic Import)。</span><span class="sxs-lookup"><span data-stu-id="31e32-155">In this scenario, the class can declare a *dynamic import*.</span></span> <span data-ttu-id="31e32-156">下列匯入符合具有合約名稱 "TheString" 的所有匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-156">The following import matches any export with contract name "TheString".</span></span>

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

<span data-ttu-id="31e32-157">當合約類型是從 `dynamic` 關鍵字推斷而來時，會符合所有合約類型。</span><span class="sxs-lookup"><span data-stu-id="31e32-157">When the contract type is inferred from the `dynamic` keyword, it will match any contract type.</span></span> <span data-ttu-id="31e32-158">在此範例中，匯入 **一律** 應指定要符合的合約名稱</span><span class="sxs-lookup"><span data-stu-id="31e32-158">In this case, an import should **always** specify a contract name to match on.</span></span> <span data-ttu-id="31e32-159">(如果未指定合約名稱，則會將匯入視為不符合任何匯出)。以下兩個匯出皆符合前述匯入。</span><span class="sxs-lookup"><span data-stu-id="31e32-159">(If no contract name is specified, the import will be considered to match no exports.) Both of the following exports would match the previous import.</span></span>

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

<span data-ttu-id="31e32-160">顯然地，匯入端類別必須能夠處理任何類型的物件。</span><span class="sxs-lookup"><span data-stu-id="31e32-160">Obviously, the importing class must be prepared to deal with an object of arbitrary type.</span></span>

### <a name="lazy-imports"></a><span data-ttu-id="31e32-161">延遲匯入</span><span class="sxs-lookup"><span data-stu-id="31e32-161">Lazy Imports</span></span>

<span data-ttu-id="31e32-162">在某些情況下，匯入端類別可能需要間接參考所匯入的物件，以避免立即具現化該物件。</span><span class="sxs-lookup"><span data-stu-id="31e32-162">In some cases, the importing class may require an indirect reference to the imported object, so that the object is not instantiated immediately.</span></span> <span data-ttu-id="31e32-163">在此情況下，類別會使用 *的合約類型來宣告* 「延遲匯入」 `Lazy<T>`(Lazy Import)。</span><span class="sxs-lookup"><span data-stu-id="31e32-163">In this scenario, the class can declare a *lazy import* by using a contract type of `Lazy<T>`.</span></span> <span data-ttu-id="31e32-164">下列匯入端屬性會宣告延遲匯入。</span><span class="sxs-lookup"><span data-stu-id="31e32-164">The following importing property declares a lazy import.</span></span>

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

<span data-ttu-id="31e32-165">對組合引擎來說， `Lazy<T>` 的合約類型與 `T`的合約類型會視為相同。</span><span class="sxs-lookup"><span data-stu-id="31e32-165">From the point of view of the composition engine, a contract type of `Lazy<T>` is considered identical to contract type of `T`.</span></span> <span data-ttu-id="31e32-166">因此，前述匯入會符合下列匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-166">Therefore, the previous import would match the following export.</span></span>

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

<span data-ttu-id="31e32-167">您可以在延遲匯入的 `Import` 屬性中指定合約名稱與合約類型，方法如稍早的＜匯入和匯出基本概念＞一節所述。</span><span class="sxs-lookup"><span data-stu-id="31e32-167">The contract name and contract type can be specified in the `Import` attribute for a lazy import, as described earlier in the "Basic Imports and Exports" section.</span></span>

### <a name="prerequisite-imports"></a><span data-ttu-id="31e32-168">先決條件匯入</span><span class="sxs-lookup"><span data-stu-id="31e32-168">Prerequisite Imports</span></span>

<span data-ttu-id="31e32-169">所匯出的 MEF 組件通常是由組合引擎所建立，不論是為了回應直接要求，或是為了應需要填入相符的匯入。</span><span class="sxs-lookup"><span data-stu-id="31e32-169">Exported MEF parts are typically created by the composition engine, in response to a direct request or the need to fill a matched import.</span></span> <span data-ttu-id="31e32-170">根據預設，建立組件時，組合引擎會使用沒有參數的建構函式。</span><span class="sxs-lookup"><span data-stu-id="31e32-170">By default, when creating a part, the composition engine uses the parameter-less constructor.</span></span> <span data-ttu-id="31e32-171">若要讓引擎使用不同的建構函式，您可以使用 `ImportingConstructor` 屬性來標記引擎。</span><span class="sxs-lookup"><span data-stu-id="31e32-171">To make the engine use a different constructor, you can mark it with the `ImportingConstructor` attribute.</span></span>

<span data-ttu-id="31e32-172">每個組件都只能有一個建構函式供組合引擎使用。</span><span class="sxs-lookup"><span data-stu-id="31e32-172">Each part may have only one constructor for use by the composition engine.</span></span> <span data-ttu-id="31e32-173">不提供預設建構函式和 `ImportingConstructor` 屬性，或是提供多個 `ImportingConstructor` 屬性，都會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="31e32-173">Providing no default constructor and no `ImportingConstructor` attribute, or providing more than one `ImportingConstructor` attribute, will produce an error.</span></span>

<span data-ttu-id="31e32-174">為了填入以 `ImportingConstructor` 屬性標記之建構函式的參數，所有參數都會自動以匯入的形式宣告。</span><span class="sxs-lookup"><span data-stu-id="31e32-174">To fill the parameters of a constructor marked with the `ImportingConstructor` attribute, all of those parameters are automatically declared as imports.</span></span> <span data-ttu-id="31e32-175">這種方法很方便用於宣告在組件初始設定期間使用的匯入。</span><span class="sxs-lookup"><span data-stu-id="31e32-175">This is a convenient way to declare imports that are used during part initialization.</span></span> <span data-ttu-id="31e32-176">下列類別使用 `ImportingConstructor` 來宣告匯入。</span><span class="sxs-lookup"><span data-stu-id="31e32-176">The following class uses `ImportingConstructor` to declare an import.</span></span>

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

<span data-ttu-id="31e32-177">根據預設， `ImportingConstructor` 屬性會針對所有參數匯入使用推斷的合約類型與合約名稱。</span><span class="sxs-lookup"><span data-stu-id="31e32-177">By default, the `ImportingConstructor` attribute uses inferred contract types and contract names for all of the parameter imports.</span></span> <span data-ttu-id="31e32-178">您可以覆寫此預設值，方法是以 `Import` 屬性裝飾參數，然後明確地定義合約類型與合約名稱。</span><span class="sxs-lookup"><span data-stu-id="31e32-178">It is possible to override this by decorating the parameters with `Import` attributes, which can then define the contract type and contract name explicitly.</span></span> <span data-ttu-id="31e32-179">下列程式碼示範使用此語法匯入衍生類別 (而不是父類別) 的建構函式。</span><span class="sxs-lookup"><span data-stu-id="31e32-179">The following code demonstrates a constructor that uses this syntax to import a derived class instead of a parent class.</span></span>

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

<span data-ttu-id="31e32-180">特別要提的是，處理集合參數時應小心。</span><span class="sxs-lookup"><span data-stu-id="31e32-180">In particular, you should be careful with collection parameters.</span></span> <span data-ttu-id="31e32-181">例如，如果您在具有 `ImportingConstructor` 類型之參數的建構函式上指定 `IEnumerable<int>`，則匯入會符合 `IEnumerable<int>`類型的單一匯出，而不是 `int`類型的一組匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-181">For example, if you specify `ImportingConstructor` on a constructor with a parameter of type `IEnumerable<int>`, the import will match a single export of type `IEnumerable<int>`, instead of a set of exports of type `int`.</span></span> <span data-ttu-id="31e32-182">若要符合 `int`類型的一組匯出，您必須以 `ImportMany` 屬性裝飾參數。</span><span class="sxs-lookup"><span data-stu-id="31e32-182">To match a set of exports of type `int`, you have to decorate the parameter with the `ImportMany` attribute.</span></span>

<span data-ttu-id="31e32-183">由 `ImportingConstructor` 屬性以匯入形式宣告的參數也會標記為「先決條件匯入」(Prerequisite Import)。</span><span class="sxs-lookup"><span data-stu-id="31e32-183">Parameters declared as imports by the `ImportingConstructor` attribute are also marked as *prerequisite imports*.</span></span> <span data-ttu-id="31e32-184">MEF 通常會允許匯出和匯入形成 *「循環」*(Cycle)。</span><span class="sxs-lookup"><span data-stu-id="31e32-184">MEF normally allows exports and imports to form a *cycle*.</span></span> <span data-ttu-id="31e32-185">例如，物件 A 會匯入物件 B，而物件 B 會匯入物件 A，這就是循環。在一般情況下，循環並不是問題，組合容器可以正常建構這兩個物件。</span><span class="sxs-lookup"><span data-stu-id="31e32-185">For example, a cycle is where object A imports object B, which in turn imports object A. Under ordinary circumstances, a cycle is not a problem, and the composition container constructs both objects normally.</span></span>

<span data-ttu-id="31e32-186">當某個組件的建構函式需要匯入的值時，該物件就不能參與循環。</span><span class="sxs-lookup"><span data-stu-id="31e32-186">When an imported value is required by the constructor of a part, that object cannot participate in a cycle.</span></span> <span data-ttu-id="31e32-187">如果物件 A 要求要等物件 B 建構後才能建構自己，而物件 B 會匯入物件 A，這個循環就無法解決而引發組合錯誤。</span><span class="sxs-lookup"><span data-stu-id="31e32-187">If object A requires that object B be constructed before it can be constructed itself, and object B imports object A, then the cycle will be unable to resolve and a composition error will occur.</span></span> <span data-ttu-id="31e32-188">因此，在建構函式參數上宣告的匯入是先決條件性匯入，也就是說，必須先填入這些匯入，才能從需要這些匯入的物件使用任何匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-188">Imports declared on constructor parameters are therefore prerequisite imports, which must all be filled before any of the exports from the object that requires them can be used.</span></span>

### <a name="optional-imports"></a><span data-ttu-id="31e32-189">選擇性匯入</span><span class="sxs-lookup"><span data-stu-id="31e32-189">Optional Imports</span></span>

<span data-ttu-id="31e32-190">`Import` 屬性指定要讓組件正常運作必須達到的需求。</span><span class="sxs-lookup"><span data-stu-id="31e32-190">The `Import` attribute specifies a requirement for the part to function.</span></span> <span data-ttu-id="31e32-191">如果無法完成匯入，則組合該組件會失敗，而組件會無法使用。</span><span class="sxs-lookup"><span data-stu-id="31e32-191">If an import cannot be fulfilled, the composition of that part will fail and the part will not be available.</span></span>

<span data-ttu-id="31e32-192">您可以使用 *屬性，將匯入指定為* 「選擇性」 `AllowDefault` (Optional) 匯入。</span><span class="sxs-lookup"><span data-stu-id="31e32-192">You can specify that an import is *optional* by using the `AllowDefault` property.</span></span> <span data-ttu-id="31e32-193">在此情況下，即使匯入不符合任何可用的匯出，組合也會成功，並且匯入端屬性會設定為其屬性類型的預設值 (如果是物件屬性則為 `null`，如果是布林值屬性則為 `false`，如果是數值屬性則為零)。下列類別使用選擇性匯入。</span><span class="sxs-lookup"><span data-stu-id="31e32-193">In this case, the composition will succeed even if the import does not match any available exports, and the importing property will be set to the default for its property type (`null` for object properties, `false` for Booleans, or zero for numeric properties.) The following class uses an optional import.</span></span>

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

    //If no matching export is available,
    //thePlugin will be set to null.
}
```

### <a name="importing-multiple-objects"></a><span data-ttu-id="31e32-194">匯入多個物件</span><span class="sxs-lookup"><span data-stu-id="31e32-194">Importing Multiple Objects</span></span>

<span data-ttu-id="31e32-195">`Import` 屬性必須剛好符合一個匯出，才能順利組合。</span><span class="sxs-lookup"><span data-stu-id="31e32-195">The `Import` attribute will only be successfully composed when it matches one and only one export.</span></span> <span data-ttu-id="31e32-196">其他情況將會產生組合錯誤。</span><span class="sxs-lookup"><span data-stu-id="31e32-196">Other cases will produce a composition error.</span></span> <span data-ttu-id="31e32-197">若要匯入多個與同一個合約相符的匯出，請使用 `ImportMany` 屬性。</span><span class="sxs-lookup"><span data-stu-id="31e32-197">To import more than one export that matches the same contract, use the `ImportMany` attribute.</span></span> <span data-ttu-id="31e32-198">以這個屬性標記的匯入一律會是選擇性匯入。</span><span class="sxs-lookup"><span data-stu-id="31e32-198">Imports marked with this attribute are always optional.</span></span> <span data-ttu-id="31e32-199">例如，即使沒有相符的匯出，組合也不會失敗。</span><span class="sxs-lookup"><span data-stu-id="31e32-199">For example, composition will not fail if no matching exports are present.</span></span> <span data-ttu-id="31e32-200">下列類別會匯入 `IMyAddin`類型之任意數目的匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-200">The following class imports any number of exports of type `IMyAddin`.</span></span>

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

<span data-ttu-id="31e32-201">使用一般的 `IEnumerable<T>` 語法和方法，即可存取所匯入的陣列。</span><span class="sxs-lookup"><span data-stu-id="31e32-201">The imported array can be accessed by using ordinary `IEnumerable<T>` syntax and methods.</span></span> <span data-ttu-id="31e32-202">另外，也可以改用一般陣列 (`IMyAddin[]`)。</span><span class="sxs-lookup"><span data-stu-id="31e32-202">It is also possible to use an ordinary array (`IMyAddin[]`) instead.</span></span>

<span data-ttu-id="31e32-203">搭配 `Lazy<T>` 語法一起使用時，這個模式非常重要。</span><span class="sxs-lookup"><span data-stu-id="31e32-203">This pattern can be very important when you use it in combination with the `Lazy<T>` syntax.</span></span> <span data-ttu-id="31e32-204">例如，您可以使用 `ImportMany`、 `IEnumerable<T>`和 `Lazy<T>`匯入任意數目之物件的間接參考，然後只具現化成為必要的物件。</span><span class="sxs-lookup"><span data-stu-id="31e32-204">For example, by using `ImportMany`, `IEnumerable<T>`, and `Lazy<T>`, you can import indirect references to any number of objects and only instantiate the ones that become necessary.</span></span> <span data-ttu-id="31e32-205">下列類別示範這個模式。</span><span class="sxs-lookup"><span data-stu-id="31e32-205">The following class shows this pattern.</span></span>

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

## <a name="avoiding-discovery"></a><span data-ttu-id="31e32-206">避免探索</span><span class="sxs-lookup"><span data-stu-id="31e32-206">Avoiding Discovery</span></span>

<span data-ttu-id="31e32-207">在某些情況下，您可能不想讓組件被當做目錄的一部分來探索。</span><span class="sxs-lookup"><span data-stu-id="31e32-207">In some cases, you may want to prevent a part from being discovered as part of a catalog.</span></span> <span data-ttu-id="31e32-208">例如，您可能想讓組件成為用於繼承的基底類別，而不直接使用。</span><span class="sxs-lookup"><span data-stu-id="31e32-208">For example, the part may be a base class intended to be inherited from, but not used.</span></span> <span data-ttu-id="31e32-209">有兩種方法可達成這個目標。</span><span class="sxs-lookup"><span data-stu-id="31e32-209">There are two ways to accomplish this.</span></span> <span data-ttu-id="31e32-210">第一種方法是在組件類別上使用 `abstract` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="31e32-210">First, you can use the `abstract` keyword on the part class.</span></span> <span data-ttu-id="31e32-211">抽象類別絕不會提供匯出，但是可以提供繼承的匯出給衍生自抽象類別的類別。</span><span class="sxs-lookup"><span data-stu-id="31e32-211">Abstract classes never provide exports, although they can provide inherited exports to classes that derive from them.</span></span>

<span data-ttu-id="31e32-212">如果無法將類別變成抽象類別，您可以使用 `PartNotDiscoverable` 屬性加以裝飾。</span><span class="sxs-lookup"><span data-stu-id="31e32-212">If the class cannot be made abstract, you can decorate it with the `PartNotDiscoverable` attribute.</span></span> <span data-ttu-id="31e32-213">使用這個屬性裝飾的組件將不會包含在任何目錄中。</span><span class="sxs-lookup"><span data-stu-id="31e32-213">A part decorated with this attribute will not be included in any catalogs.</span></span> <span data-ttu-id="31e32-214">下列範例示範這些模式。</span><span class="sxs-lookup"><span data-stu-id="31e32-214">The following example demonstrates these patterns.</span></span> <span data-ttu-id="31e32-215">目錄會探索到`DataOne` 。</span><span class="sxs-lookup"><span data-stu-id="31e32-215">`DataOne` will be discovered by the catalog.</span></span> <span data-ttu-id="31e32-216">由於 `DataTwo` 是抽象的，因此不會被探索到。</span><span class="sxs-lookup"><span data-stu-id="31e32-216">Since `DataTwo` is abstract, it will not be discovered.</span></span> <span data-ttu-id="31e32-217">由於 `DataThree` 使用 `PartNotDiscoverable` 屬性，因此不會被探索到。</span><span class="sxs-lookup"><span data-stu-id="31e32-217">Since `DataThree` used the `PartNotDiscoverable` attribute, it will not be discovered.</span></span>

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

## <a name="metadata-and-metadata-views"></a><span data-ttu-id="31e32-218">中繼資料和中繼資料檢視</span><span class="sxs-lookup"><span data-stu-id="31e32-218">Metadata and Metadata Views</span></span>

<span data-ttu-id="31e32-219">匯出可以提供有關本身的其他資訊，也稱為 *「中繼資料」*(Metadata)。</span><span class="sxs-lookup"><span data-stu-id="31e32-219">Exports can provide additional information about themselves known as *metadata*.</span></span> <span data-ttu-id="31e32-220">中繼資料可用來將所匯出物件的屬性傳送至匯入端組件。</span><span class="sxs-lookup"><span data-stu-id="31e32-220">Metadata can be used to convey properties of the exported object to the importing part.</span></span> <span data-ttu-id="31e32-221">匯入端組件可使用此資料來決定要使用的匯出，或是蒐集匯出相關資訊，而不必建構匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-221">The importing part can use this data to decide which exports to use, or to gather information about an export without having to construct it.</span></span> <span data-ttu-id="31e32-222">因此，匯入必須是延遲匯入才能使用中繼資料。</span><span class="sxs-lookup"><span data-stu-id="31e32-222">For this reason, an import must be lazy to use metadata.</span></span>

<span data-ttu-id="31e32-223">為了使用中繼資料，您通常會宣告一個稱為 *「中繼資料檢視」*(Metadata View) 的介面，該介面會宣告可以使用哪些中繼資料。</span><span class="sxs-lookup"><span data-stu-id="31e32-223">To use metadata, you typically declare an interface known as a *metadata view*, which declares what metadata will be available.</span></span> <span data-ttu-id="31e32-224">中繼資料檢視介面必須只有屬性，而這些屬性必須具有 `get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="31e32-224">The metadata view interface must have only properties, and those properties must have `get` accessors.</span></span> <span data-ttu-id="31e32-225">下列介面是中繼資料檢視範例。</span><span class="sxs-lookup"><span data-stu-id="31e32-225">The following interface is an example metadata view.</span></span>

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

<span data-ttu-id="31e32-226">您也可以使用泛型集合 `IDictionary<string, object>`做為中繼資料檢視，但是這樣會享受不到類型檢查的好處，應該加以避免。</span><span class="sxs-lookup"><span data-stu-id="31e32-226">It is also possible to use a generic collection, `IDictionary<string, object>`, as a metadata view, but this forfeits the benefits of type checking and should be avoided.</span></span>

<span data-ttu-id="31e32-227">一般而言，中繼資料檢視中具名的所有屬性都是必要屬性，未提供這些屬性的匯出將會視為不相符。</span><span class="sxs-lookup"><span data-stu-id="31e32-227">Ordinarily, all of the properties named in the metadata view are required, and any exports that do not provide them will not be considered a match.</span></span> <span data-ttu-id="31e32-228">`DefaultValue` 屬性 (Attribute) 指定某個屬性 (Property) 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="31e32-228">The `DefaultValue` attribute specifies that a property is optional.</span></span> <span data-ttu-id="31e32-229">如果未納入該屬性 (Property)，則會指派指定的預設值做為 `DefaultValue`的參數。</span><span class="sxs-lookup"><span data-stu-id="31e32-229">If the property is not included, it will be assigned the default value specified as a parameter of `DefaultValue`.</span></span> <span data-ttu-id="31e32-230">以下是以中繼資料裝飾的兩個不同類別。</span><span class="sxs-lookup"><span data-stu-id="31e32-230">The following are two different classes decorated with metadata.</span></span> <span data-ttu-id="31e32-231">這兩個類別都符合前述中繼資料檢視。</span><span class="sxs-lookup"><span data-stu-id="31e32-231">Both of these classes would match the previous metadata view.</span></span>

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

<span data-ttu-id="31e32-232">中繼資料會在 `Export` 屬性後面以 `ExportMetadata` 屬性表示。</span><span class="sxs-lookup"><span data-stu-id="31e32-232">Metadata is expressed after the `Export` attribute by using the `ExportMetadata` attribute.</span></span> <span data-ttu-id="31e32-233">每項中繼資料都是由名稱/值組所組成。</span><span class="sxs-lookup"><span data-stu-id="31e32-233">Each piece of metadata is composed of a name/value pair.</span></span> <span data-ttu-id="31e32-234">中繼資料的名稱部分必須符合中繼資料檢視中適當屬性 (Property) 的名稱，並為該屬性指派值。</span><span class="sxs-lookup"><span data-stu-id="31e32-234">The name portion of the metadata must match the name of the appropriate property in the metadata view, and the value will be assigned to that property.</span></span>

<span data-ttu-id="31e32-235">匯入者可指定要使用的中繼資料檢視 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="31e32-235">It is the importer that specifies what metadata view, if any, will be in use.</span></span> <span data-ttu-id="31e32-236">具有中繼資料的匯入會以延遲匯入的形式宣告，並以中繼資料介面做為 `Lazy<T,T>`的第二個類型參數。</span><span class="sxs-lookup"><span data-stu-id="31e32-236">An import with metadata is declared as a lazy import, with the metadata interface as the second type parameter to `Lazy<T,T>`.</span></span> <span data-ttu-id="31e32-237">下列類別會匯入具有中繼資料的前述組件。</span><span class="sxs-lookup"><span data-stu-id="31e32-237">The following class imports the previous part with metadata.</span></span>

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

<span data-ttu-id="31e32-238">在許多情況下，您會想要將中繼資料與 `ImportMany` 屬性結合，以便剖析多個可用的匯入，然後只選擇並具現化某個匯入，或者是篩選集合中符合特定條件的項目。</span><span class="sxs-lookup"><span data-stu-id="31e32-238">In many cases, you will want to combine metadata with the `ImportMany` attribute, in order to parse through the available imports and choose and instantiate only one, or filter a collection to match a certain condition.</span></span> <span data-ttu-id="31e32-239">下列類別只會具現化 `IPlugin` 值為 "Logger" 的 `Name` 物件。</span><span class="sxs-lookup"><span data-stu-id="31e32-239">The following class instantiates only `IPlugin` objects that have the `Name` value "Logger".</span></span>

```vb
Public Class User

    <ImportMany()>
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))

    Public Function InstantiateLogger() As IPlugin

        Dim logger As IPlugin
        logger = Nothing

        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins
            If Plugin.Metadata.Name = "Logger" Then
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

    public IPlugin InstantiateLogger()
    {
        IPlugin logger = null;

        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)
        {
            if (plugin.Metadata.Name == "Logger")
                logger = plugin.Value;
        }
        return logger;
    }
}
```

<a name="import_and_export_inheritance"></a>

## <a name="import-and-export-inheritance"></a><span data-ttu-id="31e32-240">匯入及匯出繼承</span><span class="sxs-lookup"><span data-stu-id="31e32-240">Import and Export Inheritance</span></span>

<span data-ttu-id="31e32-241">如果類別繼承自某個組件，則該類別也可能會變成組件。</span><span class="sxs-lookup"><span data-stu-id="31e32-241">If a class inherits from a part, that class may also become a part.</span></span> <span data-ttu-id="31e32-242">子類別一律會繼承匯入。</span><span class="sxs-lookup"><span data-stu-id="31e32-242">Imports are always inherited by subclasses.</span></span> <span data-ttu-id="31e32-243">因此，組件的子類別一律會是組件，因為其具有和父類別相同的匯入。</span><span class="sxs-lookup"><span data-stu-id="31e32-243">Therefore, a subclass of a part will always be a part, with the same imports as its parent class.</span></span>

<span data-ttu-id="31e32-244">子類別不會繼承以 `Export` 屬性宣告的匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-244">Exports declared by using the `Export` attribute are not inherited by subclasses.</span></span> <span data-ttu-id="31e32-245">不過，組件可以使用 `InheritedExport` 屬性來匯出自己。</span><span class="sxs-lookup"><span data-stu-id="31e32-245">However, a part can export itself by using the `InheritedExport` attribute.</span></span> <span data-ttu-id="31e32-246">組件的子類別會繼承並提供同一個匯出，包括合約名稱與合約類型。</span><span class="sxs-lookup"><span data-stu-id="31e32-246">Subclasses of the part will inherit and provide the same export, including contract name and contract type.</span></span> <span data-ttu-id="31e32-247">與 `Export` 屬性不同的是， `InheritedExport` 只能在類別層級套用，而不能在成員層級套用。</span><span class="sxs-lookup"><span data-stu-id="31e32-247">Unlike an `Export` attribute, `InheritedExport` can be applied only at the class level, and not at the member level.</span></span> <span data-ttu-id="31e32-248">因此，永遠無法繼承成員層級的匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-248">Therefore, member-level exports can never be inherited.</span></span>

<span data-ttu-id="31e32-249">下列四個類別示範匯入和匯出的繼承原則。</span><span class="sxs-lookup"><span data-stu-id="31e32-249">The following four classes demonstrate the principles of import and export inheritance.</span></span> <span data-ttu-id="31e32-250">`NumTwo` 繼承自 `NumOne`，因此 `NumTwo` 會匯入 `IMyData`。</span><span class="sxs-lookup"><span data-stu-id="31e32-250">`NumTwo` inherits from `NumOne`, so `NumTwo` will import `IMyData`.</span></span> <span data-ttu-id="31e32-251">由於不會繼承一般匯出，因此 `NumTwo` 不會匯出任何項目。</span><span class="sxs-lookup"><span data-stu-id="31e32-251">Ordinary exports are not inherited, so `NumTwo` will not export anything.</span></span> <span data-ttu-id="31e32-252">`NumFour` 繼承自 `NumThree`。</span><span class="sxs-lookup"><span data-stu-id="31e32-252">`NumFour` inherits from `NumThree`.</span></span> <span data-ttu-id="31e32-253">由於 `NumThree` 使用 `InheritedExport`，因此 `NumFour` 有一個具有合約類型 `NumThree`的匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-253">Because `NumThree` used `InheritedExport`, `NumFour` has one export with contract type `NumThree`.</span></span> <span data-ttu-id="31e32-254">由於絕不會繼承成員層級的匯出，因此不會匯出 `IMyData` 。</span><span class="sxs-lookup"><span data-stu-id="31e32-254">Member-level exports are never inherited, so `IMyData` is not exported.</span></span>

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

<span data-ttu-id="31e32-255">如果 `InheritedExport` 屬性有相關聯的中繼資料，也會繼承該中繼資料</span><span class="sxs-lookup"><span data-stu-id="31e32-255">If there is metadata associated with an `InheritedExport` attribute, that metadata will also be inherited.</span></span> <span data-ttu-id="31e32-256">(如需詳細資訊，請參閱稍早的＜中繼資料和中繼資料檢視＞一節)。子類別無法修改所繼承的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="31e32-256">(For more information, see the earlier "Metadata and Metadata Views" section.) Inherited metadata cannot be modified by the subclass.</span></span> <span data-ttu-id="31e32-257">不過，子類別可以藉由重新宣告具有相同合約名稱與合約類型 (但使用新的中繼資料) 的 `InheritedExport` ，以新的中繼資料來取代繼承的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="31e32-257">However, by re-declaring the `InheritedExport` attribute with the same contract name and contract type, but with new metadata, the subclass can replace the inherited metadata with new metadata.</span></span> <span data-ttu-id="31e32-258">下列類別示範這個原則。</span><span class="sxs-lookup"><span data-stu-id="31e32-258">The following class demonstrates this principle.</span></span> <span data-ttu-id="31e32-259">`MegaLogger` 組件繼承自 `Logger` 並包含 `InheritedExport` 屬性。</span><span class="sxs-lookup"><span data-stu-id="31e32-259">The `MegaLogger` part inherits from `Logger` and includes the `InheritedExport` attribute.</span></span> <span data-ttu-id="31e32-260">由於 `MegaLogger` 重新宣告名為 Status 的新中繼資料，因此不會從 `Logger`繼承 Name 和 Version 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="31e32-260">Since `MegaLogger` re-declares new metadata named Status, it does not inherit the Name and Version metadata from `Logger`.</span></span>

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

<span data-ttu-id="31e32-261">當您重新宣告 `InheritedExport` 屬性以覆寫中繼資料時，請確定合約類型相同。</span><span class="sxs-lookup"><span data-stu-id="31e32-261">When re-declaring the `InheritedExport` attribute to override metadata, make sure that the contract types are the same.</span></span> <span data-ttu-id="31e32-262">(在上述範例中，合約類型是 `IPlugin`)。如果合約類型不同，則第二個屬性會從組件建立第二個獨立的匯出，而不是覆寫原有的匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-262">(In the previous example, `IPlugin` is the contract type.) If they differ, instead of overriding, the second attribute will create a second, independent export from the part.</span></span> <span data-ttu-id="31e32-263">一般而言，這表示當您覆寫 `InheritedExport` 屬性時，您必須明確指定合約類型，如上述範例所示。</span><span class="sxs-lookup"><span data-stu-id="31e32-263">Generally, this means that you will have to explicitly specify the contract type when you override an `InheritedExport` attribute, as shown in the previous example.</span></span>

<span data-ttu-id="31e32-264">由於無法直接具現化介面，因此通常無法以 `Export` 或 `Import` 屬性裝飾介面。</span><span class="sxs-lookup"><span data-stu-id="31e32-264">Since interfaces cannot be instantiated directly, they generally cannot be decorated with `Export` or `Import` attributes.</span></span> <span data-ttu-id="31e32-265">不過，您可以在介面層級以 `InheritedExport` 屬性裝飾介面，然後該匯出與所有相關聯的中繼資料就會由任何實作端類別所繼承。</span><span class="sxs-lookup"><span data-stu-id="31e32-265">However, an interface can be decorated with an `InheritedExport` attribute at the interface level, and that export along with any associated metadata will be inherited by any implementing classes.</span></span> <span data-ttu-id="31e32-266">但是，介面本身無法當做組件使用。</span><span class="sxs-lookup"><span data-stu-id="31e32-266">The interface itself will not be available as a part, however.</span></span>

<a name="custom_export_attributes"></a>

## <a name="custom-export-attributes"></a><span data-ttu-id="31e32-267">自訂匯出屬性</span><span class="sxs-lookup"><span data-stu-id="31e32-267">Custom Export Attributes</span></span>

<span data-ttu-id="31e32-268">您可以擴充基本的匯出屬性 `Export` 和 `InheritedExport`，以納入中繼資料做為屬性 (Attribute) 的屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="31e32-268">The basic export attributes, `Export` and `InheritedExport`, can be extended to include metadata as attribute properties.</span></span> <span data-ttu-id="31e32-269">要將類似的中繼資料套用至許多組件，或是建立中繼資料屬性的繼承樹時，這個做法會很有用。</span><span class="sxs-lookup"><span data-stu-id="31e32-269">This technique is useful for applying similar metadata to many parts, or creating an inheritance tree of metadata attributes.</span></span>

<span data-ttu-id="31e32-270">自訂屬性可以指定合約類型、合約名稱或其他任何中繼資料。</span><span class="sxs-lookup"><span data-stu-id="31e32-270">A custom attribute can specify the contract type, the contract name, or any other metadata.</span></span> <span data-ttu-id="31e32-271">若要定義自訂屬性，必須以 `ExportAttribute` 屬性裝飾從 `InheritedExportAttribute`(或 `MetadataAttribute` ) 繼承的類別。</span><span class="sxs-lookup"><span data-stu-id="31e32-271">In order to define a custom attribute, a class inheriting from `ExportAttribute` (or `InheritedExportAttribute`) must be decorated with the `MetadataAttribute` attribute.</span></span> <span data-ttu-id="31e32-272">下列類別會定義自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="31e32-272">The following class defines a custom attribute.</span></span>

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

<span data-ttu-id="31e32-273">這個類別使用合約類型 `MyAttribute` 和某個名為 `IMyData` 的中繼資料，定義名為 `MyMetadata`的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="31e32-273">This class defines a custom attribute named `MyAttribute` with contract type `IMyData` and some metadata named `MyMetadata`.</span></span> <span data-ttu-id="31e32-274">類別中以 `MetadataAttribute` 屬性 (Attribute) 標記的所有屬性 (Property)，都會視為在自訂屬性 (Attribute) 中定義的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="31e32-274">All properties in a class marked with the `MetadataAttribute` attribute are considered to be metadata defined in the custom attribute.</span></span> <span data-ttu-id="31e32-275">下列兩個宣告的用法是相同的。</span><span class="sxs-lookup"><span data-stu-id="31e32-275">The following two declarations are equivalent.</span></span>

```vb
<Export(GetType(IMyAddin))>
<ExportMetadata("MyMetadata", "theData")>
Public Property myAddin As MyAddin
```

```vb
<MyAttribute("theData")>
Public Property myAddin As MyAddin
```

```csharp
[Export(typeof(IMyAddin)),
    ExportMetadata("MyMetadata", "theData")]
public MyAddin myAddin { get; set; }
```

```csharp
[MyAttribute("theData")]
public MyAddin myAddin { get; set; }
```

<span data-ttu-id="31e32-276">在第一個宣告中，已明確定義合約類型和中繼資料。</span><span class="sxs-lookup"><span data-stu-id="31e32-276">In the first declaration, the contract type and metadata are explicitly defined.</span></span> <span data-ttu-id="31e32-277">在第二個宣告中，合約類型和中繼資料隱含在自訂的屬性中。</span><span class="sxs-lookup"><span data-stu-id="31e32-277">In the second declaration, the contract type and metadata are implicit in the customized attribute.</span></span> <span data-ttu-id="31e32-278">特別是在必須將大量相同的中繼資料套用至許多組件 (例如，作者或著作權資訊) 的情況下，使用自訂屬性可以節省許多時間，而且避免一再執行重複的動作。</span><span class="sxs-lookup"><span data-stu-id="31e32-278">Particularly in cases where a large amount of identical metadata must be applied to many parts (for example, author or copyright information), using a custom attribute can save a lot of time and duplication.</span></span> <span data-ttu-id="31e32-279">另外，還可以建立自訂屬性的繼承樹，以允許更多變化。</span><span class="sxs-lookup"><span data-stu-id="31e32-279">Further, inheritance trees of custom attributes can be created to allow for variations.</span></span>

<span data-ttu-id="31e32-280">若要在自訂屬性中建立選擇性中繼資料，您可以使用 `DefaultValue` 屬性。</span><span class="sxs-lookup"><span data-stu-id="31e32-280">To create optional metadata in a custom attribute, you can use the `DefaultValue` attribute.</span></span> <span data-ttu-id="31e32-281">當這個屬性 (Attribute) 套用至自訂屬性 (Attribute) 類別中的某個屬性 (Property) 時，會將裝飾的屬性 (Property) 指定為匯出者不一定要提供的選擇性屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="31e32-281">When this attribute is applied to a property in a custom attribute class, it specifies that the decorated property is optional and does not have to be supplied by an exporter.</span></span> <span data-ttu-id="31e32-282">如果未提供屬性 (Property) 的值，則會將屬性類型的預設值 (通常是 `null`、 `false`或 0) 指派給該屬性。</span><span class="sxs-lookup"><span data-stu-id="31e32-282">If a value for the property is not supplied, it will be assigned the default value for its property type (usually `null`, `false`, or 0.)</span></span>

<a name="creation_policies"></a>

## <a name="creation-policies"></a><span data-ttu-id="31e32-283">建立原則</span><span class="sxs-lookup"><span data-stu-id="31e32-283">Creation Policies</span></span>

<span data-ttu-id="31e32-284">當組件指定匯入並執行組合時，組合容器會嘗試尋找相符的匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-284">When a part specifies an import and composition is performed, the composition container attempts to find a matching export.</span></span> <span data-ttu-id="31e32-285">如果匯入成功符合匯出，便會將匯入端成員設定為所匯出物件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="31e32-285">If it matches the import with an export successfully, the importing member is set to an instance of the exported object.</span></span> <span data-ttu-id="31e32-286">這個執行個體的來源是由匯出端組件的 *「建立原則」*(Creation Policy) 所控制。</span><span class="sxs-lookup"><span data-stu-id="31e32-286">Where this instance comes from is controlled by the exporting part's *creation policy*.</span></span>

<span data-ttu-id="31e32-287">兩個可能的建立原則為 *「共用」* (Shared) 和 *「非共用」*(Non-Shared)。</span><span class="sxs-lookup"><span data-stu-id="31e32-287">The two possible creation policies are *shared* and *non-shared*.</span></span> <span data-ttu-id="31e32-288">具有共用建立原則的組件會在具有該合約之組件的容器中供每個匯入共用。</span><span class="sxs-lookup"><span data-stu-id="31e32-288">A part with a creation policy of shared will be shared between every import in the container for a part with that contract.</span></span> <span data-ttu-id="31e32-289">當組合引擎在找到相符項而必須設定匯入端屬性時，會具現化新的組件複本 (如果尚未存在任何複本)，或是提供現有的複本。</span><span class="sxs-lookup"><span data-stu-id="31e32-289">When the composition engine finds a match and has to set an importing property, it will instantiate a new copy of the part only if one does not already exist; otherwise, it will supply the existing copy.</span></span> <span data-ttu-id="31e32-290">這表示可能有許多物件參考同一個組件。</span><span class="sxs-lookup"><span data-stu-id="31e32-290">This means that many objects may have references to the same part.</span></span> <span data-ttu-id="31e32-291">這類組件不應該依賴可能會由多個位置變更的內部狀態。</span><span class="sxs-lookup"><span data-stu-id="31e32-291">Such parts should not rely on internal state that might be changed from many places.</span></span> <span data-ttu-id="31e32-292">此原則適用於靜態組件、提供服務的組件，以及耗用大量記憶體或其他資源的組件。</span><span class="sxs-lookup"><span data-stu-id="31e32-292">This policy is appropriate for static parts, parts that provide services, and parts that consume a lot of memory or other resources.</span></span>

<span data-ttu-id="31e32-293">每次找到其中一個匯出的相符匯入，都會建立具有非共用建立原則的組件。</span><span class="sxs-lookup"><span data-stu-id="31e32-293">A part with the creation policy of non-shared will be created every time a matching import for one of its exports is found.</span></span> <span data-ttu-id="31e32-294">因此，系統會為容器中每個符合該組件之其中一個匯出合約的匯入，各具現化一個新的複本。</span><span class="sxs-lookup"><span data-stu-id="31e32-294">A new copy will therefore be instantiated for every import in the container that matches one of the part's exported contracts.</span></span> <span data-ttu-id="31e32-295">這些複本的內部狀態不會受到共用。</span><span class="sxs-lookup"><span data-stu-id="31e32-295">The internal state of these copies will not be shared.</span></span> <span data-ttu-id="31e32-296">此原則適用於其中每個匯入都需要專屬內部狀態的組件。</span><span class="sxs-lookup"><span data-stu-id="31e32-296">This policy is appropriate for parts where each import requires its own internal state.</span></span>

<span data-ttu-id="31e32-297">匯入和匯出都可以指定組件的建立原則，其值包含 `Shared`、 `NonShared`或 `Any`。</span><span class="sxs-lookup"><span data-stu-id="31e32-297">Both the import and the export can specify the creation policy of a part, from among the values `Shared`, `NonShared`, or `Any`.</span></span> <span data-ttu-id="31e32-298">對於匯入和匯出而言，預設值皆為 `Any` 。</span><span class="sxs-lookup"><span data-stu-id="31e32-298">The default is `Any` for both imports and exports.</span></span> <span data-ttu-id="31e32-299">指定 `Shared` 或 `NonShared` 的匯出，只會符合指定相同值或是指定 `Any`的匯入。</span><span class="sxs-lookup"><span data-stu-id="31e32-299">An export that specifies `Shared` or `NonShared` will only match an import that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="31e32-300">同樣地，指定 `Shared` 或 `NonShared` 的匯入，只會符合指定相同值或是指定 `Any`的匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-300">Similarly, an import that specifies `Shared` or `NonShared` will only match an export that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="31e32-301">就像是合約名稱或合約類型不同的匯入和匯出不會相符一樣，建立原則不相容的匯入和匯出也不會視為相符。</span><span class="sxs-lookup"><span data-stu-id="31e32-301">Imports and exports with incompatible creation policies are not considered a match, in the same way as an import and export whose contract name or contract type are not a match.</span></span> <span data-ttu-id="31e32-302">如果匯入和匯出都指定 `Any`，或是因未指定建立原則而預設為 `Any`，則建立原則會預設為共用。</span><span class="sxs-lookup"><span data-stu-id="31e32-302">If both import and export specify `Any`, or do not specify a creation policy and default to `Any`, the creation policy will default to shared.</span></span>

<span data-ttu-id="31e32-303">下列範例示範指定建立原則的匯入和匯出。</span><span class="sxs-lookup"><span data-stu-id="31e32-303">The following example shows both imports and exports specifying creation policies.</span></span> <span data-ttu-id="31e32-304">`PartOne` 未指定建立原則，因此預設值為 `Any`。</span><span class="sxs-lookup"><span data-stu-id="31e32-304">`PartOne` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="31e32-305">`PartTwo` 未指定建立原則，因此預設值為 `Any`。</span><span class="sxs-lookup"><span data-stu-id="31e32-305">`PartTwo` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="31e32-306">由於匯入和匯出都預設為 `Any`，因此會共用 `PartOne` 。</span><span class="sxs-lookup"><span data-stu-id="31e32-306">Since both import and export default to `Any`, `PartOne` will be shared.</span></span> <span data-ttu-id="31e32-307">`PartThree` 指定 `Shared` 建立原則，因此 `PartTwo` 和 `PartThree` 會共用相同的 `PartOne`複本。</span><span class="sxs-lookup"><span data-stu-id="31e32-307">`PartThree` specifies a `Shared` creation policy, so `PartTwo` and `PartThree` will share the same copy of `PartOne`.</span></span> <span data-ttu-id="31e32-308">`PartFour` 指定 `NonShared` 建立原則，因此 `PartFour` 在 `PartFive`中不會共用。</span><span class="sxs-lookup"><span data-stu-id="31e32-308">`PartFour` specifies a `NonShared` creation policy, so `PartFour` will be non-shared in `PartFive`.</span></span> <span data-ttu-id="31e32-309">`PartSix` 指定 `NonShared` 建立原則。</span><span class="sxs-lookup"><span data-stu-id="31e32-309">`PartSix` specifies a `NonShared` creation policy.</span></span> <span data-ttu-id="31e32-310">`PartFive` 和 `PartSix` 將收到個別的 `PartFour`複本。</span><span class="sxs-lookup"><span data-stu-id="31e32-310">`PartFive` and `PartSix` will each receive separate copies of `PartFour`.</span></span> <span data-ttu-id="31e32-311">`PartSeven` 指定 `Shared` 建立原則。</span><span class="sxs-lookup"><span data-stu-id="31e32-311">`PartSeven` specifies a `Shared` creation policy.</span></span> <span data-ttu-id="31e32-312">由於沒有具有 `PartFour` 建立原則的已匯出 `Shared`，因此 `PartSeven` 匯入不符合任何項目，並且不會被填入。</span><span class="sxs-lookup"><span data-stu-id="31e32-312">Because there is no exported `PartFour` with a creation policy of `Shared`, the `PartSeven` import does not match anything and will not be filled.</span></span>

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
    'Since the export's creation policy was explicitly
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
    //Since the export's creation policy was explicitly
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

## <a name="life-cycle-and-disposing"></a><span data-ttu-id="31e32-313">生命週期和處置</span><span class="sxs-lookup"><span data-stu-id="31e32-313">Life Cycle and Disposing</span></span>

<span data-ttu-id="31e32-314">由於組件裝載於組合容器中，因此其生命週期可能比一般物件更複雜。</span><span class="sxs-lookup"><span data-stu-id="31e32-314">Because parts are hosted in the composition container, their life cycle can be more complex than ordinary objects.</span></span> <span data-ttu-id="31e32-315">組件可以實作兩個與生命週期相關的重要介面： `IDisposable` 和 `IPartImportsSatisfiedNotification`。</span><span class="sxs-lookup"><span data-stu-id="31e32-315">Parts can implement two important life cycle-related interfaces: `IDisposable` and `IPartImportsSatisfiedNotification`.</span></span>

<span data-ttu-id="31e32-316">如同一般的 .NET Framework 物件，需要在關閉時執行工作的組件，或是需要釋放資源的組件，都應該實作 `IDisposable`。</span><span class="sxs-lookup"><span data-stu-id="31e32-316">Parts that require work to be performed at shut down or that need to release resources should implement `IDisposable`, as usual for .NET Framework objects.</span></span> <span data-ttu-id="31e32-317">但是，由於容器會建立和維護對組件的參考，因此只有擁有組件的容器應該對組件呼叫 `Dispose` 方法。</span><span class="sxs-lookup"><span data-stu-id="31e32-317">However, since the container creates and maintains references to parts, only the container that owns a part should call the `Dispose` method on it.</span></span> <span data-ttu-id="31e32-318">容器本身會實作 `IDisposable`，而且在 `Dispose` 清除過程中，它會對所擁有的全部組件呼叫 `Dispose` 。</span><span class="sxs-lookup"><span data-stu-id="31e32-318">The container itself implements `IDisposable`, and as portion of its cleanup in `Dispose` it will call `Dispose` on all the parts that it owns.</span></span> <span data-ttu-id="31e32-319">因此，只要不再需要組合容器和其擁有的所有組件，便應該處置該組合容器。</span><span class="sxs-lookup"><span data-stu-id="31e32-319">For this reason, you should always dispose the composition container when it and any parts it owns are no longer needed.</span></span>

<span data-ttu-id="31e32-320">對於存留期很長的組合容器而言，長期讓具有非共用建立原則的組件耗用記憶體可能會帶來問題。</span><span class="sxs-lookup"><span data-stu-id="31e32-320">For long-lived composition containers, memory consumption by parts with a creation policy of non-shared can become a problem.</span></span> <span data-ttu-id="31e32-321">這些非共用的組件可能會建立多次，並且在處置容器本身之前，都不會處置這些組件。</span><span class="sxs-lookup"><span data-stu-id="31e32-321">These non-shared parts can be created multiple times and will not be disposed until the container itself is disposed.</span></span> <span data-ttu-id="31e32-322">為了解決這個問題，容器提供了 `ReleaseExport` 方法。</span><span class="sxs-lookup"><span data-stu-id="31e32-322">To deal with this, the container provides the `ReleaseExport` method.</span></span> <span data-ttu-id="31e32-323">在非共用的匯出上呼叫這個方法，可從組合容器中移除該匯出並進行處置。</span><span class="sxs-lookup"><span data-stu-id="31e32-323">Calling this method on a non-shared export removes that export from the composition container and disposes it.</span></span> <span data-ttu-id="31e32-324">移除的匯出唯一使用的組件，以及樹狀目錄中的下層組件，也會一併遭到移除和處置。</span><span class="sxs-lookup"><span data-stu-id="31e32-324">Parts that are used only by the removed export, and so on down the tree, are also removed and disposed.</span></span> <span data-ttu-id="31e32-325">如此一來，不需處置組合容器本身，即可回收資源。</span><span class="sxs-lookup"><span data-stu-id="31e32-325">In this way, resources can be reclaimed without disposing the composition container itself.</span></span>

<span data-ttu-id="31e32-326">`IPartImportsSatisfiedNotification` 包含一個名為 `OnImportsSatisfied`的方法。</span><span class="sxs-lookup"><span data-stu-id="31e32-326">`IPartImportsSatisfiedNotification` contains one method named `OnImportsSatisfied`.</span></span> <span data-ttu-id="31e32-327">當組合完成且組件的匯入可開始使用時，組合容器會對任何實作介面的組件呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="31e32-327">This method is called by the composition container on any parts that implement the interface when composition has been completed and the part's imports are ready for use.</span></span> <span data-ttu-id="31e32-328">組合引擎會建立組件，以填入其他組件的匯入。</span><span class="sxs-lookup"><span data-stu-id="31e32-328">Parts are created by the composition engine to fill the imports of other parts.</span></span> <span data-ttu-id="31e32-329">設定組件的匯入之前，您無法在組件建構函式中執行任何依賴或操作匯入值的初始設定，除非已使用 `ImportingConstructor` 屬性指定這些值做為先決條件。</span><span class="sxs-lookup"><span data-stu-id="31e32-329">Before the imports of a part have been set, you cannot perform any initialization that relies on or manipulates imported values in the part constructor unless those values have been specified as prerequisites by using the `ImportingConstructor` attribute.</span></span> <span data-ttu-id="31e32-330">這通常是比較好的方法，但在某些情況下，可能無法插入建構函式。</span><span class="sxs-lookup"><span data-stu-id="31e32-330">This is normally the preferred method, but in some cases, constructor injection may not be available.</span></span> <span data-ttu-id="31e32-331">在這些情況下，您可以在 `OnImportsSatisfied`中執行初始設定，並且組件應該實作 `IPartImportsSatisfiedNotification`。</span><span class="sxs-lookup"><span data-stu-id="31e32-331">In those cases, initialization can be performed in `OnImportsSatisfied`, and the part should implement `IPartImportsSatisfiedNotification`.</span></span>

## <a name="see-also"></a><span data-ttu-id="31e32-332">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31e32-332">See also</span></span>

- [<span data-ttu-id="31e32-333">Channel 9 影片：Open Up Your Applications with the Managed Extensibility Framework (透過 Managed Extensibility Framework 開展應用程式)</span><span class="sxs-lookup"><span data-stu-id="31e32-333">Channel 9 Video: Open Up Your Applications with the Managed Extensibility Framework</span></span>](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)
- [<span data-ttu-id="31e32-334">Channel 9 影片：Managed Extensibility Framework (MEF) 2.0</span><span class="sxs-lookup"><span data-stu-id="31e32-334">Channel 9 Video: Managed Extensibility Framework (MEF) 2.0</span></span>](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
