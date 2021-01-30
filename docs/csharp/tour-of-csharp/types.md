---
title: 定義類型及其成員-C 的教學課程#
description: '程式的建立要素為類型。 瞭解如何在 c # 中建立類別、結構、介面等等。'
ms.date: 08/06/2020
ms.openlocfilehash: b1ce24611fec6fdf01d5ecb8d6ae974e147c78c5
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216599"
---
# <a name="types-and-members"></a><span data-ttu-id="c70d8-104">類型和成員</span><span class="sxs-lookup"><span data-stu-id="c70d8-104">Types and members</span></span>

<span data-ttu-id="c70d8-105">C# 為物件導向語言，支援封裝、繼承和多型的概念。</span><span class="sxs-lookup"><span data-stu-id="c70d8-105">As an object-oriented language, C# supports the concepts of encapsulation, inheritance, and polymorphism.</span></span> <span data-ttu-id="c70d8-106">類別可直接繼承自一個父類別，而且可能會執行任意數目的介面。</span><span class="sxs-lookup"><span data-stu-id="c70d8-106">A class may inherit directly from one parent class, and it may implement any number of interfaces.</span></span> <span data-ttu-id="c70d8-107">覆寫父類別中虛擬方法的方法需要利用 `override` 關鍵字，避免意外重複定義。</span><span class="sxs-lookup"><span data-stu-id="c70d8-107">Methods that override virtual methods in a parent class require the `override` keyword as a way to avoid accidental redefinition.</span></span> <span data-ttu-id="c70d8-108">在 c # 中，結構就像輕量類別;它是堆疊配置的型別，可以執行介面，但不支援繼承。</span><span class="sxs-lookup"><span data-stu-id="c70d8-108">In C#, a struct is like a lightweight class; it's a stack-allocated type that can implement interfaces but doesn't support inheritance.</span></span> <span data-ttu-id="c70d8-109">C # 也提供記錄，也就是其用途主要儲存資料值的類別類型。</span><span class="sxs-lookup"><span data-stu-id="c70d8-109">C# also provides records, which are class types whose purpose is primarily storing data values.</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="c70d8-110">類別與物件</span><span class="sxs-lookup"><span data-stu-id="c70d8-110">Classes and objects</span></span>

<span data-ttu-id="c70d8-111">*類別* 是 c # 類型中最基本的一種。</span><span class="sxs-lookup"><span data-stu-id="c70d8-111">*Classes* are the most fundamental of C#’s types.</span></span> <span data-ttu-id="c70d8-112">類別是以單一單位結合狀態 (欄位) 和動作 (方法及其他函式成員) 的資料結構。</span><span class="sxs-lookup"><span data-stu-id="c70d8-112">A class is a data structure that combines state (fields) and actions (methods and other function members) in a single unit.</span></span> <span data-ttu-id="c70d8-113">類別會提供類別 *實例* 的定義，也稱為 *物件*。</span><span class="sxs-lookup"><span data-stu-id="c70d8-113">A class provides a definition for *instances* of the class, also known as *objects*.</span></span> <span data-ttu-id="c70d8-114">類別支援「繼承」和「多型」，這些是可供「衍生類別」將「基底類別」延伸及特製化的機制。</span><span class="sxs-lookup"><span data-stu-id="c70d8-114">Classes support *inheritance* and *polymorphism*, mechanisms whereby *derived classes* can extend and specialize *base classes*.</span></span>

<span data-ttu-id="c70d8-115">建立新類別時，是使用類別宣告來建立。</span><span class="sxs-lookup"><span data-stu-id="c70d8-115">New classes are created using class declarations.</span></span> <span data-ttu-id="c70d8-116">類別宣告的開頭是標頭。</span><span class="sxs-lookup"><span data-stu-id="c70d8-116">A class declaration starts with a header.</span></span> <span data-ttu-id="c70d8-117">標頭會指定：</span><span class="sxs-lookup"><span data-stu-id="c70d8-117">The header specifies:</span></span>

- <span data-ttu-id="c70d8-118">類別的屬性和修飾詞</span><span class="sxs-lookup"><span data-stu-id="c70d8-118">The attributes and modifiers of the class</span></span>
- <span data-ttu-id="c70d8-119">類別的名稱</span><span class="sxs-lookup"><span data-stu-id="c70d8-119">The name of the class</span></span>
- <span data-ttu-id="c70d8-120">從 [基類](#base-classes) 繼承時，基類 () </span><span class="sxs-lookup"><span data-stu-id="c70d8-120">The base class (when inheriting from a [base class](#base-classes))</span></span>
- <span data-ttu-id="c70d8-121">類別所執行的介面。</span><span class="sxs-lookup"><span data-stu-id="c70d8-121">The interfaces implemented by the class.</span></span>

<span data-ttu-id="c70d8-122">此標頭後面會接著類別主體，此主體是由在 `{` 與 `}` 分隔符號之間撰寫的成員宣告清單所組成。</span><span class="sxs-lookup"><span data-stu-id="c70d8-122">The header is followed by the class body, which consists of a list of member declarations written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="c70d8-123">下列程式碼顯示名為的簡單類別的宣告 `Point` ：</span><span class="sxs-lookup"><span data-stu-id="c70d8-123">The following code shows a declaration of a simple class named `Point`:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="PointClass":::

<span data-ttu-id="c70d8-124">建立類別執行個體時，是使用 `new` 運算子來建立，此運算子會為新執行個體配置記憶體、叫用建構函式來將執行個體初始化，然後傳回對執行個體的參考。</span><span class="sxs-lookup"><span data-stu-id="c70d8-124">Instances of classes are created using the `new` operator, which allocates memory for a new instance, invokes a constructor to initialize the instance, and returns a reference to the instance.</span></span> <span data-ttu-id="c70d8-125">下列語句會建立兩個 `Point` 物件，並在兩個變數中儲存這些物件的參考：</span><span class="sxs-lookup"><span data-stu-id="c70d8-125">The following statements create two `Point` objects and store references to those objects in two variables:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="CreatePoints":::

<span data-ttu-id="c70d8-126">當物件不再可供存取時，系統會自動回收物件所佔用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="c70d8-126">The memory occupied by an object is automatically reclaimed when the object is no longer reachable.</span></span> <span data-ttu-id="c70d8-127">您不需要或無法在 c # 中明確解除配置物件。</span><span class="sxs-lookup"><span data-stu-id="c70d8-127">It's not necessary or possible to explicitly deallocate objects in C#.</span></span>

### <a name="type-parameters"></a><span data-ttu-id="c70d8-128">型別參數</span><span class="sxs-lookup"><span data-stu-id="c70d8-128">Type parameters</span></span>

<span data-ttu-id="c70d8-129">泛型類別會定義 [ \* **類型參數** _](../programming-guide/generics/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c70d8-129">Generic classes define [\***type parameters** _](../programming-guide/generics/index.md).</span></span> <span data-ttu-id="c70d8-130">型別參數是以角括弧括住的型別參數名稱清單。</span><span class="sxs-lookup"><span data-stu-id="c70d8-130">Type parameters are a list of type parameter names enclosed in angle brackets.</span></span> <span data-ttu-id="c70d8-131">類型參數會在類別名稱之後。</span><span class="sxs-lookup"><span data-stu-id="c70d8-131">Type parameters follow the class name.</span></span> <span data-ttu-id="c70d8-132">接著，就可以在類別宣告的主體中使用這些型別參數，來定義類別的成員。</span><span class="sxs-lookup"><span data-stu-id="c70d8-132">The type parameters can then be used in the body of the class declarations to define the members of the class.</span></span> <span data-ttu-id="c70d8-133">在下列範例中，`Pair` 的型別參數是 `TFirst` 和 `TSecond`：</span><span class="sxs-lookup"><span data-stu-id="c70d8-133">In the following example, the type parameters of `Pair` are `TFirst` and `TSecond`:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DefinePairClass":::

<span data-ttu-id="c70d8-134">宣告為採用型別參數的類別型別稱為 _generic 類別型別 \*。</span><span class="sxs-lookup"><span data-stu-id="c70d8-134">A class type that is declared to take type parameters is called a _generic class type\*.</span></span> <span data-ttu-id="c70d8-135">結構、介面和委派類型也可以是泛型。</span><span class="sxs-lookup"><span data-stu-id="c70d8-135">Struct, interface, and delegate types can also be generic.</span></span>
<span data-ttu-id="c70d8-136">使用泛型類別時，必須為每個型別參數提供型別參數：</span><span class="sxs-lookup"><span data-stu-id="c70d8-136">When the generic class is used, type arguments must be provided for each of the type parameters:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="CreatePairObject":::

<span data-ttu-id="c70d8-137">泛型型別若已有提供的型別參數 (如上述的 `Pair<int,string>`)，即稱為「建構的型別」。</span><span class="sxs-lookup"><span data-stu-id="c70d8-137">A generic type with type arguments provided, like `Pair<int,string>` above, is called a *constructed type*.</span></span>

### <a name="base-classes"></a><span data-ttu-id="c70d8-138">基底類別</span><span class="sxs-lookup"><span data-stu-id="c70d8-138">Base classes</span></span>

<span data-ttu-id="c70d8-139">類別宣告可指定基類。</span><span class="sxs-lookup"><span data-stu-id="c70d8-139">A class declaration may specify a base class.</span></span> <span data-ttu-id="c70d8-140">請在類別名稱和類型參數後面加上冒號和基類的名稱。</span><span class="sxs-lookup"><span data-stu-id="c70d8-140">Follow the class name and type parameters with a colon and the name of the base class.</span></span> <span data-ttu-id="c70d8-141">省略基底類別規格即等同於衍生自類型 `object`。</span><span class="sxs-lookup"><span data-stu-id="c70d8-141">Omitting a base class specification is the same as deriving from type `object`.</span></span> <span data-ttu-id="c70d8-142">在下列範例中，的基類 `Point3D` 為 `Point` 。</span><span class="sxs-lookup"><span data-stu-id="c70d8-142">In the following example, the base class of `Point3D` is `Point`.</span></span> <span data-ttu-id="c70d8-143">在第一個範例中，的基類 `Point` 為 `object` ：</span><span class="sxs-lookup"><span data-stu-id="c70d8-143">From the first example, the base class of `Point` is `object`:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="Create3DPoint":::

<span data-ttu-id="c70d8-144">類別會繼承其基底類別的成員。</span><span class="sxs-lookup"><span data-stu-id="c70d8-144">A class inherits the members of its base class.</span></span> <span data-ttu-id="c70d8-145">繼承表示類別會隱含地包含其基類的所有成員。</span><span class="sxs-lookup"><span data-stu-id="c70d8-145">Inheritance means that a class implicitly contains almost all members of its base class.</span></span> <span data-ttu-id="c70d8-146">類別不會繼承實例和靜態的函式，以及完成項。</span><span class="sxs-lookup"><span data-stu-id="c70d8-146">A class doesn't inherit the instance and static constructors, and the finalizer.</span></span> <span data-ttu-id="c70d8-147">衍生類別可以將新成員加入至它所繼承的成員，但無法移除繼承成員的定義。</span><span class="sxs-lookup"><span data-stu-id="c70d8-147">A derived class can add new members to those members it inherits, but it can't remove the definition of an inherited member.</span></span> <span data-ttu-id="c70d8-148">在上述範例中， `Point3D` 繼承的 `X` 和 `Y` 成員 `Point` ，而每個 `Point3D` 實例都包含三個屬性：、 `X` `Y` 和 `Z` 。</span><span class="sxs-lookup"><span data-stu-id="c70d8-148">In the previous example, `Point3D` inherits the `X` and `Y` members from `Point`, and every `Point3D` instance contains three properties, `X`, `Y`, and `Z`.</span></span>

<span data-ttu-id="c70d8-149">在類別型別到其任何基底類別型別之間都存在著隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="c70d8-149">An implicit conversion exists from a class type to any of its base class types.</span></span> <span data-ttu-id="c70d8-150">類別型別的變數可以參考該類別的實例，或任何衍生類別的實例。</span><span class="sxs-lookup"><span data-stu-id="c70d8-150">A variable of a class type can reference an instance of that class or an instance of any derived class.</span></span> <span data-ttu-id="c70d8-151">例如，以先前的類別宣告為例，`Point` 型別的變數可以參考 `Point` 或 `Point3D`：</span><span class="sxs-lookup"><span data-stu-id="c70d8-151">For example, given the previous class declarations, a variable of type `Point` can reference either a `Point` or a `Point3D`:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="ImplicitCastToBase":::

## <a name="structs"></a><span data-ttu-id="c70d8-152">結構</span><span class="sxs-lookup"><span data-stu-id="c70d8-152">Structs</span></span>

<span data-ttu-id="c70d8-153">類別會定義支援繼承和多型的類型。</span><span class="sxs-lookup"><span data-stu-id="c70d8-153">Classes define types that support inheritance and polymorphism.</span></span> <span data-ttu-id="c70d8-154">它們可讓您根據衍生類別的階層來建立複雜的行為。</span><span class="sxs-lookup"><span data-stu-id="c70d8-154">They enable you to create sophisticated behaviors based on hierarchies of derived classes.</span></span> <span data-ttu-id="c70d8-155">相較之下， [ \* **結構** _](../language-reference/builtin-types/struct.md)類型是較簡單的類型，其主要用途是儲存資料值。</span><span class="sxs-lookup"><span data-stu-id="c70d8-155">By contrast, [\***struct** _](../language-reference/builtin-types/struct.md) types are simpler types whose primary purpose is to store data values.</span></span> <span data-ttu-id="c70d8-156">結構無法宣告基底類型;它們隱含地衍生自 <xref:System.ValueType?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="c70d8-156">Structs can't declare a base type; they implicitly derive from <xref:System.ValueType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c70d8-157">您無法 `struct` 從類型衍生其他類型 `struct` 。</span><span class="sxs-lookup"><span data-stu-id="c70d8-157">You can't derive other `struct` types from a `struct` type.</span></span> <span data-ttu-id="c70d8-158">它們是隱含密封的。</span><span class="sxs-lookup"><span data-stu-id="c70d8-158">They're implicitly sealed.</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="PointStruct":::

## <a name="interfaces"></a><span data-ttu-id="c70d8-159">介面</span><span class="sxs-lookup"><span data-stu-id="c70d8-159">Interfaces</span></span>

<span data-ttu-id="c70d8-160">[_\*_介面_\*_](../programming-guide/interfaces/index.md)會定義可由類別和結構執行的合約。</span><span class="sxs-lookup"><span data-stu-id="c70d8-160">An [_*_interface_*_](../programming-guide/interfaces/index.md) defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="c70d8-161">介面可以包含方法、屬性、事件和索引子。</span><span class="sxs-lookup"><span data-stu-id="c70d8-161">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="c70d8-162">介面通常不會提供它所定義之成員的實作為，它只會指定必須由執行介面之類別或結構提供的成員。</span><span class="sxs-lookup"><span data-stu-id="c70d8-162">An interface typically doesn't provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="c70d8-163">介面可能採用 _\*_多重繼承_\*_。</span><span class="sxs-lookup"><span data-stu-id="c70d8-163">Interfaces may employ _*_multiple inheritance_*_.</span></span> <span data-ttu-id="c70d8-164">在下列範例中，介面 `IComboBox` 同時繼承自 `ITextBox` 和 `IListBox`。</span><span class="sxs-lookup"><span data-stu-id="c70d8-164">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="FirstInterfaces":::

<span data-ttu-id="c70d8-165">類別和結構可以實作多個介面。</span><span class="sxs-lookup"><span data-stu-id="c70d8-165">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="c70d8-166">在下列範例中，類別 `EditBox` 可以實作 `IControl` 與 `IDataBound` 兩者。</span><span class="sxs-lookup"><span data-stu-id="c70d8-166">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="ImplementInterfaces":::

<span data-ttu-id="c70d8-167">當類別或結構實作特定介面時，可以將該類別或結構的執行個體隱含地轉換為該介面型別。</span><span class="sxs-lookup"><span data-stu-id="c70d8-167">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="c70d8-168">例如：</span><span class="sxs-lookup"><span data-stu-id="c70d8-168">For example</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="UseInterfaces":::

## <a name="enums"></a><span data-ttu-id="c70d8-169">列舉</span><span class="sxs-lookup"><span data-stu-id="c70d8-169">Enums</span></span>

<span data-ttu-id="c70d8-170">[_\*_列舉_\*_](../language-reference/builtin-types/enum.md)型別會定義一組常數值。</span><span class="sxs-lookup"><span data-stu-id="c70d8-170">An [_*_Enum_*_](../language-reference/builtin-types/enum.md) type defines a set of constant values.</span></span> <span data-ttu-id="c70d8-171">以下宣告 `enum` 定義不同根蔬菜的常數：</span><span class="sxs-lookup"><span data-stu-id="c70d8-171">The following `enum` declares constants that define different root vegetables:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="EnumDeclaration":::

<span data-ttu-id="c70d8-172">您也可以定義 `enum` 要用來組合為旗標的。</span><span class="sxs-lookup"><span data-stu-id="c70d8-172">You can also define an `enum` to be used in combination as flags.</span></span> <span data-ttu-id="c70d8-173">下列宣告會宣告四個季節的一組旗標。</span><span class="sxs-lookup"><span data-stu-id="c70d8-173">The following declaration declares a set of flags for the four seasons.</span></span> <span data-ttu-id="c70d8-174">可能會套用季節的任何組合，包括 `All` 包含所有季節的值：</span><span class="sxs-lookup"><span data-stu-id="c70d8-174">Any combination of the seasons may be applied, including an `All` value that includes all seasons:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="FlagsEnumDeclaration":::

<span data-ttu-id="c70d8-175">下列範例會顯示上述兩個列舉的宣告：</span><span class="sxs-lookup"><span data-stu-id="c70d8-175">The following example shows declarations of both the preceding enums:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="UsingEnums":::

## <a name="nullable-types"></a><span data-ttu-id="c70d8-176">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="c70d8-176">Nullable types</span></span>

<span data-ttu-id="c70d8-177">任何類型的變數都可以宣告為 _\*_不可為 null_*_ 或 _*_可為 null_\*_。</span><span class="sxs-lookup"><span data-stu-id="c70d8-177">Variables of any type may be declared as _*_non-nullable_*_ or _*_nullable_*_.</span></span> <span data-ttu-id="c70d8-178">可為 null 的變數可以保留額外 `null` 值，表示沒有任何值。</span><span class="sxs-lookup"><span data-stu-id="c70d8-178">A nullable variable can hold an additional `null` value, indicating no value.</span></span> <span data-ttu-id="c70d8-179">可為 null 的實值型別 (結構或列舉) 由表示 <xref:System.Nullable%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="c70d8-179">Nullable Value types (structs or enums) are represented by <xref:System.Nullable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c70d8-180">不可為 null 且可為 Null 的參考型別都是以基礎參考型別表示。</span><span class="sxs-lookup"><span data-stu-id="c70d8-180">Non-nullable and Nullable Reference types are both represented by the underlying reference type.</span></span> <span data-ttu-id="c70d8-181">差別是由編譯器所讀取的中繼資料和某些程式庫所表示。</span><span class="sxs-lookup"><span data-stu-id="c70d8-181">The distinction is represented by metadata read by the compiler and some libraries.</span></span> <span data-ttu-id="c70d8-182">如果可為 null 參考進行取值，而未先檢查其值，則編譯器會提供警告 `null` 。</span><span class="sxs-lookup"><span data-stu-id="c70d8-182">The compiler provides warnings when nullable references are dereferenced without first checking their value against `null`.</span></span> <span data-ttu-id="c70d8-183">若為不可為 null 的參考指派了可能的值，編譯器也會提供警告 `null` 。</span><span class="sxs-lookup"><span data-stu-id="c70d8-183">The compiler also provides warnings when non-nullable references are assigned a value that may be `null`.</span></span> <span data-ttu-id="c70d8-184">下列範例會宣告 _\*_可為 null 的 int_\*_，將它初始化為 `null` 。</span><span class="sxs-lookup"><span data-stu-id="c70d8-184">The following example declares a _*_nullable int_*_, initializing it to `null`.</span></span> <span data-ttu-id="c70d8-185">然後，它會將值設定為 `5` 。</span><span class="sxs-lookup"><span data-stu-id="c70d8-185">Then, it sets the value to `5`.</span></span> <span data-ttu-id="c70d8-186">它示範的概念與 _\*_可為 null 的字串_\*_ 相同。</span><span class="sxs-lookup"><span data-stu-id="c70d8-186">It demonstrates the same concept with a _*_nullable string_*_.</span></span> <span data-ttu-id="c70d8-187">如需詳細資訊，請參閱[可為 null](../language-reference/builtin-types/nullable-value-types.md)的實值型別及[可為 null 的參考](../nullable-references.md)</span><span class="sxs-lookup"><span data-stu-id="c70d8-187">For more information, see [nullable value types](../language-reference/builtin-types/nullable-value-types.md) and [nullable reference types](../nullable-references.md).</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DeclareNullable":::

## <a name="tuples"></a><span data-ttu-id="c70d8-188">Tuple</span><span class="sxs-lookup"><span data-stu-id="c70d8-188">Tuples</span></span>

<span data-ttu-id="c70d8-189">C # 支援 [_ *_元_* \*](../language-reference/builtin-types/value-tuples.md)組，可提供簡潔的語法來群組輕量資料結構中的多個資料元素。</span><span class="sxs-lookup"><span data-stu-id="c70d8-189">C# supports [_ *_tuples_*\*](../language-reference/builtin-types/value-tuples.md), which provides concise syntax to group multiple data elements in a lightweight data structure.</span></span> <span data-ttu-id="c70d8-190">您可以藉由宣告和之間成員的類型和名稱來具現化元組 `(` `)` ，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="c70d8-190">You instantiate a tuple by declaring the types and names of the members between `(` and `)`, as shown in the following example:</span></span>

:::code language="csharp" source="./snippets/shared/Types.cs" ID="DeclareTuples":::

<span data-ttu-id="c70d8-191">元組為具有多個成員的資料結構提供替代方式，而不使用下一篇文章中所述的建立區塊。</span><span class="sxs-lookup"><span data-stu-id="c70d8-191">Tuples provide an alternative for data structure with multiple members, without using the building blocks described in the next article.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c70d8-192">[上一個](index.md) 
>[下一步](program-building-blocks.md)</span><span class="sxs-lookup"><span data-stu-id="c70d8-192">[Previous](index.md)
[Next](program-building-blocks.md)</span></span>
