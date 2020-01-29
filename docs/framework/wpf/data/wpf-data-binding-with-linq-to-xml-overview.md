---
title: 使用 LINQ to XML 進行資料繫結
ms.date: 10/22/2019
ms.topic: conceptual
ms.openlocfilehash: 3c5567c81d2097a1524f5bbbf9010836ca8c0646
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733814"
---
# <a name="overview-of-wpf-data-binding-with-linq-to-xml"></a><span data-ttu-id="15fc6-102">使用 LINQ to XML 的 WPF 資料系結總覽</span><span class="sxs-lookup"><span data-stu-id="15fc6-102">Overview of WPF data binding with LINQ to XML</span></span>

<span data-ttu-id="15fc6-103">本文介紹 <xref:System.Xml.Linq> 命名空間中的動態資料系結功能。</span><span class="sxs-lookup"><span data-stu-id="15fc6-103">This article introduces the dynamic data binding features in the <xref:System.Xml.Linq> namespace.</span></span> <span data-ttu-id="15fc6-104">這些功能在 Windows Presentation Foundation (WPF) 應用程式中可以當作使用者介面 (UI) 項目的資料來源使用。</span><span class="sxs-lookup"><span data-stu-id="15fc6-104">These features can be used as a data source for user interface (UI) elements in Windows Presentation Foundation (WPF) apps.</span></span> <span data-ttu-id="15fc6-105">這個案例是以 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> 和 <xref:System.Xml.Linq.XElement?displayProperty=fullName> 的「動態屬性」為基礎。</span><span class="sxs-lookup"><span data-stu-id="15fc6-105">This scenario relies upon special *dynamic properties* of <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> and <xref:System.Xml.Linq.XElement?displayProperty=fullName>.</span></span>

## <a name="xaml-and-linq-to-xml"></a><span data-ttu-id="15fc6-106">XAML 和 LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="15fc6-106">XAML and LINQ to XML</span></span>

<span data-ttu-id="15fc6-107">Extensible Application Markup Language (XAML) 是由 Microsoft 所建立的 XML 方言，用以支援 .NET 技術。</span><span class="sxs-lookup"><span data-stu-id="15fc6-107">The Extensible Application Markup Language (XAML) is an XML dialect created by Microsoft to support .NET technologies.</span></span> <span data-ttu-id="15fc6-108">它在 WPF 中用於表示使用者介面項目與相關功能，例如，事件和資料繫結。</span><span class="sxs-lookup"><span data-stu-id="15fc6-108">It is used in WPF to represent user interface elements and related features, such as events and data binding.</span></span> <span data-ttu-id="15fc6-109">在 Windows Workflow Foundation 中，XAML 可用來表示程式結構，例如程式控制 (「工作流程」)。</span><span class="sxs-lookup"><span data-stu-id="15fc6-109">In Windows Workflow Foundation, XAML is used to represent program structure, such as program control (*workflows*).</span></span> <span data-ttu-id="15fc6-110">XAML 可讓技術的宣告性部分與定義程式更個人化行為的相關程序性程式碼分開。</span><span class="sxs-lookup"><span data-stu-id="15fc6-110">XAML enables the declarative aspects of a technology to be separated from the related procedural code that defines the more individualized behavior of a program.</span></span>

<span data-ttu-id="15fc6-111">XAML 和 LINQ to XML 有兩種廣泛的方式可以互動：</span><span class="sxs-lookup"><span data-stu-id="15fc6-111">There are two broad ways that XAML and LINQ to XML can interact:</span></span>

- <span data-ttu-id="15fc6-112">XAML 檔案是語式正確 (Well-Formed) 的 XML，因此可以透過 XML 技術 (例如，LINQ to XML) 進行查詢與管理。</span><span class="sxs-lookup"><span data-stu-id="15fc6-112">Because XAML files are well-formed XML, they can be queried and manipulated through XML technologies such as LINQ to XML.</span></span>

- <span data-ttu-id="15fc6-113">由於 LINQ to XML 查詢代表資料的來源，這些查詢可以當做 WPF UI 項目之資料繫結的資料來源使用。</span><span class="sxs-lookup"><span data-stu-id="15fc6-113">Because LINQ to XML queries represent a source of data, these queries can be used as a data source for data binding for WPF UI elements.</span></span>

<span data-ttu-id="15fc6-114">此文件描述第二個案例。</span><span class="sxs-lookup"><span data-stu-id="15fc6-114">This documentation describes the second scenario.</span></span>

## <a name="data-binding-in-the-windows-presentation-foundation"></a><span data-ttu-id="15fc6-115">Windows Presentation Foundation 中的資料系結</span><span class="sxs-lookup"><span data-stu-id="15fc6-115">Data binding in the Windows Presentation Foundation</span></span>

<span data-ttu-id="15fc6-116">WPF 資料繫結可讓 UI 項目將其屬性中的一個屬性與資料來源產生關聯。</span><span class="sxs-lookup"><span data-stu-id="15fc6-116">WPF data binding enables a UI element to associate one of its properties with a data source.</span></span> <span data-ttu-id="15fc6-117">其中一個簡單的範例為 <xref:System.Windows.Controls.Label>，其文字表示使用者定義物件中公用屬性的值。</span><span class="sxs-lookup"><span data-stu-id="15fc6-117">A simple example of this is a <xref:System.Windows.Controls.Label> whose text presents the value of a public property in a user-defined object.</span></span> <span data-ttu-id="15fc6-118">WPF 資料繫結依賴下列元件：</span><span class="sxs-lookup"><span data-stu-id="15fc6-118">WPF data binding relies on the following components:</span></span>

|<span data-ttu-id="15fc6-119">元件</span><span class="sxs-lookup"><span data-stu-id="15fc6-119">Component</span></span>|<span data-ttu-id="15fc6-120">描述</span><span class="sxs-lookup"><span data-stu-id="15fc6-120">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="15fc6-121">繫結目標</span><span class="sxs-lookup"><span data-stu-id="15fc6-121">Binding target</span></span>|<span data-ttu-id="15fc6-122">與資料來源相關聯的 UI 項目。</span><span class="sxs-lookup"><span data-stu-id="15fc6-122">The UI element to be associated with the data source.</span></span> <span data-ttu-id="15fc6-123">WPF 中的 Visual 項目衍生自 <xref:System.Windows.UIElement> 類別。</span><span class="sxs-lookup"><span data-stu-id="15fc6-123">Visual elements in WPF are derived from the <xref:System.Windows.UIElement> class.</span></span>|
|<span data-ttu-id="15fc6-124">目標屬性</span><span class="sxs-lookup"><span data-stu-id="15fc6-124">Target property</span></span>|<span data-ttu-id="15fc6-125">反映資料繫結來源值的繫結目標「相依性屬性」。</span><span class="sxs-lookup"><span data-stu-id="15fc6-125">The *dependency property* of the binding target that reflects the value of the data-binding source.</span></span> <span data-ttu-id="15fc6-126">相依性屬性是由 <xref:System.Windows.DependencyObject> 類別 (可衍生 <xref:System.Windows.UIElement>) 直接支援。</span><span class="sxs-lookup"><span data-stu-id="15fc6-126">Dependency properties are directly supported by the <xref:System.Windows.DependencyObject> class, which <xref:System.Windows.UIElement> derives from.</span></span>|
|<span data-ttu-id="15fc6-127">繫結來源</span><span class="sxs-lookup"><span data-stu-id="15fc6-127">Binding source</span></span>|<span data-ttu-id="15fc6-128">一或多個值的來源物件，這些值會提供給 UI 項目進行顯示。</span><span class="sxs-lookup"><span data-stu-id="15fc6-128">The source object for one or more values that are supplied to the UI element for presentation.</span></span> <span data-ttu-id="15fc6-129">WPF 會自動支援下列類型做為繫結來源：CLR 物件、ADO.NET 資料物件、XML 資料 (來自 XPath 或 LINQ to XML 查詢)，或其他 <xref:System.Windows.DependencyObject>。</span><span class="sxs-lookup"><span data-stu-id="15fc6-129">WPF automatically supports the following types as binding sources: CLR objects, ADO.NET data objects, XML data (from XPath or LINQ to XML queries), or another <xref:System.Windows.DependencyObject>.</span></span>|
|<span data-ttu-id="15fc6-130">來源路徑</span><span class="sxs-lookup"><span data-stu-id="15fc6-130">Source path</span></span>|<span data-ttu-id="15fc6-131">繫結來源的屬性，可解析要繫結的值或值集合。</span><span class="sxs-lookup"><span data-stu-id="15fc6-131">The property of the binding source that resolves to the value or set of values that is to be bound.</span></span>|

<span data-ttu-id="15fc6-132">相依性屬性為 WPF 專屬的概念，代表 UI 項目動態計算的屬性。</span><span class="sxs-lookup"><span data-stu-id="15fc6-132">A dependency property is a concept specific to WPF that represent a dynamically computed property of a UI element.</span></span> <span data-ttu-id="15fc6-133">例如，相依性屬性通常具有父項目提供的預設值或值。</span><span class="sxs-lookup"><span data-stu-id="15fc6-133">For example, dependency properties often have default values or values that are provided by a parent element.</span></span> <span data-ttu-id="15fc6-134">這些特殊的屬性是由 <xref:System.Windows.DependencyProperty> 類別 (而非具有標準屬性的欄位) 的執行個體所支援。</span><span class="sxs-lookup"><span data-stu-id="15fc6-134">These special properties are backed by instances of the <xref:System.Windows.DependencyProperty> class (and not fields as with standard properties).</span></span> <span data-ttu-id="15fc6-135">如需詳細資訊，請參閱[相依性屬性概觀](../advanced/dependency-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="15fc6-135">For more information, see [Dependency Properties Overview](../advanced/dependency-properties-overview.md).</span></span>

### <a name="dynamic-data-binding-in-wpf"></a><span data-ttu-id="15fc6-136">WPF 中的動態資料系結</span><span class="sxs-lookup"><span data-stu-id="15fc6-136">Dynamic data binding in WPF</span></span>

<span data-ttu-id="15fc6-137">根據預設，只有在初始化目標 UI 項目後，才會發生資料繫結。</span><span class="sxs-lookup"><span data-stu-id="15fc6-137">By default, data binding occurs only when the target UI element is initialized.</span></span> <span data-ttu-id="15fc6-138">這稱為「單次」繫結。</span><span class="sxs-lookup"><span data-stu-id="15fc6-138">This is called *one-time* binding.</span></span> <span data-ttu-id="15fc6-139">就大部分的用途而言，這還不足夠；資料繫結解決方案通常需要在執行階段，使用下列其中一項，動態傳播這些變更：</span><span class="sxs-lookup"><span data-stu-id="15fc6-139">For most purposes, this is insufficient; typically, a data-binding solution requires that the changes be dynamically propagated at run time using one of the following:</span></span>

- <span data-ttu-id="15fc6-140">「單向」繫結會促使自動傳播對一端所做的變更。</span><span class="sxs-lookup"><span data-stu-id="15fc6-140">*One-way* binding causes the changes to one side to be propagated automatically.</span></span> <span data-ttu-id="15fc6-141">最常見的情況下，對來源的變更會反映到目標中，但是反向有時候很有用。</span><span class="sxs-lookup"><span data-stu-id="15fc6-141">Most commonly, changes to the source are reflected in the target, but the reverse can sometimes be useful.</span></span>

- <span data-ttu-id="15fc6-142">在「雙向」繫結中，對來源所做的變更會自動傳播到目標，而對目標所做的變更也會自動傳播到來源。</span><span class="sxs-lookup"><span data-stu-id="15fc6-142">In *two-way* binding, changes to the source are automatically propagated to the target, and changes to the target are automatically propagated to the source.</span></span>

<span data-ttu-id="15fc6-143">若要讓單向或雙向繫結發生，來源必須實作變更通知機制，例如，藉由針對支援的每個屬性實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面或使用 *PropertyNameChanged* 模式。</span><span class="sxs-lookup"><span data-stu-id="15fc6-143">For one-way or two-way binding to occur, the source must implement a change notification mechanism, for example by implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface or by using a *PropertyNameChanged* pattern for each property supported.</span></span>

<span data-ttu-id="15fc6-144">如需有關 WPF 中資料繫結的詳細資訊，請參閱[資料繫結 (WPF)](/dotnet/framework/wpf/data/data-binding-wpf)。</span><span class="sxs-lookup"><span data-stu-id="15fc6-144">For more information about data binding in WPF, see [Data Binding (WPF)](/dotnet/framework/wpf/data/data-binding-wpf).</span></span>

## <a name="dynamic-properties-in-linq-to-xml-classes"></a><span data-ttu-id="15fc6-145">LINQ to XML 類別中的動態屬性</span><span class="sxs-lookup"><span data-stu-id="15fc6-145">Dynamic properties in LINQ to XML classes</span></span>

<span data-ttu-id="15fc6-146">多數的 LINQ to XML 類別不會限定為適當的 WPF 動態資料來源。</span><span class="sxs-lookup"><span data-stu-id="15fc6-146">Most LINQ to XML classes do not qualify as proper WPF dynamic data sources.</span></span> <span data-ttu-id="15fc6-147">某些最實用的資訊僅能透過方法而非屬性取得，而且這些類別中的屬性不會實作變更通知。</span><span class="sxs-lookup"><span data-stu-id="15fc6-147">Some of the most useful information is available only through methods, not properties, and properties in these classes do not implement change notifications.</span></span> <span data-ttu-id="15fc6-148">為了支援 WPF 資料繫結，LINQ to XML 會公開一組「動態屬性」。</span><span class="sxs-lookup"><span data-stu-id="15fc6-148">To support WPF data binding, LINQ to XML exposes a set of *dynamic properties*.</span></span>

<span data-ttu-id="15fc6-149">這些動態屬性是特殊的執行階段屬性，會在 <xref:System.Xml.Linq.XAttribute> 和 <xref:System.Xml.Linq.XElement> 類別中，複製現有方法和屬性的功能。</span><span class="sxs-lookup"><span data-stu-id="15fc6-149">These dynamic properties are special run-time properties that duplicate the functionality of existing methods and properties in the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> classes.</span></span> <span data-ttu-id="15fc6-150">這些屬性會單獨加入到這些類別中，讓它們當做 WPF 的動態資料來源使用。</span><span class="sxs-lookup"><span data-stu-id="15fc6-150">They were added to these classes solely to enable them to act as dynamic data sources for WPF.</span></span> <span data-ttu-id="15fc6-151">為符合這個需求，全部這些動態屬性都要實作變更通知。</span><span class="sxs-lookup"><span data-stu-id="15fc6-151">To meet this need, all these dynamic properties implement change notifications.</span></span> <span data-ttu-id="15fc6-152">下一節 [LINQ to XML 動態屬性](linq-to-xml-dynamic-properties.md)中會提供這些動態屬性的詳細參考。</span><span class="sxs-lookup"><span data-stu-id="15fc6-152">A detailed reference for these dynamic properties is provided in the next section, [LINQ to XML Dynamic Properties](linq-to-xml-dynamic-properties.md).</span></span>

> [!NOTE]
> <span data-ttu-id="15fc6-153">在 <xref:System.Xml.Linq> 命名空間各種類別中找到的多數標準公用屬性都可以用於一次資料繫結。</span><span class="sxs-lookup"><span data-stu-id="15fc6-153">Many of the standard public properties, found in the various classes in the <xref:System.Xml.Linq> namespace, can be used for one-time data binding.</span></span> <span data-ttu-id="15fc6-154">不過請記住，在此配置下，不會自動更新來源或目標。</span><span class="sxs-lookup"><span data-stu-id="15fc6-154">However, remember that neither the source nor the target will be dynamically updated under this scheme.</span></span>

### <a name="access-dynamic-properties"></a><span data-ttu-id="15fc6-155">存取動態屬性</span><span class="sxs-lookup"><span data-stu-id="15fc6-155">Access dynamic properties</span></span>

<span data-ttu-id="15fc6-156"><xref:System.Xml.Linq.XAttribute> 和 <xref:System.Xml.Linq.XElement> 類別中的動態屬性無法像標準屬性般存取。</span><span class="sxs-lookup"><span data-stu-id="15fc6-156">The dynamic properties in the <xref:System.Xml.Linq.XAttribute> and <xref:System.Xml.Linq.XElement> classes cannot be accessed like standard properties.</span></span> <span data-ttu-id="15fc6-157">例如，在 CLR 相容的語言 (例如 C#) 中，這些屬性無法：</span><span class="sxs-lookup"><span data-stu-id="15fc6-157">For example, in CLR-compliant languages such as C#, they cannot be:</span></span>

- <span data-ttu-id="15fc6-158">直接在編譯階段存取。</span><span class="sxs-lookup"><span data-stu-id="15fc6-158">Accessed directly at compile time.</span></span> <span data-ttu-id="15fc6-159">編譯器和 Visual Studio IntelliSense 看不到動態屬性。</span><span class="sxs-lookup"><span data-stu-id="15fc6-159">Dynamic properties are invisible to the compiler and to Visual Studio IntelliSense.</span></span>

- <span data-ttu-id="15fc6-160">在執行階段，使用 .NET 反映尋找或存取。</span><span class="sxs-lookup"><span data-stu-id="15fc6-160">Discovered or accessed at run time using .NET reflection.</span></span> <span data-ttu-id="15fc6-161">即使是在執行階段，它們都不是基本 CLR 偵測的屬性。</span><span class="sxs-lookup"><span data-stu-id="15fc6-161">Even at run time, they are not properties in the basic CLR sense.</span></span>

<span data-ttu-id="15fc6-162">在 C# 中，動態屬性僅能在執行階段，透過 <xref:System.ComponentModel> 命名空間提供的功能存取。</span><span class="sxs-lookup"><span data-stu-id="15fc6-162">In C#, dynamic properties can only be accessed at run time through facilities provided by the <xref:System.ComponentModel> namespace.</span></span>

<span data-ttu-id="15fc6-163">但是，相較之下，在 XML 原始檔中，動態屬性可以透過下列格式的直接附註存取：</span><span class="sxs-lookup"><span data-stu-id="15fc6-163">In contrast, however, in an XML source dynamic properties can be accessed through a straightforward notation in the following form:</span></span>

```xml
<object>.<dynamic-property>
```

<span data-ttu-id="15fc6-164">這兩種類別的動態屬性會解析可直接使用的值，或解析必須隨索引提供的索引子 (Indexer)，才能取得所產生的值或值集合。</span><span class="sxs-lookup"><span data-stu-id="15fc6-164">The dynamic properties for these two classes either resolve to a value that can be used directly, or to an indexer that must be supplied with an index to obtain the resulting value or collection of values.</span></span> <span data-ttu-id="15fc6-165">後者的語法採用的格式為：</span><span class="sxs-lookup"><span data-stu-id="15fc6-165">The latter syntax takes the form:</span></span>

```xml
<object>.<dynamic-property>[<index-value>]
```

<span data-ttu-id="15fc6-166">如需詳細資訊，請參閱 [LINQ to XML 動態屬性](linq-to-xml-dynamic-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="15fc6-166">For more information, see [LINQ to XML Dynamic Properties](linq-to-xml-dynamic-properties.md).</span></span>

<span data-ttu-id="15fc6-167">若要實作 WPF 動態繫結，動態屬性將搭配 <xref:System.Windows.Data> 命名空間 (特別是 <xref:System.Windows.Data.Binding> 類別) 所提供的功能使用。</span><span class="sxs-lookup"><span data-stu-id="15fc6-167">To implement WPF dynamic binding, dynamic properties will be used with facilities provided by the <xref:System.Windows.Data> namespace, most notably the <xref:System.Windows.Data.Binding> class.</span></span>

## <a name="see-also"></a><span data-ttu-id="15fc6-168">請參閱</span><span class="sxs-lookup"><span data-stu-id="15fc6-168">See also</span></span>

- [<span data-ttu-id="15fc6-169">WPF 資料繫結與 LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="15fc6-169">WPF Data Binding with LINQ to XML</span></span>](wpf-data-binding-with-linq-to-xml-overview.md)
- [<span data-ttu-id="15fc6-170">LINQ to XML 動態屬性</span><span class="sxs-lookup"><span data-stu-id="15fc6-170">LINQ to XML Dynamic Properties</span></span>](linq-to-xml-dynamic-properties.md)
- [<span data-ttu-id="15fc6-171">WPF 中的 XAML</span><span class="sxs-lookup"><span data-stu-id="15fc6-171">XAML in WPF</span></span>](../advanced/xaml-in-wpf.md)
- [<span data-ttu-id="15fc6-172">資料繫結 (WPF)</span><span class="sxs-lookup"><span data-stu-id="15fc6-172">Data Binding (WPF)</span></span>](/dotnet/framework/wpf/data/data-binding-wpf)
- [<span data-ttu-id="15fc6-173">使用工作流程標記</span><span class="sxs-lookup"><span data-stu-id="15fc6-173">Using Workflow Markup</span></span>](https://go.microsoft.com/fwlink/?LinkId=98685)
