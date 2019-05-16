---
title: 使用偵錯工具顯示屬性增強偵錯功能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- debugger, display attributes
- DebuggerTypeProxyAttribute attribute
- debugging [.NET Framework], debugger display attributes
- DebuggerDisplayAttribute attribute
- display attributes for debugger
- DebuggerBrowsableAttribute attribute
ms.assetid: 72bb7aa9-459b-42c4-9163-9312fab4c410
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6663b4875fc2c3698b612a4958140ba199ea2669
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631926"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="9d97b-102">使用偵錯工具顯示屬性增強偵錯功能</span><span class="sxs-lookup"><span data-stu-id="9d97b-102">Enhancing Debugging with the Debugger Display Attributes</span></span>

<span data-ttu-id="9d97b-103">偵錯工具顯示屬性能讓指定並最了解該類型執行階段行為的開發人員，也指定該類型在偵錯工具中顯示的外觀。</span><span class="sxs-lookup"><span data-stu-id="9d97b-103">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="9d97b-104">此外，提供 `Target` 屬性的偵錯工具顯示屬性，也可供沒有原始程式碼背景的使用者在組件層級使用。</span><span class="sxs-lookup"><span data-stu-id="9d97b-104">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="9d97b-105"><xref:System.Diagnostics.DebuggerDisplayAttribute> 屬性控制類型或成員在偵錯工具變數視窗中顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="9d97b-105">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="9d97b-106"><xref:System.Diagnostics.DebuggerBrowsableAttribute> 屬性決定欄位或屬性是否以及如何顯示在偵錯工具變數視窗中。</span><span class="sxs-lookup"><span data-stu-id="9d97b-106">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="9d97b-107"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> 屬性會指定類型的替代類型 (或 Proxy)，並且變更在偵錯工具視窗中顯示類型的方式。</span><span class="sxs-lookup"><span data-stu-id="9d97b-107">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="9d97b-108">當您檢視有 proxy 或替代類型的變數時，proxy 會替代偵錯工具顯示視窗中的原始類型。</span><span class="sxs-lookup"><span data-stu-id="9d97b-108">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window.</span></span> <span data-ttu-id="9d97b-109">偵錯工具變數視窗只會顯示 proxy 型別的 Public 成員。</span><span class="sxs-lookup"><span data-stu-id="9d97b-109">The debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="9d97b-110">私用成員不會顯示。</span><span class="sxs-lookup"><span data-stu-id="9d97b-110">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="9d97b-111">使用 DebuggerDisplayAttribute</span><span class="sxs-lookup"><span data-stu-id="9d97b-111">Using the DebuggerDisplayAttribute</span></span>  

<span data-ttu-id="9d97b-112"><xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> 建構函式有單一引數：在類型執行個體的 [值] 一欄中顯示的字串。</span><span class="sxs-lookup"><span data-stu-id="9d97b-112">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="9d97b-113">這個字串可以包含括弧 ({ 和 })。</span><span class="sxs-lookup"><span data-stu-id="9d97b-113">This string can contain braces ({ and }).</span></span> <span data-ttu-id="9d97b-114">括弧內的文字會評估為運算式。</span><span class="sxs-lookup"><span data-stu-id="9d97b-114">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="9d97b-115">例如，下列 C# 程式碼會在選取加號 (+) 時顯示 "Count = 4"，展開偵錯工具顯示的 `MyHashtable` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="9d97b-115">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

<span data-ttu-id="9d97b-116">不處理套用至運算式參考屬性 (property) 的屬性 (attribute)。</span><span class="sxs-lookup"><span data-stu-id="9d97b-116">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="9d97b-117">在 C# 編譯器，一般運算式僅能以隱含方式存取目標類型目前執行個體的此一參考。</span><span class="sxs-lookup"><span data-stu-id="9d97b-117">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="9d97b-118">運算式有限制，不能存取別名、區域變數或指標。</span><span class="sxs-lookup"><span data-stu-id="9d97b-118">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="9d97b-119">在 C# 程式碼中，您可以使用以括弧括住的一般運算式，以隱含方式存取目標類型目前執行個體的 `this` 指標。</span><span class="sxs-lookup"><span data-stu-id="9d97b-119">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>

<span data-ttu-id="9d97b-120">例如，如果 C# 物件具有覆寫的 `ToString()`，則偵錯工具會呼叫覆寫並顯示它的結果，而不是標準的 `{<typeName>}.`。因此，如果您已覆寫 `ToString()`，就不需要使用 <xref:System.Diagnostics.DebuggerDisplayAttribute>。</span><span class="sxs-lookup"><span data-stu-id="9d97b-120">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="9d97b-121">如果兩者都使用，<xref:System.Diagnostics.DebuggerDisplayAttribute> 屬性則會優先於 `ToString()` 覆寫。</span><span class="sxs-lookup"><span data-stu-id="9d97b-121">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>

## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="9d97b-122">使用 DebuggerBrowsableAttribute</span><span class="sxs-lookup"><span data-stu-id="9d97b-122">Using the DebuggerBrowsableAttribute</span></span>
 <span data-ttu-id="9d97b-123">將 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 套用至欄位或屬性，以指定欄位或屬性在偵錯工具視窗中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="9d97b-123">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="9d97b-124">這個屬性的建構函式會使用其中一個 <xref:System.Diagnostics.DebuggerBrowsableState> 列舉值，指定下列狀態之一：</span><span class="sxs-lookup"><span data-stu-id="9d97b-124">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>

- <span data-ttu-id="9d97b-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> 指出成員未顯示在資料視窗中。</span><span class="sxs-lookup"><span data-stu-id="9d97b-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="9d97b-126">例如，對欄位的 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 使用此值，會從階層中移除欄位；當您按一下類型執行個體的加號 (+) 展開封入類型時，不會顯示欄位。</span><span class="sxs-lookup"><span data-stu-id="9d97b-126">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>

- <span data-ttu-id="9d97b-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> 指出已顯示成員，但預設不展開。</span><span class="sxs-lookup"><span data-stu-id="9d97b-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="9d97b-128">這是預設行為。</span><span class="sxs-lookup"><span data-stu-id="9d97b-128">This is the default behavior.</span></span>

- <span data-ttu-id="9d97b-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> 指出成員本身不會顯示，但如果它是陣列或集合，則會顯示其組成物件。</span><span class="sxs-lookup"><span data-stu-id="9d97b-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>

> [!NOTE]
>  <span data-ttu-id="9d97b-130">.NET Framework 2.0 版中的 Visual Basic 不支援 <xref:System.Diagnostics.DebuggerBrowsableAttribute>。</span><span class="sxs-lookup"><span data-stu-id="9d97b-130">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>

<span data-ttu-id="9d97b-131">下列程式碼範例示範，使用 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 防止它後面的屬性出現在類別的偵錯視窗中。</span><span class="sxs-lookup"><span data-stu-id="9d97b-131">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="9d97b-132">使用 DebuggerTypeProxy</span><span class="sxs-lookup"><span data-stu-id="9d97b-132">Using the DebuggerTypeProxy</span></span>
 <span data-ttu-id="9d97b-133">當您需要大幅並從本質上變更類型的偵錯檢視，但不是變更類型本身時，請使用 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9d97b-133">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="9d97b-134"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> 屬性用來指定類型的顯示 Proxy，讓開發人員調整類型的檢視。</span><span class="sxs-lookup"><span data-stu-id="9d97b-134">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="9d97b-135">這個屬性，如 <xref:System.Diagnostics.DebuggerDisplayAttribute>，可以用在組件層級；如此 <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> 屬性會指定要使用 Proxy 的類型。</span><span class="sxs-lookup"><span data-stu-id="9d97b-135">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="9d97b-136">建議的用法是，這個屬性指定的私用巢狀類型，會出現在要套用屬性的類型內。</span><span class="sxs-lookup"><span data-stu-id="9d97b-136">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="9d97b-137">顯示類型時，支援類型檢視器的運算式評估工具會檢查這個屬性。</span><span class="sxs-lookup"><span data-stu-id="9d97b-137">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="9d97b-138">如果找到屬性，運算式評估工具會用顯示 Proxy 類型替代套用屬性的類型。</span><span class="sxs-lookup"><span data-stu-id="9d97b-138">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>

 <span data-ttu-id="9d97b-139">當 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 出現時，偵錯工具變數視窗只會顯示 Proxy 類型的 Public 成員。</span><span class="sxs-lookup"><span data-stu-id="9d97b-139">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="9d97b-140">私用成員不會顯示。</span><span class="sxs-lookup"><span data-stu-id="9d97b-140">Private members are not displayed.</span></span> <span data-ttu-id="9d97b-141">屬性增強的檢視不會變更資料視窗的行為。</span><span class="sxs-lookup"><span data-stu-id="9d97b-141">The behavior of the data window is not changed by attribute-enhanced views.</span></span>

 <span data-ttu-id="9d97b-142">為避免不必要的效能損失，在使用者按一下資料視窗中類型旁的加號 (+)，或者套用 <xref:System.Diagnostics.DebuggerBrowsableAttribute> 屬性展開物件之前，不會處理顯示 Proxy 的屬性。</span><span class="sxs-lookup"><span data-stu-id="9d97b-142">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="9d97b-143">因此，顯示類型不建議套用任何屬性。</span><span class="sxs-lookup"><span data-stu-id="9d97b-143">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="9d97b-144">屬性可以而且應該套用在顯示類型的主體中。</span><span class="sxs-lookup"><span data-stu-id="9d97b-144">Attributes can and should be applied within the body of the display type.</span></span>

 <span data-ttu-id="9d97b-145">下列程式碼範例示範使用 <xref:System.Diagnostics.DebuggerTypeProxyAttribute> 指定類型，用為偵錯工具的顯示 Proxy。</span><span class="sxs-lookup"><span data-stu-id="9d97b-145">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>

```csharp
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable : Hashtable
{
    private const string TestString =
        "This should not appear in the debug window.";

    internal class HashtableDebugView
    {
        private Hashtable hashtable;
        public const string TestStringProxy =
            "This should appear in the debug window.";

        // The constructor for the type proxy class must have a
        // constructor that takes the target type as a parameter.
        public HashtableDebugView(Hashtable hashtable)
        {
            this.hashtable = hashtable;
        }
    }
}
```

## <a name="example"></a><span data-ttu-id="9d97b-146">範例</span><span class="sxs-lookup"><span data-stu-id="9d97b-146">Example</span></span>

### <a name="description"></a><span data-ttu-id="9d97b-147">描述</span><span class="sxs-lookup"><span data-stu-id="9d97b-147">Description</span></span>

<span data-ttu-id="9d97b-148">下列程式碼範例可以在 Visual Studio 以查看套用的結果中檢視<xref:System.Diagnostics.DebuggerDisplayAttribute>， <xref:System.Diagnostics.DebuggerBrowsableAttribute>，和<xref:System.Diagnostics.DebuggerTypeProxyAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="9d97b-148">The following code example can be viewed in Visual Studio to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>

### <a name="code"></a><span data-ttu-id="9d97b-149">程式碼</span><span class="sxs-lookup"><span data-stu-id="9d97b-149">Code</span></span>

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="9d97b-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d97b-150">See also</span></span>

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
