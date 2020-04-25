---
title: PropertyPath XAML 語法
ms.date: 03/30/2017
helpviewer_keywords:
- PropertyPath object [WPF]
- XAML [WPF], PropertyPath object
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
ms.openlocfilehash: 817ce750cdad58e504eef5144cfb8a2813bca596
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141283"
---
# <a name="propertypath-xaml-syntax"></a><span data-ttu-id="4a87f-102">PropertyPath XAML 語法</span><span class="sxs-lookup"><span data-stu-id="4a87f-102">PropertyPath XAML Syntax</span></span>

<span data-ttu-id="4a87f-103"><xref:System.Windows.PropertyPath>物件支援複雜的內嵌[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]語法，用於設定以<xref:System.Windows.PropertyPath>類型做為其值的各種屬性。</span><span class="sxs-lookup"><span data-stu-id="4a87f-103">The <xref:System.Windows.PropertyPath> object supports a complex inline [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntax for setting various properties that take the <xref:System.Windows.PropertyPath> type as their value.</span></span> <span data-ttu-id="4a87f-104">本主題記載適用<xref:System.Windows.PropertyPath>于系結和動畫語法的語法。</span><span class="sxs-lookup"><span data-stu-id="4a87f-104">This topic documents the <xref:System.Windows.PropertyPath> syntax as applied to binding and animation syntaxes.</span></span>

<a name="where"></a>

## <a name="where-propertypath-is-used"></a><span data-ttu-id="4a87f-105">PropertyPath 的用途</span><span class="sxs-lookup"><span data-stu-id="4a87f-105">Where PropertyPath Is Used</span></span>

<span data-ttu-id="4a87f-106"><xref:System.Windows.PropertyPath>是常用於數個[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]功能的物件。</span><span class="sxs-lookup"><span data-stu-id="4a87f-106"><xref:System.Windows.PropertyPath> is a common object that is used in several [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] features.</span></span> <span data-ttu-id="4a87f-107">雖然使用一般<xref:System.Windows.PropertyPath>來傳達屬性路徑資訊， <xref:System.Windows.PropertyPath>但作為類型的每個功能區域的使用方式會有所不同。</span><span class="sxs-lookup"><span data-stu-id="4a87f-107">Despite using the common <xref:System.Windows.PropertyPath> to convey property path information, the usages for each feature area where <xref:System.Windows.PropertyPath> is used as a type vary.</span></span> <span data-ttu-id="4a87f-108">因此，依功能來說明語法會比較實際。</span><span class="sxs-lookup"><span data-stu-id="4a87f-108">Therefore, it is more practical to document the syntaxes on a per-feature basis.</span></span>

<span data-ttu-id="4a87f-109">主要是[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]用<xref:System.Windows.PropertyPath>來描述物件模型路徑，以便遍歷物件資料來源的屬性，以及描述目標動畫的目標路徑。</span><span class="sxs-lookup"><span data-stu-id="4a87f-109">Primarily, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uses <xref:System.Windows.PropertyPath> to describe object-model paths for traversing the properties of an object data source, and to describe the target path for targeted animations.</span></span>

<span data-ttu-id="4a87f-110">某些樣式和範本屬性（例如<xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType> ）會採用表面上類似的<xref:System.Windows.PropertyPath>限定屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="4a87f-110">Some style and template properties such as <xref:System.Windows.Setter.Property%2A?displayProperty=nameWithType> take a qualified property name that superficially resembles a <xref:System.Windows.PropertyPath>.</span></span> <span data-ttu-id="4a87f-111">但這不是真正的<xref:System.Windows.PropertyPath>事實;相反地，它是一種合格的*擁有者。* WPF [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器會與的型別轉換<xref:System.Windows.DependencyProperty>子一起啟用的屬性字串格式用法。</span><span class="sxs-lookup"><span data-stu-id="4a87f-111">But this is not a true <xref:System.Windows.PropertyPath>; instead it is a qualified *owner.property* string format usage that is enabled by the WPF [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor in combination with the type converter for <xref:System.Windows.DependencyProperty>.</span></span>

<a name="databinding_s"></a>

## <a name="propertypath-for-objects-in-data-binding"></a><span data-ttu-id="4a87f-112">資料繫結中物件的 PropertyPath</span><span class="sxs-lookup"><span data-stu-id="4a87f-112">PropertyPath for Objects in Data Binding</span></span>

<span data-ttu-id="4a87f-113">資料繫結是一個 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 功能，您可藉以繫結至任何相依性屬性的目標值。</span><span class="sxs-lookup"><span data-stu-id="4a87f-113">Data binding is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] feature whereby you can bind to the target value of any dependency property.</span></span> <span data-ttu-id="4a87f-114">不過，這類資料繫結的來源不需要是相依性屬性；它可以是適用的資料提供者所能辨識的任何屬性類型。</span><span class="sxs-lookup"><span data-stu-id="4a87f-114">However, the source of such a data binding need not be a dependency property; it can be any property type that is recognized by the applicable data provider.</span></span> <span data-ttu-id="4a87f-115">屬性路徑特別用於<xref:System.Windows.Data.ObjectDataProvider>，後者是用來從通用語言執行時間（CLR）物件及其屬性取得系結來源。</span><span class="sxs-lookup"><span data-stu-id="4a87f-115">Property paths are particularly used for the <xref:System.Windows.Data.ObjectDataProvider>, which is used for obtaining binding sources from common language runtime (CLR) objects and their properties.</span></span>

<span data-ttu-id="4a87f-116">請注意，資料系結至 XML 並<xref:System.Windows.PropertyPath>不會使用，因為它<xref:System.Windows.Data.Binding.Path%2A>不會<xref:System.Windows.Data.Binding>使用中的。</span><span class="sxs-lookup"><span data-stu-id="4a87f-116">Note that data binding to XML does not use <xref:System.Windows.PropertyPath>, because it does not use <xref:System.Windows.Data.Binding.Path%2A> in the <xref:System.Windows.Data.Binding>.</span></span> <span data-ttu-id="4a87f-117">相反地，您<xref:System.Windows.Data.Binding.XPath%2A>可以使用，並在資料的 XML 檔物件模型（DOM）中指定有效的 XPath 語法。</span><span class="sxs-lookup"><span data-stu-id="4a87f-117">Instead, you use <xref:System.Windows.Data.Binding.XPath%2A> and specify valid XPath syntax into the XML Document Object Model (DOM) of the data.</span></span> <span data-ttu-id="4a87f-118"><xref:System.Windows.Data.Binding.XPath%2A>也指定為字串，但此處未記載。請參閱[使用 XMLDataProvider 和 XPath 查詢系結至 XML 資料](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="4a87f-118"><xref:System.Windows.Data.Binding.XPath%2A> is also specified as a string, but is not documented here; see [Bind to XML Data Using an XMLDataProvider and XPath Queries](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span>

<span data-ttu-id="4a87f-119">若要了解資料繫結中的屬性路徑，關鍵在於您可以將繫結的目標設為個別的屬性值，也可以改為繫結至要取得清單或集合的目標屬性。</span><span class="sxs-lookup"><span data-stu-id="4a87f-119">A key to understanding property paths in data binding is that you can target the binding to an individual property value, or you can instead bind to target properties that take lists or collections.</span></span> <span data-ttu-id="4a87f-120">如果您要系結集合，例如<xref:System.Windows.Controls.ListBox>系結會根據集合中有多少資料項目而展開，則您的屬性路徑應該參考集合物件，而不是個別的集合專案。</span><span class="sxs-lookup"><span data-stu-id="4a87f-120">If you are binding collections, for instance binding a <xref:System.Windows.Controls.ListBox> that will expand depending on how many data items are in the collection, then your property path should reference the collection object, not individual collection items.</span></span> <span data-ttu-id="4a87f-121">資料系結引擎會自動將當做資料來源使用的集合與系結目標的型別進行比對，因而產生像是以<xref:System.Windows.Controls.ListBox>專案陣列填入的行為。</span><span class="sxs-lookup"><span data-stu-id="4a87f-121">The data binding engine will match the collection used as the data source to the type of the binding target automatically, resulting in behavior such as populating a <xref:System.Windows.Controls.ListBox> with an items array.</span></span>

<a name="singlecurrent"></a>

### <a name="single-property-on-the-immediate-object-as-data-context"></a><span data-ttu-id="4a87f-122">直接物件上做為資料內容的單一屬性</span><span class="sxs-lookup"><span data-stu-id="4a87f-122">Single Property on the Immediate Object as Data Context</span></span>

```xml
<Binding Path="propertyName" ... />
```

<span data-ttu-id="4a87f-123">*propertyName*必須解析為目前<xref:System.Windows.FrameworkElement.DataContext%2A>中的屬性名稱，以供<xref:System.Windows.Data.Binding.Path%2A>使用。</span><span class="sxs-lookup"><span data-stu-id="4a87f-123">*propertyName* must resolve to be the name of a property that is in the current <xref:System.Windows.FrameworkElement.DataContext%2A> for a <xref:System.Windows.Data.Binding.Path%2A> usage.</span></span> <span data-ttu-id="4a87f-124">如果您的繫結會更新來源，則該屬性必須是讀取/寫入屬性，且來源物件必須是可變動的。</span><span class="sxs-lookup"><span data-stu-id="4a87f-124">If your binding updates the source, that property must be read/write and the source object must be mutable.</span></span>

<a name="singleindex"></a>

### <a name="single-indexer-on-the-immediate-object-as-data-context"></a><span data-ttu-id="4a87f-125">直接物件上做為資料內容的單一索引子</span><span class="sxs-lookup"><span data-stu-id="4a87f-125">Single Indexer on the Immediate Object as Data Context</span></span>

```xml
<Binding Path="[key]" ... />
```

<span data-ttu-id="4a87f-126">`key` 必須是對字典或雜湊表之具類型的索引，或是陣列的整數索引。</span><span class="sxs-lookup"><span data-stu-id="4a87f-126">`key` must be either the typed index to a dictionary or hash table, or the integer index of an array.</span></span> <span data-ttu-id="4a87f-127">此外，索引鍵值的類型必須是可直接繫結至要套用它的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a87f-127">Also, the value of the key must be a type that is directly bindable to the property where it is applied.</span></span> <span data-ttu-id="4a87f-128">例如，包含字串索引鍵和字串值的雜湊表，可以用這種方式系結至的<xref:System.Windows.Controls.TextBox>文字。</span><span class="sxs-lookup"><span data-stu-id="4a87f-128">For instance, a hash table that contains string keys and string values can be used this way to bind to Text for a <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="4a87f-129">或者，如果索引鍵指向集合或子索引，您可以使用此語法來繫結至目標集合屬性。</span><span class="sxs-lookup"><span data-stu-id="4a87f-129">Or, if the key points to a collection or subindex, you could use this syntax to bind to a target collection property.</span></span> <span data-ttu-id="4a87f-130">否則，您需要透過語法 (例如 `<Binding Path="[key].propertyName" .../>`) 來參考特定的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a87f-130">Otherwise, you need to reference a specific property, through a syntax such as `<Binding Path="[key].propertyName" .../>`.</span></span>

<span data-ttu-id="4a87f-131">您可以視需要指定索引的類型。</span><span class="sxs-lookup"><span data-stu-id="4a87f-131">You can specify the type of the index if necessary.</span></span> <span data-ttu-id="4a87f-132">如需索引屬性路徑這方面的詳細資訊，請<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>參閱。</span><span class="sxs-lookup"><span data-stu-id="4a87f-132">For details on this aspect of an indexed property path, see <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.</span></span>

<a name="multipleindirect"></a>

### <a name="multiple-property-indirect-property-targeting"></a><span data-ttu-id="4a87f-133">多個屬性 (間接屬性目標設定)</span><span class="sxs-lookup"><span data-stu-id="4a87f-133">Multiple Property (Indirect Property Targeting)</span></span>

```xml
<Binding Path="propertyName.propertyName2" ... />
```

<span data-ttu-id="4a87f-134">`propertyName`必須解析為目前的屬性名稱<xref:System.Windows.FrameworkElement.DataContext%2A>。</span><span class="sxs-lookup"><span data-stu-id="4a87f-134">`propertyName` must resolve to be the name of a property that is the current <xref:System.Windows.FrameworkElement.DataContext%2A>.</span></span> <span data-ttu-id="4a87f-135">路徑屬性 `propertyName` 和 `propertyName2` 可以是存在於關聯性中的任何屬性，其中 `propertyName2` 是存在於值為 `propertyName` 之類型中的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a87f-135">The path properties `propertyName` and `propertyName2` can be any properties that exist in a relationship, where `propertyName2` is a property that exists on the type that is the value of `propertyName`.</span></span>

<a name="singleattached"></a>

### <a name="single-property-attached-or-otherwise-type-qualified"></a><span data-ttu-id="4a87f-136">單一屬性 (附加或類型限定)</span><span class="sxs-lookup"><span data-stu-id="4a87f-136">Single Property, Attached or Otherwise Type-Qualified</span></span>

```xml
<object property="(ownerType.propertyName)" ... />
```

<span data-ttu-id="4a87f-137">括弧表示中的這個屬性<xref:System.Windows.PropertyPath>應使用部分限定性來建立。</span><span class="sxs-lookup"><span data-stu-id="4a87f-137">The parentheses indicate that this property in a <xref:System.Windows.PropertyPath> should be constructed using a partial qualification.</span></span> <span data-ttu-id="4a87f-138">它可以使用 XML 命名空間來尋找具有適當對應的類型。</span><span class="sxs-lookup"><span data-stu-id="4a87f-138">It can use an XML namespace to find the type with an appropriate mapping.</span></span> <span data-ttu-id="4a87f-139">透過`ownerType`每個元件中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的<xref:System.Windows.Markup.XmlnsDefinitionAttribute>宣告，搜尋處理器可以存取的類型。</span><span class="sxs-lookup"><span data-stu-id="4a87f-139">The `ownerType` searches types that a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor has access to, through the <xref:System.Windows.Markup.XmlnsDefinitionAttribute> declarations in each assembly.</span></span> <span data-ttu-id="4a87f-140">大部分的應用程式都有對應至 `http://schemas.microsoft.com/winfx/2006/xaml/presentation` 命名空間的預設 XML 命名空間，因此，前置詞通常只需用於自訂類型或該命名空間以外的類型。</span><span class="sxs-lookup"><span data-stu-id="4a87f-140">Most applications have the default XML namespace mapped to the `http://schemas.microsoft.com/winfx/2006/xaml/presentation` namespace, so a prefix is usually only necessary for custom types or types otherwise outside that namespace.</span></span>  <span data-ttu-id="4a87f-141">`propertyName` 必須解析為存在於 `ownerType` 上的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="4a87f-141">`propertyName` must resolve to be the name of a property existing on the `ownerType`.</span></span> <span data-ttu-id="4a87f-142">此語法通常用於下列其中一種情況：</span><span class="sxs-lookup"><span data-stu-id="4a87f-142">This syntax is generally used for one of the following cases:</span></span>

- <span data-ttu-id="4a87f-143">指定於 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的路徑，其位於不具指定目標類型的樣式或範本中。</span><span class="sxs-lookup"><span data-stu-id="4a87f-143">The path is specified in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that is in a style or template that does not have a specified Target Type.</span></span> <span data-ttu-id="4a87f-144">除此之外，限定用法通常是無效的，因為在非樣式和非範本的情況中，屬性會存在於執行個體上，而非類型上。</span><span class="sxs-lookup"><span data-stu-id="4a87f-144">A qualified usage is generally not valid for cases other than this, because in non-style, non-template cases, the property exists on an instance, not a type.</span></span>

- <span data-ttu-id="4a87f-145">屬性是附加屬性。</span><span class="sxs-lookup"><span data-stu-id="4a87f-145">The property is an attached property.</span></span>

- <span data-ttu-id="4a87f-146">您要繫結至靜態屬性。</span><span class="sxs-lookup"><span data-stu-id="4a87f-146">You are binding to a static property.</span></span>

<span data-ttu-id="4a87f-147">若要當做分`propertyName` <xref:System.Windows.DependencyProperty>鏡腳本目標使用，指定為的屬性必須是。</span><span class="sxs-lookup"><span data-stu-id="4a87f-147">For use as storyboard target, the property specified as `propertyName` must be a <xref:System.Windows.DependencyProperty>.</span></span>

<a name="sourcetraversal"></a>

### <a name="source-traversal-binding-to-hierarchies-of-collections"></a><span data-ttu-id="4a87f-148">來源周遊 (繫結至集合的階層)</span><span class="sxs-lookup"><span data-stu-id="4a87f-148">Source Traversal (Binding to Hierarchies of Collections)</span></span>

```xml
<object Path="propertyName/propertyNameX" ... />
```

<span data-ttu-id="4a87f-149">此語法中的 / 是用來在階層式資料來源物件內進行巡覽，並支援含有連續 / 字元之階層的多個步驟。</span><span class="sxs-lookup"><span data-stu-id="4a87f-149">The / in this syntax is used to navigate within a hierarchical data source object, and multiple steps into the hierarchy with successive / characters are supported.</span></span> <span data-ttu-id="4a87f-150">來源周遊負責目前的記錄指標位置，這是藉由將資料與其檢視的 UI 同步處理來判斷。</span><span class="sxs-lookup"><span data-stu-id="4a87f-150">The source traversal accounts for the current record pointer position, which is determined by synchronizing the data with the UI of its view.</span></span> <span data-ttu-id="4a87f-151">如需與階層式資料來源物件繫結的詳細資訊，以及資料繫結中目前記錄指標的概念，請參閱[使用含階層式資料的主從式模式](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md)或[資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4a87f-151">For details on binding with hierarchical data source objects, and the concept of current record pointer in data binding, see [Use the Master-Detail Pattern with Hierarchical Data](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) or [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4a87f-152">表面上，此語法類似 XPath。</span><span class="sxs-lookup"><span data-stu-id="4a87f-152">Superficially, this syntax resembles XPath.</span></span> <span data-ttu-id="4a87f-153">用來系結至 XML 資料來源的 true XPath 運算式不會當做<xref:System.Windows.Data.Binding.Path%2A>值使用，應該改為用於互斥<xref:System.Windows.Data.Binding.XPath%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="4a87f-153">A true XPath expression for binding to an XML data source is not used as a <xref:System.Windows.Data.Binding.Path%2A> value and should instead be used for the mutually exclusive <xref:System.Windows.Data.Binding.XPath%2A> property.</span></span>

### <a name="collection-views"></a><span data-ttu-id="4a87f-154">集合檢視</span><span class="sxs-lookup"><span data-stu-id="4a87f-154">Collection Views</span></span>

<span data-ttu-id="4a87f-155">若要參考具名的集合檢視，請在集合檢視名稱前面加上雜湊字元 (`#`)。</span><span class="sxs-lookup"><span data-stu-id="4a87f-155">To reference a named collection view, prefix the collection view name with the hash character (`#`).</span></span>

### <a name="current-record-pointer"></a><span data-ttu-id="4a87f-156">目前的記錄指標</span><span class="sxs-lookup"><span data-stu-id="4a87f-156">Current Record Pointer</span></span>

<span data-ttu-id="4a87f-157">若要參考集合檢視的目前記錄指標或是一對多資料繫結案例，請以正斜線 (`/`) 做為路徑字串的開頭。</span><span class="sxs-lookup"><span data-stu-id="4a87f-157">To reference the current record pointer for a collection view or master detail data binding scenario, start the path string with a forward slash (`/`).</span></span> <span data-ttu-id="4a87f-158">任何超過正斜線的路徑，都會從目前的記錄指標開始周遊。</span><span class="sxs-lookup"><span data-stu-id="4a87f-158">Any path past the forward slash is traversed starting from the current record pointer.</span></span>

### <a name="multiple-indexers"></a><span data-ttu-id="4a87f-159">多個索引子</span><span class="sxs-lookup"><span data-stu-id="4a87f-159">Multiple Indexers</span></span>

```xaml
<object Path="[index1,index2...]" ... />
```

<span data-ttu-id="4a87f-160">或</span><span class="sxs-lookup"><span data-stu-id="4a87f-160">or</span></span>

```xaml
<object Path="propertyName[index,index2...]" ... />
```

<span data-ttu-id="4a87f-161">如果特定物件支援多個索引子，就可依順序指定那些索引子，類似陣列參考語法。</span><span class="sxs-lookup"><span data-stu-id="4a87f-161">If a given object supports multiple indexers, those indexers can be specified in order, similar to an array referencing syntax.</span></span> <span data-ttu-id="4a87f-162">上述物件可以是目前的內容，或是包含多重索引物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="4a87f-162">The object in question can be either the current context or the value of a property that contains a multiple index object.</span></span>

<span data-ttu-id="4a87f-163">根據預設，索引子值是使用基礎物件的特性來輸入。</span><span class="sxs-lookup"><span data-stu-id="4a87f-163">By default, the indexer values are typed by using the characteristics of the underlying object.</span></span> <span data-ttu-id="4a87f-164">您可以視需要指定索引的類型。</span><span class="sxs-lookup"><span data-stu-id="4a87f-164">You can specify the type of the index if necessary.</span></span> <span data-ttu-id="4a87f-165">如需輸入索引子的詳細資訊<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>，請參閱。</span><span class="sxs-lookup"><span data-stu-id="4a87f-165">For details on typing the indexers, see <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>.</span></span>

<a name="mixing"></a>

### <a name="mixing-syntaxes"></a><span data-ttu-id="4a87f-166">混合語法</span><span class="sxs-lookup"><span data-stu-id="4a87f-166">Mixing Syntaxes</span></span>

<span data-ttu-id="4a87f-167">上述語法可穿插使用。</span><span class="sxs-lookup"><span data-stu-id="4a87f-167">Each of the syntaxes shown above can be interspersed.</span></span> <span data-ttu-id="4a87f-168">例如，下列範例會在`ColorGrid`屬性的特定 x、y 上建立色彩的屬性路徑，其中包含<xref:System.Windows.Media.SolidColorBrush>物件的圖元格線陣列：</span><span class="sxs-lookup"><span data-stu-id="4a87f-168">For instance, the following is an example that creates a property path to the color at a particular x,y of a `ColorGrid` property that contains a pixel grid array of <xref:System.Windows.Media.SolidColorBrush> objects:</span></span>

```xml
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" ... />
```

### <a name="escapes-for-property-path-strings"></a><span data-ttu-id="4a87f-169">屬性路徑字串的逸出</span><span class="sxs-lookup"><span data-stu-id="4a87f-169">Escapes for Property Path Strings</span></span>

<span data-ttu-id="4a87f-170">對於某些商務物件，您可能會遇到屬性路徑字串需要逸出序列，才能正確剖析的情況。</span><span class="sxs-lookup"><span data-stu-id="4a87f-170">For certain business objects, you might encounter a case where the property path string requires an escape sequence in order to parse correctly.</span></span> <span data-ttu-id="4a87f-171">需要逸出的情況應該相當罕見，因為在通常用來定義商務物件的語言中，這其中許多字元都有類似的命名互動問題。</span><span class="sxs-lookup"><span data-stu-id="4a87f-171">The need to escape should be rare, because many of these characters have similar naming-interaction issues in languages that would typically be used to define the business object.</span></span>

- <span data-ttu-id="4a87f-172">在索引子 ([ ]) 內，插入號字元 (^) 會逸出下一個字元。</span><span class="sxs-lookup"><span data-stu-id="4a87f-172">Inside indexers ([ ]), the caret character (^) escapes the next character.</span></span>

- <span data-ttu-id="4a87f-173">您必須將專屬於 XML 語言定義的某些字元逸出 (使用 XML 實體)。</span><span class="sxs-lookup"><span data-stu-id="4a87f-173">You must escape (using XML entities) certain characters that are special to the XML language definition.</span></span> <span data-ttu-id="4a87f-174">使用 `&` 逸出 "&" 字元。</span><span class="sxs-lookup"><span data-stu-id="4a87f-174">Use `&` to escape the character "&".</span></span> <span data-ttu-id="4a87f-175">使用 `>` 逸出 ">" 結束標記。</span><span class="sxs-lookup"><span data-stu-id="4a87f-175">Use `>` to escape the end tag ">".</span></span>

- <span data-ttu-id="4a87f-176">您必須將專屬於用來處理標記延伸之 WPF XAML 剖析器行為的字元逸出 (使用反斜線 `\`)。</span><span class="sxs-lookup"><span data-stu-id="4a87f-176">You must escape (using backslash `\`) characters that are special to the WPF XAML parser behavior for processing a markup extension.</span></span>

  - <span data-ttu-id="4a87f-177">反斜線 (`\`) 本身是逸出字元。</span><span class="sxs-lookup"><span data-stu-id="4a87f-177">Backslash (`\`) is the escape character itself.</span></span>

  - <span data-ttu-id="4a87f-178">等號 (`=`) 會分隔屬性名稱和屬性值。</span><span class="sxs-lookup"><span data-stu-id="4a87f-178">The equal sign (`=`) separates property name from property value.</span></span>

  - <span data-ttu-id="4a87f-179">逗號 (`,`) 會分隔屬性。</span><span class="sxs-lookup"><span data-stu-id="4a87f-179">Comma (`,`) separates properties.</span></span>

  - <span data-ttu-id="4a87f-180">右大括號 (`}`) 是標記延伸的結尾。</span><span class="sxs-lookup"><span data-stu-id="4a87f-180">The right curly brace (`}`) is the end of a markup extension.</span></span>

> [!NOTE]
> <span data-ttu-id="4a87f-181">技術上來說，這些逸出也適用於分鏡腳本屬性路徑，但您通常會周遊現有 WPF 物件的物件模型，因此應該不需要逸出。</span><span class="sxs-lookup"><span data-stu-id="4a87f-181">Technically, these escapes work for a storyboard property path also, but you are usually traversing object models for existing WPF objects, and escaping should be unnecessary.</span></span>

<a name="databinding_sa"></a>

## <a name="propertypath-for-animation-targets"></a><span data-ttu-id="4a87f-182">動畫目標的 PropertyPath</span><span class="sxs-lookup"><span data-stu-id="4a87f-182">PropertyPath for Animation Targets</span></span>

<span data-ttu-id="4a87f-183">動畫的目標屬性必須是接受<xref:System.Windows.Freezable>或基本類型的相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="4a87f-183">The target property of an animation must be a dependency property that takes either a <xref:System.Windows.Freezable> or a primitive type.</span></span> <span data-ttu-id="4a87f-184">不過，類型上的目標屬性和最終動畫屬性可存在於不同物件上。</span><span class="sxs-lookup"><span data-stu-id="4a87f-184">However, the targeted property on a type and the eventual animated property can exist on different objects.</span></span> <span data-ttu-id="4a87f-185">對動畫來說，屬性路徑是用來定義具名動畫目標物件的屬性與所需目標動畫屬性之間的關係，方法則是周遊屬性值中的物件-屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="4a87f-185">For animations, a property path is used to define the connection between the named animation target object's property and the intended target animation property, by traversing object-property relationships in the property values.</span></span>

<a name="general"></a>

### <a name="general-object-property-considerations-for-animations"></a><span data-ttu-id="4a87f-186">動畫的一般物件-屬性考量</span><span class="sxs-lookup"><span data-stu-id="4a87f-186">General Object-Property Considerations for Animations</span></span>

<span data-ttu-id="4a87f-187">如需一般動畫概念的詳細資訊，請參閱[分鏡腳本概觀](../graphics-multimedia/storyboards-overview.md)和[動畫概觀](../graphics-multimedia/animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4a87f-187">For more information on animation concepts in general, see [Storyboards Overview](../graphics-multimedia/storyboards-overview.md) and [Animation Overview](../graphics-multimedia/animation-overview.md).</span></span>

<span data-ttu-id="4a87f-188">要製作動畫的實值型別或屬性必須是<xref:System.Windows.Freezable>型別或基本型別。</span><span class="sxs-lookup"><span data-stu-id="4a87f-188">The value type or the property being animated must be either a <xref:System.Windows.Freezable> type or a primitive.</span></span> <span data-ttu-id="4a87f-189">啟動路徑的屬性必須解析為存在於指定<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>類型上之相依性屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="4a87f-189">The property that starts the path must resolve to be the name of a dependency property that exists on the specified <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> type.</span></span>

<span data-ttu-id="4a87f-190">為了支援<xref:System.Windows.Freezable>複製已凍結的動畫，所指定的物件<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>必須是<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>衍生類別。</span><span class="sxs-lookup"><span data-stu-id="4a87f-190">In order to support cloning for animating a <xref:System.Windows.Freezable> that is already frozen, the object specified by <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> must be a <xref:System.Windows.FrameworkElement> or <xref:System.Windows.FrameworkContentElement> derived class.</span></span>

<a name="singlestepanim"></a>

### <a name="single-property-on-the-target-object"></a><span data-ttu-id="4a87f-191">目標物件上的單一屬性</span><span class="sxs-lookup"><span data-stu-id="4a87f-191">Single Property on the Target Object</span></span>

```xml
<animation Storyboard.TargetProperty="propertyName" ... />
```

<span data-ttu-id="4a87f-192">`propertyName`必須解析為存在於指定<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>類型上之相依性屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="4a87f-192">`propertyName` must resolve to be the name of a dependency property that exists on the specified <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> type.</span></span>

<a name="indirectanim"></a>

### <a name="indirect-property-targeting"></a><span data-ttu-id="4a87f-193">間接屬性目標</span><span class="sxs-lookup"><span data-stu-id="4a87f-193">Indirect Property Targeting</span></span>

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2" ... />
```

<span data-ttu-id="4a87f-194">`propertyName`必須是實<xref:System.Windows.Freezable>數值型別或基本類型的屬性，其存在於指定<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>的類型上。</span><span class="sxs-lookup"><span data-stu-id="4a87f-194">`propertyName` must be a property that is either a <xref:System.Windows.Freezable> value type or a primitive, which exists on the specified <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> type.</span></span>

<span data-ttu-id="4a87f-195">`propertyName2` 必須是存在於值為 `propertyName` 之物件上的相依性屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="4a87f-195">`propertyName2` must be the name of a dependency property that exists on the object that is the value of `propertyName`.</span></span> <span data-ttu-id="4a87f-196">換句話說， `propertyName2`必須當做類型`propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>的相依性屬性存在。</span><span class="sxs-lookup"><span data-stu-id="4a87f-196">In other words, `propertyName2` must exist as a dependency property on the type that is the `propertyName` <xref:System.Windows.DependencyProperty.PropertyType%2A>.</span></span>

<span data-ttu-id="4a87f-197">由於已套用樣式和範本，因此需要間接設定動畫的目標。</span><span class="sxs-lookup"><span data-stu-id="4a87f-197">Indirect targeting of animations is necessary because of applied styles and templates.</span></span> <span data-ttu-id="4a87f-198">若要以動畫為目標，您需要目標<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>物件上的，而且該名稱是由[x：Name](../../../desktop-wpf/xaml-services/xname-directive.md)或<xref:System.Windows.FrameworkElement.Name%2A>所建立。</span><span class="sxs-lookup"><span data-stu-id="4a87f-198">In order to target an animation, you need a <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> on a target object, and that name is established by [x:Name](../../../desktop-wpf/xaml-services/xname-directive.md) or <xref:System.Windows.FrameworkElement.Name%2A>.</span></span> <span data-ttu-id="4a87f-199">雖然範本和樣式元素也可以有名稱，但那些名稱只在樣式和範本的名稱範圍內有效</span><span class="sxs-lookup"><span data-stu-id="4a87f-199">Although template and style elements also can have names, those names are only valid within the namescope of the style and template.</span></span> <span data-ttu-id="4a87f-200">(如果範本和樣式會與應用程式標記共用名稱範圍，則名稱不能是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4a87f-200">(If templates and styles did share namescopes with application markup, names couldn't be unique.</span></span> <span data-ttu-id="4a87f-201">樣式和範本實際上會在實例之間共用，而且會永久保存重複的名稱）。因此，如果您可能想要建立動畫之專案的個別屬性來自樣式或範本，您必須從不是來自樣式範本的命名專案實例開始，然後以樣式或樣板視覺化樹狀結構的目標來到達您想要建立動畫的屬性。</span><span class="sxs-lookup"><span data-stu-id="4a87f-201">The styles and templates are literally shared between instances and would perpetuate duplicate names.) Thus, if the individual properties of an element that you might wish to animate came from a style or template, you need to start with a named element instance that is not from a style template, and then target into the style or template visual tree to arrive at the property you wish to animate.</span></span>

<span data-ttu-id="4a87f-202"><xref:System.Windows.Controls.Panel.Background%2A>例如，的<xref:System.Windows.Controls.Panel>屬性是來自主題範本的完整<xref:System.Windows.Media.Brush> （實際上是<xref:System.Windows.Media.SolidColorBrush>）。</span><span class="sxs-lookup"><span data-stu-id="4a87f-202">For instance, the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Panel> is a complete <xref:System.Windows.Media.Brush> (actually a <xref:System.Windows.Media.SolidColorBrush>) that came from a theme template.</span></span> <span data-ttu-id="4a87f-203">若要完全<xref:System.Windows.Media.Brush>建立動畫，必須是 BrushAnimation （可能是每個<xref:System.Windows.Media.Brush>類型都有一個），而且沒有這種類型。</span><span class="sxs-lookup"><span data-stu-id="4a87f-203">To animate a <xref:System.Windows.Media.Brush> completely, there would need to be a BrushAnimation (probably one for every <xref:System.Windows.Media.Brush> type) and there is no such type.</span></span> <span data-ttu-id="4a87f-204">若要建立筆刷的動畫，您可以改為<xref:System.Windows.Media.Brush>建立特定類型之屬性的動畫。</span><span class="sxs-lookup"><span data-stu-id="4a87f-204">To animate a Brush, you instead animate properties of a particular <xref:System.Windows.Media.Brush> type.</span></span> <span data-ttu-id="4a87f-205">您必須從<xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Media.SolidColorBrush.Color%2A>取得，才能在<xref:System.Windows.Media.Animation.ColorAnimation>該處套用。</span><span class="sxs-lookup"><span data-stu-id="4a87f-205">You need to get from <xref:System.Windows.Media.SolidColorBrush> to its <xref:System.Windows.Media.SolidColorBrush.Color%2A> to apply a <xref:System.Windows.Media.Animation.ColorAnimation> there.</span></span> <span data-ttu-id="4a87f-206">此範例的屬性路徑就是 `Background.Color`。</span><span class="sxs-lookup"><span data-stu-id="4a87f-206">The property path for this example would be `Background.Color`.</span></span>

<a name="attachedanim"></a>

### <a name="attached-properties"></a><span data-ttu-id="4a87f-207">附加屬性</span><span class="sxs-lookup"><span data-stu-id="4a87f-207">Attached Properties</span></span>

```xml
<animation Storyboard.TargetProperty="(ownerType.propertyName)" ... />
```

<span data-ttu-id="4a87f-208">括弧表示中的這個屬性<xref:System.Windows.PropertyPath>應使用部分限定性來建立。</span><span class="sxs-lookup"><span data-stu-id="4a87f-208">The parentheses indicate that this property in a <xref:System.Windows.PropertyPath> should be constructed using a partial qualification.</span></span> <span data-ttu-id="4a87f-209">它可使用 XML 命名空間來尋找此類型。</span><span class="sxs-lookup"><span data-stu-id="4a87f-209">It can use an XML namespace to find the type.</span></span> <span data-ttu-id="4a87f-210">透過`ownerType`每個元件中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的<xref:System.Windows.Markup.XmlnsDefinitionAttribute>宣告，搜尋處理器可以存取的類型。</span><span class="sxs-lookup"><span data-stu-id="4a87f-210">The `ownerType` searches types that a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor has access to, through the <xref:System.Windows.Markup.XmlnsDefinitionAttribute> declarations in each assembly.</span></span> <span data-ttu-id="4a87f-211">大部分的應用程式都有對應至 `http://schemas.microsoft.com/winfx/2006/xaml/presentation` 命名空間的預設 XML 命名空間，因此，前置詞通常只需用於自訂類型或該命名空間以外的類型。</span><span class="sxs-lookup"><span data-stu-id="4a87f-211">Most applications have the default XML namespace mapped to the `http://schemas.microsoft.com/winfx/2006/xaml/presentation` namespace, so a prefix is usually only necessary for custom types or types otherwise outside that namespace.</span></span> <span data-ttu-id="4a87f-212">`propertyName` 必須解析為存在於 `ownerType` 上的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="4a87f-212">`propertyName` must resolve to be the name of a property existing on the `ownerType`.</span></span> <span data-ttu-id="4a87f-213">指定為`propertyName`的屬性必須是<xref:System.Windows.DependencyProperty>。</span><span class="sxs-lookup"><span data-stu-id="4a87f-213">The property specified as `propertyName` must be a <xref:System.Windows.DependencyProperty>.</span></span> <span data-ttu-id="4a87f-214">(所有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 附加屬性都會實作為相依性屬性，因此只有自訂附加屬性才會發生此問題)。</span><span class="sxs-lookup"><span data-stu-id="4a87f-214">(All [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] attached properties are implemented as dependency properties, so this issue is only of concern for custom attached properties.)</span></span>

<a name="indexanim"></a>

### <a name="indexers"></a><span data-ttu-id="4a87f-215">索引子</span><span class="sxs-lookup"><span data-stu-id="4a87f-215">Indexers</span></span>

```xml
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" ... />
```

<span data-ttu-id="4a87f-216">大部分的相依性<xref:System.Windows.Freezable>屬性或類型都不支援索引子。</span><span class="sxs-lookup"><span data-stu-id="4a87f-216">Most dependency properties or <xref:System.Windows.Freezable> types do not support an indexer.</span></span> <span data-ttu-id="4a87f-217">因此，若要在動畫路徑中使用索引子，就只能在具名目標上開始鏈結的屬性與最終動畫屬性之間的中繼位置上使用。</span><span class="sxs-lookup"><span data-stu-id="4a87f-217">Therefore, the only usage for an indexer in an animation path is at an intermediate position between the property that starts the chain on the named target and the eventual animated property.</span></span> <span data-ttu-id="4a87f-218">在所提供的語法中，就是 `propertyName2`。</span><span class="sxs-lookup"><span data-stu-id="4a87f-218">In the provided syntax, that is `propertyName2`.</span></span> <span data-ttu-id="4a87f-219">例如，如果中繼屬性是中的集合（例如<xref:System.Windows.Media.TransformGroup>），則可能需要索引子使用方式。 `RenderTransform.Children[1].Angle`</span><span class="sxs-lookup"><span data-stu-id="4a87f-219">For instance, an indexer usage might be necessary if the intermediate property is a collection such as <xref:System.Windows.Media.TransformGroup>, in a property path such as `RenderTransform.Children[1].Angle`.</span></span>

<a name="ppincode"></a>

## <a name="propertypath-in-code"></a><span data-ttu-id="4a87f-220">程式碼中的 PropertyPath</span><span class="sxs-lookup"><span data-stu-id="4a87f-220">PropertyPath in Code</span></span>

<span data-ttu-id="4a87f-221">的程式碼<xref:System.Windows.PropertyPath>使用方式（包括如何建立<xref:System.Windows.PropertyPath>）記載于的參考主題<xref:System.Windows.PropertyPath>。</span><span class="sxs-lookup"><span data-stu-id="4a87f-221">Code usage for <xref:System.Windows.PropertyPath>, including how to construct a <xref:System.Windows.PropertyPath>, is documented in the reference topic for <xref:System.Windows.PropertyPath>.</span></span>

<span data-ttu-id="4a87f-222">一般而言， <xref:System.Windows.PropertyPath>設計成使用兩個不同的函式，一個用於系結使用方式和最簡單的動畫用法，另一個用於複雜的動畫使用方式。</span><span class="sxs-lookup"><span data-stu-id="4a87f-222">In general, <xref:System.Windows.PropertyPath> is designed to use two different constructors, one for the binding usages and simplest animation usages, and one for the complex animation usages.</span></span> <span data-ttu-id="4a87f-223"><xref:System.Windows.PropertyPath.%23ctor%28System.Object%29>將簽章用於系結使用方式，其中物件為字串。</span><span class="sxs-lookup"><span data-stu-id="4a87f-223">Use the <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> signature for binding usages, where the object is a string.</span></span> <span data-ttu-id="4a87f-224"><xref:System.Windows.PropertyPath.%23ctor%28System.Object%29>使用單一步驟動畫路徑的簽章，其中物件為<xref:System.Windows.DependencyProperty>。</span><span class="sxs-lookup"><span data-stu-id="4a87f-224">Use the <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> signature for one-step animation paths, where the object is a <xref:System.Windows.DependencyProperty>.</span></span> <span data-ttu-id="4a87f-225">針對複雜<xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29>的動畫使用簽章。</span><span class="sxs-lookup"><span data-stu-id="4a87f-225">Use the <xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> signature for complex animations.</span></span> <span data-ttu-id="4a87f-226">後面這個建構函式會針對第一個參數使用語彙基元字串，並使用物件陣列來填滿語彙基元字串中的位置，以定義屬性路徑關聯性。</span><span class="sxs-lookup"><span data-stu-id="4a87f-226">This latter constructor uses a token string for the first parameter and an array of objects that fill positions in the token string to define a property path relationship.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a87f-227">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a87f-227">See also</span></span>

- <xref:System.Windows.PropertyPath>
- [<span data-ttu-id="4a87f-228">資料系結總覽</span><span class="sxs-lookup"><span data-stu-id="4a87f-228">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="4a87f-229">分鏡腳本概觀</span><span class="sxs-lookup"><span data-stu-id="4a87f-229">Storyboards Overview</span></span>](../graphics-multimedia/storyboards-overview.md)
