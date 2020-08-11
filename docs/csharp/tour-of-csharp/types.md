---
title: 定義類型及其成員-C 的教學課程#
description: '程式的建立區塊為類型。 瞭解如何在 c # 中建立類別、結構、介面等等。'
ms.date: 08/06/2020
ms.openlocfilehash: 69d6f0fe1e11f287fb5e385761fc210a61929d10
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88068513"
---
# <a name="types-and-members"></a><span data-ttu-id="2f034-104">類型和成員</span><span class="sxs-lookup"><span data-stu-id="2f034-104">Types and members</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="2f034-105">類別與物件</span><span class="sxs-lookup"><span data-stu-id="2f034-105">Classes and objects</span></span>

<span data-ttu-id="2f034-106">*類別*是 c # 的最基本類型。</span><span class="sxs-lookup"><span data-stu-id="2f034-106">*Classes* are the most fundamental of C#’s types.</span></span> <span data-ttu-id="2f034-107">類別是以單一單位結合狀態 (欄位) 和動作 (方法及其他函式成員) 的資料結構。</span><span class="sxs-lookup"><span data-stu-id="2f034-107">A class is a data structure that combines state (fields) and actions (methods and other function members) in a single unit.</span></span> <span data-ttu-id="2f034-108">類別會提供類別*實例*的定義，也稱為*物件*。</span><span class="sxs-lookup"><span data-stu-id="2f034-108">A class provides a definition for *instances* of the class, also known as *objects*.</span></span> <span data-ttu-id="2f034-109">類別支援「繼承」\*\* 和「多型」**，這些是可供「衍生類別」** 將「基底類別」\*\* 延伸及特製化的機制。</span><span class="sxs-lookup"><span data-stu-id="2f034-109">Classes support *inheritance* and *polymorphism*, mechanisms whereby *derived classes* can extend and specialize *base classes*.</span></span>

<span data-ttu-id="2f034-110">建立新類別時，是使用類別宣告來建立。</span><span class="sxs-lookup"><span data-stu-id="2f034-110">New classes are created using class declarations.</span></span> <span data-ttu-id="2f034-111">類別宣告的開頭為標頭。</span><span class="sxs-lookup"><span data-stu-id="2f034-111">A class declaration starts with a header.</span></span> <span data-ttu-id="2f034-112">標頭會指定：</span><span class="sxs-lookup"><span data-stu-id="2f034-112">The header specifies:</span></span>

- <span data-ttu-id="2f034-113">類別的屬性和修飾詞</span><span class="sxs-lookup"><span data-stu-id="2f034-113">The attributes and modifiers of the class</span></span>
- <span data-ttu-id="2f034-114">類別的名稱</span><span class="sxs-lookup"><span data-stu-id="2f034-114">The name of the class</span></span>
- <span data-ttu-id="2f034-115">從[基類](#base-classes)繼承時，會 (基類) </span><span class="sxs-lookup"><span data-stu-id="2f034-115">The base class (when inheriting from a [base class](#base-classes))</span></span>
- <span data-ttu-id="2f034-116">類別所實作為的介面。</span><span class="sxs-lookup"><span data-stu-id="2f034-116">The interfaces implemented by the class.</span></span>

<span data-ttu-id="2f034-117">此標頭後面會接著類別主體，此主體是由在 `{` 與 `}` 分隔符號之間撰寫的成員宣告清單所組成。</span><span class="sxs-lookup"><span data-stu-id="2f034-117">The header is followed by the class body, which consists of a list of member declarations written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="2f034-118">下列程式碼顯示名為之簡單類別的宣告 `Point` ：</span><span class="sxs-lookup"><span data-stu-id="2f034-118">The following code shows a declaration of a simple class named `Point`:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="PointClass":::

<span data-ttu-id="2f034-119">建立類別執行個體時，是使用 `new` 運算子來建立，此運算子會為新執行個體配置記憶體、叫用建構函式來將執行個體初始化，然後傳回對執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="2f034-119">Instances of classes are created using the `new` operator, which allocates memory for a new instance, invokes a constructor to initialize the instance, and returns a reference to the instance.</span></span> <span data-ttu-id="2f034-120">下列語句會建立兩個 `Point` 物件，並在兩個變數中儲存這些物件的參考：</span><span class="sxs-lookup"><span data-stu-id="2f034-120">The following statements create two `Point` objects and store references to those objects in two variables:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="CreatePoints":::

<span data-ttu-id="2f034-121">當物件不再可供存取時，系統會自動回收物件所佔用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="2f034-121">The memory occupied by an object is automatically reclaimed when the object is no longer reachable.</span></span> <span data-ttu-id="2f034-122">這不是必要的，也不可能在 c # 中明確地解除配置物件。</span><span class="sxs-lookup"><span data-stu-id="2f034-122">It's neither necessary nor possible to explicitly deallocate objects in C#.</span></span>

### <a name="type-parameters"></a><span data-ttu-id="2f034-123">型別參數</span><span class="sxs-lookup"><span data-stu-id="2f034-123">Type parameters</span></span>

<span data-ttu-id="2f034-124">泛型類別會定義[***型別參數***](../programming-guide/generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2f034-124">Generic classes define [***type parameters***](../programming-guide/generics/index.md).</span></span> <span data-ttu-id="2f034-125">型別參數是以角括弧括住之型別參數名稱的清單。</span><span class="sxs-lookup"><span data-stu-id="2f034-125">Type parameters are a list of type parameter names enclosed in angle brackets.</span></span> <span data-ttu-id="2f034-126">類型參數會遵循類別名稱。</span><span class="sxs-lookup"><span data-stu-id="2f034-126">Type parameters follow the class name.</span></span> <span data-ttu-id="2f034-127">接著，就可以在類別宣告的主體中使用這些型別參數，來定義類別的成員。</span><span class="sxs-lookup"><span data-stu-id="2f034-127">The type parameters can then be used in the body of the class declarations to define the members of the class.</span></span> <span data-ttu-id="2f034-128">在下列範例中，`Pair` 的型別參數是 `TFirst` 和 `TSecond`：</span><span class="sxs-lookup"><span data-stu-id="2f034-128">In the following example, the type parameters of `Pair` are `TFirst` and `TSecond`:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DefinePairClass":::

<span data-ttu-id="2f034-129">類別型別若宣告為會採用型別參數，即稱為「泛型類別型別」\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f034-129">A class type that is declared to take type parameters is called a *generic class type*.</span></span> <span data-ttu-id="2f034-130">結構、介面和委派類型也可以是泛型。</span><span class="sxs-lookup"><span data-stu-id="2f034-130">Struct, interface, and delegate types can also be generic.</span></span>
<span data-ttu-id="2f034-131">使用泛型類別時，必須為每個型別參數提供型別參數：</span><span class="sxs-lookup"><span data-stu-id="2f034-131">When the generic class is used, type arguments must be provided for each of the type parameters:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="CreatePairObject":::

<span data-ttu-id="2f034-132">泛型型別若已有提供的型別參數 (如上述的 `Pair<int,string>`)，即稱為「建構的型別」\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f034-132">A generic type with type arguments provided, like `Pair<int,string>` above, is called a *constructed type*.</span></span>

### <a name="base-classes"></a><span data-ttu-id="2f034-133">基底類別</span><span class="sxs-lookup"><span data-stu-id="2f034-133">Base classes</span></span>

<span data-ttu-id="2f034-134">類別宣告可以指定基類。</span><span class="sxs-lookup"><span data-stu-id="2f034-134">A class declaration may specify a base class.</span></span> <span data-ttu-id="2f034-135">請在類別名稱和類型參數後面加上冒號和基類的名稱。</span><span class="sxs-lookup"><span data-stu-id="2f034-135">Follow the class name and type parameters with a colon and the name of the base class.</span></span> <span data-ttu-id="2f034-136">省略基底類別規格即等同於衍生自類型 `object`。</span><span class="sxs-lookup"><span data-stu-id="2f034-136">Omitting a base class specification is the same as deriving from type `object`.</span></span> <span data-ttu-id="2f034-137">在下列範例中，的基類 `Point3D` 是 `Point` 。</span><span class="sxs-lookup"><span data-stu-id="2f034-137">In the following example, the base class of `Point3D` is `Point`.</span></span> <span data-ttu-id="2f034-138">在第一個範例中，的基類 `Point` 是 `object` ：</span><span class="sxs-lookup"><span data-stu-id="2f034-138">From the first example, the base class of `Point` is `object`:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="Create3DPoint":::

<span data-ttu-id="2f034-139">類別會繼承其基底類別的成員。</span><span class="sxs-lookup"><span data-stu-id="2f034-139">A class inherits the members of its base class.</span></span> <span data-ttu-id="2f034-140">繼承表示類別會隱含地包含其基類的所有成員。</span><span class="sxs-lookup"><span data-stu-id="2f034-140">Inheritance means that a class implicitly contains almost all members of its base class.</span></span> <span data-ttu-id="2f034-141">類別不會繼承實例和靜態的函式，以及完成項。</span><span class="sxs-lookup"><span data-stu-id="2f034-141">A class doesn't inherit the instance and static constructors, and the finalizer.</span></span> <span data-ttu-id="2f034-142">衍生類別可以將新成員加入至它所繼承的成員，但無法移除繼承成員的定義。</span><span class="sxs-lookup"><span data-stu-id="2f034-142">A derived class can add new members to those members it inherits, but it can't remove the definition of an inherited member.</span></span> <span data-ttu-id="2f034-143">在上述範例中，會 `Point3D` `X` 從繼承和 `Y` 成員 `Point` ，而且每個 `Point3D` 實例都包含三個屬性：、 `X` `Y` 和 `Z` 。</span><span class="sxs-lookup"><span data-stu-id="2f034-143">In the previous example, `Point3D` inherits the `X` and `Y` members from `Point`, and every `Point3D` instance contains three properties, `X`, `Y`, and `Z`.</span></span>

<span data-ttu-id="2f034-144">在類別型別到其任何基底類別型別之間都存在著隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="2f034-144">An implicit conversion exists from a class type to any of its base class types.</span></span> <span data-ttu-id="2f034-145">類別類型的變數可以參考該類別的實例，或任何衍生類別的實例。</span><span class="sxs-lookup"><span data-stu-id="2f034-145">A variable of a class type can reference an instance of that class or an instance of any derived class.</span></span> <span data-ttu-id="2f034-146">例如，以先前的類別宣告為例，`Point` 型別的變數可以參考 `Point` 或 `Point3D`：</span><span class="sxs-lookup"><span data-stu-id="2f034-146">For example, given the previous class declarations, a variable of type `Point` can reference either a `Point` or a `Point3D`:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="ImplicitCastToBase":::

## <a name="structs"></a><span data-ttu-id="2f034-147">結構</span><span class="sxs-lookup"><span data-stu-id="2f034-147">Structs</span></span>

<span data-ttu-id="2f034-148">類別會定義支援繼承和多型的類型。</span><span class="sxs-lookup"><span data-stu-id="2f034-148">Classes define types that support inheritance and polymorphism.</span></span> <span data-ttu-id="2f034-149">它們可讓您根據衍生類別的階層來建立複雜的行為。</span><span class="sxs-lookup"><span data-stu-id="2f034-149">They enable you to create sophisticated behaviors based on hierarchies of derived classes.</span></span> <span data-ttu-id="2f034-150">相反地，[***結構***](../language-reference/builtin-types/struct.md)類型是較簡單的類型，其主要目的是用來儲存資料值。</span><span class="sxs-lookup"><span data-stu-id="2f034-150">By contrast, [***struct***](../language-reference/builtin-types/struct.md) types are simpler types whose primary purpose is to store data values.</span></span> <span data-ttu-id="2f034-151">結構無法宣告基底類型;它們會隱含衍生自 <xref:System.ValueType?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="2f034-151">Structs can't declare a base type; they implicitly derive from <xref:System.ValueType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2f034-152">您無法 `struct` 從類型衍生其他類型 `struct` 。</span><span class="sxs-lookup"><span data-stu-id="2f034-152">You can't derive other `struct` types from a `struct` type.</span></span> <span data-ttu-id="2f034-153">它們是隱含密封的。</span><span class="sxs-lookup"><span data-stu-id="2f034-153">They're implicitly sealed.</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="PointStruct":::

## <a name="interfaces"></a><span data-ttu-id="2f034-154">介面</span><span class="sxs-lookup"><span data-stu-id="2f034-154">Interfaces</span></span>

<span data-ttu-id="2f034-155">[***介面***](../programming-guide/interfaces/index.md)會定義可由類別和結構來執行的合約。</span><span class="sxs-lookup"><span data-stu-id="2f034-155">An [***interface***](../programming-guide/interfaces/index.md) defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="2f034-156">介面可以包含方法、屬性、事件和索引子。</span><span class="sxs-lookup"><span data-stu-id="2f034-156">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="2f034-157">介面通常不會提供它所定義之成員的執行，它只會指定必須由實介面的類別或結構所提供的成員。</span><span class="sxs-lookup"><span data-stu-id="2f034-157">An interface typically doesn't provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="2f034-158">介面可以採用「多重繼承」\*\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2f034-158">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="2f034-159">在下列範例中，介面 `IComboBox` 同時繼承自 `ITextBox` 和 `IListBox`。</span><span class="sxs-lookup"><span data-stu-id="2f034-159">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="FirstInterfaces":::

<span data-ttu-id="2f034-160">類別和結構可以實作多個介面。</span><span class="sxs-lookup"><span data-stu-id="2f034-160">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="2f034-161">在下列範例中，類別 `EditBox` 可以實作 `IControl` 與 `IDataBound` 兩者。</span><span class="sxs-lookup"><span data-stu-id="2f034-161">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="ImplementInterfaces":::

<span data-ttu-id="2f034-162">當類別或結構實作特定介面時，可以將該類別或結構的執行個體隱含地轉換為該介面型別。</span><span class="sxs-lookup"><span data-stu-id="2f034-162">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="2f034-163">例如：</span><span class="sxs-lookup"><span data-stu-id="2f034-163">For example</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="UseInterfaces":::

## <a name="enums"></a><span data-ttu-id="2f034-164">列舉</span><span class="sxs-lookup"><span data-stu-id="2f034-164">Enums</span></span>

<span data-ttu-id="2f034-165">[***列舉***](../language-reference/builtin-types/enum.md)型別會定義一組常數值。</span><span class="sxs-lookup"><span data-stu-id="2f034-165">An [***Enum***](../language-reference/builtin-types/enum.md) type defines a set of constant values.</span></span> <span data-ttu-id="2f034-166">下列宣告 `enum` 的常數會定義不同的根蔬菜：</span><span class="sxs-lookup"><span data-stu-id="2f034-166">The following `enum` declares constants that define different root vegetables:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="EnumDeclaration":::

<span data-ttu-id="2f034-167">您也可以將定義為 `enum` 用於旗標的。</span><span class="sxs-lookup"><span data-stu-id="2f034-167">You can also define an `enum` to be used in combination as flags.</span></span> <span data-ttu-id="2f034-168">下列宣告會宣告四個季節的一組旗標。</span><span class="sxs-lookup"><span data-stu-id="2f034-168">The following declaration declares a set of flags for the four seasons.</span></span> <span data-ttu-id="2f034-169">可能會套用季節的任何組合，包括 `All` 包含所有季節的值：</span><span class="sxs-lookup"><span data-stu-id="2f034-169">Any combination of the seasons may be applied, including an `All` value that includes all seasons:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="FlagsEnumDeclaration":::

<span data-ttu-id="2f034-170">下列範例顯示上述列舉的宣告：</span><span class="sxs-lookup"><span data-stu-id="2f034-170">The following example shows declarations of both the preceding enums:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="UsingEnums":::

## <a name="nullable-types"></a><span data-ttu-id="2f034-171">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="2f034-171">Nullable types</span></span>

<span data-ttu-id="2f034-172">任何類型的變數都可能宣告為***不可為 null***或***可為 null***。</span><span class="sxs-lookup"><span data-stu-id="2f034-172">Variables of any type may be declared as ***non-nullable*** or ***nullable***.</span></span> <span data-ttu-id="2f034-173">可為 null 的變數可以保留額外的 `null` 值，指出沒有任何值。</span><span class="sxs-lookup"><span data-stu-id="2f034-173">A nullable variable can hold an additional `null` value, indicating no value.</span></span> <span data-ttu-id="2f034-174">可為 null 的實數值型別 (結構或列舉) 以表示 <xref:System.Nullable%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="2f034-174">Nullable Value types (structs or enums) are represented by <xref:System.Nullable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2f034-175">不可為 null 且可為 Null 的參考型別都是以基礎參考型別表示。</span><span class="sxs-lookup"><span data-stu-id="2f034-175">Non-nullable and Nullable Reference types are both represented by the underlying reference type.</span></span> <span data-ttu-id="2f034-176">區別是由編譯器和部分程式庫所讀取的中繼資料來表示。</span><span class="sxs-lookup"><span data-stu-id="2f034-176">The distinction is represented by metadata read by the compiler and some libraries.</span></span> <span data-ttu-id="2f034-177">當可為 null 參考取值時，編譯器會提供警告，而不會先檢查其值是否為 `null` 。</span><span class="sxs-lookup"><span data-stu-id="2f034-177">The compiler provides warnings when nullable references are dereferenced without first checking their value against `null`.</span></span> <span data-ttu-id="2f034-178">當不可為 null 的參考指派給可能是的值時，編譯器也會提供警告 `null` 。</span><span class="sxs-lookup"><span data-stu-id="2f034-178">The compiler also provides warnings when non-nullable references are assigned to a value that may be `null`.</span></span> <span data-ttu-id="2f034-179">下列範例會宣告***可為 null 的 int***，將其初始化為 `null` 。</span><span class="sxs-lookup"><span data-stu-id="2f034-179">The following example declares a ***nullable int***, initializing it to `null`.</span></span> <span data-ttu-id="2f034-180">然後，它會將值設定為 `5` 。</span><span class="sxs-lookup"><span data-stu-id="2f034-180">Then, it sets the value to `5`.</span></span> <span data-ttu-id="2f034-181">它會使用***可為 null 的字串***來示範相同的概念。</span><span class="sxs-lookup"><span data-stu-id="2f034-181">It demonstrates the same concept with a ***nullable string***.</span></span> <span data-ttu-id="2f034-182">如需詳細資訊，請參閱[可為 null 的實數值型別](../language-reference/builtin-types/nullable-value-types.md)和[nullable 參考型別](../nullable-references.md)。</span><span class="sxs-lookup"><span data-stu-id="2f034-182">For more information, see [nullable value types](../language-reference/builtin-types/nullable-value-types.md) and [nullable reference types](../nullable-references.md).</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DeclareNullable":::

## <a name="tuples"></a><span data-ttu-id="2f034-183">Tuple</span><span class="sxs-lookup"><span data-stu-id="2f034-183">Tuples</span></span>

<span data-ttu-id="2f034-184">C # 支援[***元***](../language-reference/builtin-types/value-tuples.md)組，其提供精簡的語法，以將多個資料元素群組在輕量資料結構中。</span><span class="sxs-lookup"><span data-stu-id="2f034-184">C# supports [***tuples***](../language-reference/builtin-types/value-tuples.md), which provides concise syntax to group multiple data elements in a lightweight data structure.</span></span> <span data-ttu-id="2f034-185">您可以在和之間宣告成員的類型和名稱，以具現化元組 `(` `)` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2f034-185">You instantiate a tuple by declaring the types and names of the members between `(` and `)`, as shown in the following example:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DeclareTuples":::

<span data-ttu-id="2f034-186">元組提供具有多個成員之資料結構的替代方案，而不使用下一篇文章中所述的建立區塊。</span><span class="sxs-lookup"><span data-stu-id="2f034-186">Tuples provide an alternative for data structure with multiple members, without using the building blocks described in the next article.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2f034-187">[上一個](index.md) 
>[下一步](program-building-blocks.md)</span><span class="sxs-lookup"><span data-stu-id="2f034-187">[Previous](index.md)
[Next](program-building-blocks.md)</span></span>
