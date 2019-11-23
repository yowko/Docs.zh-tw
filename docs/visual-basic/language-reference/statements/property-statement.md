---
title: Property 語句（Visual Basic）
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 2c3e417aad404171a43342dc92773615ec350ef5
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332740"
---
# <a name="property-statement"></a><span data-ttu-id="bed8d-102">Property Statement</span><span class="sxs-lookup"><span data-stu-id="bed8d-102">Property Statement</span></span>

<span data-ttu-id="bed8d-103">宣告屬性的名稱，以及用來儲存和取出屬性值的屬性程式。</span><span class="sxs-lookup"><span data-stu-id="bed8d-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>

## <a name="syntax"></a><span data-ttu-id="bed8d-104">語法</span><span class="sxs-lookup"><span data-stu-id="bed8d-104">Syntax</span></span>

```vb
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
    [ <attributelist> ] [ accessmodifier ] Get
        [ statements ]
    End Get
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )
        [ statements ]
    End Set
End Property
- or -
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
```

## <a name="parts"></a><span data-ttu-id="bed8d-105">組件</span><span class="sxs-lookup"><span data-stu-id="bed8d-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="bed8d-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bed8d-106">Optional.</span></span> <span data-ttu-id="bed8d-107">適用于這個屬性或 `Get` 或 `Set` 程式的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="bed8d-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="bed8d-108">請參閱[屬性清單](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="bed8d-108">See [Attribute List](attribute-list.md).</span></span>

- `Default`

  <span data-ttu-id="bed8d-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bed8d-109">Optional.</span></span> <span data-ttu-id="bed8d-110">指定此屬性為其定義所在之類別或結構的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="bed8d-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="bed8d-111">預設屬性必須接受參數，而且可以在不指定屬性名稱的情況下設定和抓取。</span><span class="sxs-lookup"><span data-stu-id="bed8d-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="bed8d-112">如果您將屬性宣告為 `Default`，就無法在屬性或其任何屬性程式上使用 `Private`。</span><span class="sxs-lookup"><span data-stu-id="bed8d-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>

- `accessmodifier`

  <span data-ttu-id="bed8d-113">在 `Property` 語句和最多一個 `Get` 和 `Set` 語句上都是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="bed8d-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="bed8d-114">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="bed8d-114">Can be one of the following:</span></span>

  - [<span data-ttu-id="bed8d-115">Public</span><span class="sxs-lookup"><span data-stu-id="bed8d-115">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="bed8d-116">Protected</span><span class="sxs-lookup"><span data-stu-id="bed8d-116">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="bed8d-117">Friend</span><span class="sxs-lookup"><span data-stu-id="bed8d-117">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="bed8d-118">Private</span><span class="sxs-lookup"><span data-stu-id="bed8d-118">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="bed8d-119">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="bed8d-119">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="bed8d-120">Private Protected</span><span class="sxs-lookup"><span data-stu-id="bed8d-120">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="bed8d-121">請參閱 [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="bed8d-121">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `propertymodifiers`

  <span data-ttu-id="bed8d-122">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bed8d-122">Optional.</span></span> <span data-ttu-id="bed8d-123">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="bed8d-123">Can be one of the following:</span></span>

  - [<span data-ttu-id="bed8d-124">多載</span><span class="sxs-lookup"><span data-stu-id="bed8d-124">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="bed8d-125">Overrides</span><span class="sxs-lookup"><span data-stu-id="bed8d-125">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="bed8d-126">Overrides</span><span class="sxs-lookup"><span data-stu-id="bed8d-126">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="bed8d-127">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="bed8d-127">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="bed8d-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="bed8d-128">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="bed8d-129">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bed8d-129">Optional.</span></span> <span data-ttu-id="bed8d-130">請參閱[共用](../modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="bed8d-130">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="bed8d-131">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bed8d-131">Optional.</span></span> <span data-ttu-id="bed8d-132">請參閱[Shadows](../modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="bed8d-132">See [Shadows](../modifiers/shadows.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="bed8d-133">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bed8d-133">Optional.</span></span> <span data-ttu-id="bed8d-134">請參閱[ReadOnly](../modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="bed8d-134">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WriteOnly`

  <span data-ttu-id="bed8d-135">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bed8d-135">Optional.</span></span> <span data-ttu-id="bed8d-136">請參閱[WriteOnly](../modifiers/writeonly.md)。</span><span class="sxs-lookup"><span data-stu-id="bed8d-136">See [WriteOnly](../modifiers/writeonly.md).</span></span>

- `Iterator`

  <span data-ttu-id="bed8d-137">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bed8d-137">Optional.</span></span> <span data-ttu-id="bed8d-138">請參閱[Iterator](../modifiers/iterator.md)。</span><span class="sxs-lookup"><span data-stu-id="bed8d-138">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="bed8d-139">必要。</span><span class="sxs-lookup"><span data-stu-id="bed8d-139">Required.</span></span> <span data-ttu-id="bed8d-140">屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="bed8d-140">Name of the property.</span></span> <span data-ttu-id="bed8d-141">請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="bed8d-141">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `parameterlist`

  <span data-ttu-id="bed8d-142">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bed8d-142">Optional.</span></span> <span data-ttu-id="bed8d-143">本機變數名稱的清單，代表這個屬性的參數，以及可能的 `Set` 程式的其他參數。</span><span class="sxs-lookup"><span data-stu-id="bed8d-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="bed8d-144">請參閱[參數清單](parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="bed8d-144">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="bed8d-145">如果 `Option Strict` `On`，則為必要。</span><span class="sxs-lookup"><span data-stu-id="bed8d-145">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="bed8d-146">這個屬性所傳回之值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bed8d-146">Data type of the value returned by this property.</span></span>

- `Implements`

  <span data-ttu-id="bed8d-147">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bed8d-147">Optional.</span></span> <span data-ttu-id="bed8d-148">指出此屬性會執行一或多個屬性，每個屬性都是由這個屬性的包含類別或結構所實的介面所定義。</span><span class="sxs-lookup"><span data-stu-id="bed8d-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="bed8d-149">請參閱[Implements 語句](implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="bed8d-149">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="bed8d-150">如果使用 `Implements`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="bed8d-150">Required if `Implements` is supplied.</span></span> <span data-ttu-id="bed8d-151">要實作為屬性的清單。</span><span class="sxs-lookup"><span data-stu-id="bed8d-151">List of properties being implemented.</span></span>

  `implementedproperty [ , implementedproperty ... ]`

  <span data-ttu-id="bed8d-152">每個 `implementedproperty` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="bed8d-152">Each `implementedproperty` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="bed8d-153">組件</span><span class="sxs-lookup"><span data-stu-id="bed8d-153">Part</span></span>|<span data-ttu-id="bed8d-154">描述</span><span class="sxs-lookup"><span data-stu-id="bed8d-154">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="bed8d-155">必要。</span><span class="sxs-lookup"><span data-stu-id="bed8d-155">Required.</span></span> <span data-ttu-id="bed8d-156">這個屬性的包含類別或結構所實作為介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="bed8d-156">Name of an interface implemented by this property's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="bed8d-157">必要。</span><span class="sxs-lookup"><span data-stu-id="bed8d-157">Required.</span></span> <span data-ttu-id="bed8d-158">屬性在 `interface`中定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="bed8d-158">Name by which the property is defined in `interface`.</span></span>|

- `Get`

  <span data-ttu-id="bed8d-159">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bed8d-159">Optional.</span></span> <span data-ttu-id="bed8d-160">如果屬性標示為 `ReadOnly`則為必要。</span><span class="sxs-lookup"><span data-stu-id="bed8d-160">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="bed8d-161">啟動用來傳回屬性值的 `Get` 屬性程式。</span><span class="sxs-lookup"><span data-stu-id="bed8d-161">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  <span data-ttu-id="bed8d-162">`Get` 語句不會與[自動執行的屬性](../../programming-guide/language-features/procedures/auto-implemented-properties.md)搭配使用。</span><span class="sxs-lookup"><span data-stu-id="bed8d-162">The `Get` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `statements`

  <span data-ttu-id="bed8d-163">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bed8d-163">Optional.</span></span> <span data-ttu-id="bed8d-164">要在 `Get` 或 `Set` 程式內執行的語句區塊。</span><span class="sxs-lookup"><span data-stu-id="bed8d-164">Block of statements to run within the `Get` or `Set` procedure.</span></span>

- `End Get`

  <span data-ttu-id="bed8d-165">結束 `Get` 屬性程式。</span><span class="sxs-lookup"><span data-stu-id="bed8d-165">Terminates the `Get` property procedure.</span></span>

- `Set`

  <span data-ttu-id="bed8d-166">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bed8d-166">Optional.</span></span> <span data-ttu-id="bed8d-167">如果屬性標示為 `WriteOnly`則為必要。</span><span class="sxs-lookup"><span data-stu-id="bed8d-167">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="bed8d-168">啟動用來儲存屬性值的 `Set` 屬性程式。</span><span class="sxs-lookup"><span data-stu-id="bed8d-168">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  <span data-ttu-id="bed8d-169">`Set` 語句不會與[自動執行的屬性](../../programming-guide/language-features/procedures/auto-implemented-properties.md)搭配使用。</span><span class="sxs-lookup"><span data-stu-id="bed8d-169">The `Set` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `End Set`

  <span data-ttu-id="bed8d-170">結束 `Set` 屬性程式。</span><span class="sxs-lookup"><span data-stu-id="bed8d-170">Terminates the `Set` property procedure.</span></span>

- `End Property`

  <span data-ttu-id="bed8d-171">終止這個屬性的定義。</span><span class="sxs-lookup"><span data-stu-id="bed8d-171">Terminates the definition of this property.</span></span>

## <a name="remarks"></a><span data-ttu-id="bed8d-172">備註</span><span class="sxs-lookup"><span data-stu-id="bed8d-172">Remarks</span></span>

<span data-ttu-id="bed8d-173">`Property` 語句會引進屬性的宣告。</span><span class="sxs-lookup"><span data-stu-id="bed8d-173">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="bed8d-174">屬性可以有 `Get` 程式（唯讀）、`Set` 程式（僅限寫入）或兩者（讀寫）。</span><span class="sxs-lookup"><span data-stu-id="bed8d-174">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="bed8d-175">使用自動執行的屬性時，您可以省略 `Get` 和 `Set` 程式。</span><span class="sxs-lookup"><span data-stu-id="bed8d-175">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="bed8d-176">如需詳細資訊，請參閱[自動實作的屬性](../../programming-guide/language-features/procedures/auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="bed8d-176">For more information, see [Auto-Implemented Properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

<span data-ttu-id="bed8d-177">您只能在類別層級使用 `Property`。</span><span class="sxs-lookup"><span data-stu-id="bed8d-177">You can use `Property` only at class level.</span></span> <span data-ttu-id="bed8d-178">這表示屬性的宣告*內容*必須是類別、結構、模組或介面，而且不能是原始程式檔、命名空間、程式或區塊。</span><span class="sxs-lookup"><span data-stu-id="bed8d-178">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="bed8d-179">如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="bed8d-179">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="bed8d-180">根據預設，屬性會使用公用存取。</span><span class="sxs-lookup"><span data-stu-id="bed8d-180">By default, properties use public access.</span></span> <span data-ttu-id="bed8d-181">您可以使用 `Property` 語句上的存取修飾詞來調整屬性的存取層級，也可以選擇性地將其中一個屬性程式調整為更嚴格的存取層級。</span><span class="sxs-lookup"><span data-stu-id="bed8d-181">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>

<span data-ttu-id="bed8d-182">Visual Basic 在屬性指派期間，將參數傳遞給 `Set` 程式。</span><span class="sxs-lookup"><span data-stu-id="bed8d-182">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="bed8d-183">如果您未提供 `Set`的參數，整合式開發環境（IDE）會使用名為 `value`的隱含參數。</span><span class="sxs-lookup"><span data-stu-id="bed8d-183">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="bed8d-184">這個參數會保留要指派給屬性的值。</span><span class="sxs-lookup"><span data-stu-id="bed8d-184">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="bed8d-185">您通常會將此值儲存在私用區域變數中，並在每次呼叫 `Get` 程式時傳回它。</span><span class="sxs-lookup"><span data-stu-id="bed8d-185">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>

## <a name="rules"></a><span data-ttu-id="bed8d-186">規則</span><span class="sxs-lookup"><span data-stu-id="bed8d-186">Rules</span></span>

- <span data-ttu-id="bed8d-187">**混合存取層級。**</span><span class="sxs-lookup"><span data-stu-id="bed8d-187">**Mixed Access Levels.**</span></span> <span data-ttu-id="bed8d-188">如果您要定義讀寫屬性，您可以選擇性地為 `Get` 或 `Set` 程式指定不同的存取層級，但不能同時為兩者。</span><span class="sxs-lookup"><span data-stu-id="bed8d-188">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="bed8d-189">如果您這樣做，程式存取層級必須比屬性的存取層級更嚴格。</span><span class="sxs-lookup"><span data-stu-id="bed8d-189">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="bed8d-190">例如，如果屬性是 `Friend`宣告的，您可以宣告 `Set` 程式 `Private`但不會 `Public`。</span><span class="sxs-lookup"><span data-stu-id="bed8d-190">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>

  <span data-ttu-id="bed8d-191">如果您要定義 `ReadOnly` 或 `WriteOnly` 屬性，單一屬性程式（分別為`Get` 或 `Set`）代表所有屬性。</span><span class="sxs-lookup"><span data-stu-id="bed8d-191">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="bed8d-192">您不能為這類程式宣告不同的存取層級，因為這會為屬性設定兩個存取層級。</span><span class="sxs-lookup"><span data-stu-id="bed8d-192">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>

- <span data-ttu-id="bed8d-193">**傳回類型。**</span><span class="sxs-lookup"><span data-stu-id="bed8d-193">**Return Type.**</span></span> <span data-ttu-id="bed8d-194">`Property` 語句可以宣告它所傳回之值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bed8d-194">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="bed8d-195">您可以指定任何資料類型，或是列舉、結構、類別或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="bed8d-195">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

  <span data-ttu-id="bed8d-196">如果您未指定 `returntype`，屬性會傳回 `Object`。</span><span class="sxs-lookup"><span data-stu-id="bed8d-196">If you do not specify `returntype`, the property returns `Object`.</span></span>

- <span data-ttu-id="bed8d-197">**實作.**</span><span class="sxs-lookup"><span data-stu-id="bed8d-197">**Implementation.**</span></span> <span data-ttu-id="bed8d-198">如果此屬性使用 `Implements` 關鍵字，則包含的類別或結構必須緊接在其 `Class` 或 `Structure` 語句後面的 `Implements` 語句。</span><span class="sxs-lookup"><span data-stu-id="bed8d-198">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="bed8d-199">`Implements` 語句必須包含 `implementslist`中指定的每個介面。</span><span class="sxs-lookup"><span data-stu-id="bed8d-199">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="bed8d-200">不過，介面用來定義 `Property` （在 `definedname`中）的名稱不一定要與這個屬性的名稱相同（在 `name`中）。</span><span class="sxs-lookup"><span data-stu-id="bed8d-200">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>

## <a name="behavior"></a><span data-ttu-id="bed8d-201">行為</span><span class="sxs-lookup"><span data-stu-id="bed8d-201">Behavior</span></span>

- <span data-ttu-id="bed8d-202">**從屬性程式傳回。**</span><span class="sxs-lookup"><span data-stu-id="bed8d-202">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="bed8d-203">當 `Get` 或 `Set` 程式回到呼叫程式碼時，執行會在叫用它的語句後面繼續進行語句。</span><span class="sxs-lookup"><span data-stu-id="bed8d-203">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>

  <span data-ttu-id="bed8d-204">`Exit Property` 和 `Return` 語句會導致立即離開屬性程式。</span><span class="sxs-lookup"><span data-stu-id="bed8d-204">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="bed8d-205">任何數目的 `Exit Property` 和 `Return` 語句都可以出現在程式中的任何位置，而且您可以混合 `Exit Property` 和 `Return` 語句。</span><span class="sxs-lookup"><span data-stu-id="bed8d-205">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>

- <span data-ttu-id="bed8d-206">**傳回值。**</span><span class="sxs-lookup"><span data-stu-id="bed8d-206">**Return Value.**</span></span> <span data-ttu-id="bed8d-207">若要從 `Get` 程式傳回值，您可以將值指派給屬性名稱，或將它包含在 `Return` 語句中。</span><span class="sxs-lookup"><span data-stu-id="bed8d-207">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="bed8d-208">下列範例會將傳回值指派給屬性名稱 `quoteForTheDay`，然後使用 `Exit Property` 語句傳回。</span><span class="sxs-lookup"><span data-stu-id="bed8d-208">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  <span data-ttu-id="bed8d-209">如果您使用 `Exit Property` 而不指派值給 `name`，`Get` 程式會傳回屬性之資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="bed8d-209">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>

  <span data-ttu-id="bed8d-210">同時 `Return` 語句會指派 `Get` 程式傳回值並結束程式。</span><span class="sxs-lookup"><span data-stu-id="bed8d-210">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="bed8d-211">下列範例會顯示這種情況。</span><span class="sxs-lookup"><span data-stu-id="bed8d-211">The following example shows this.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a><span data-ttu-id="bed8d-212">範例</span><span class="sxs-lookup"><span data-stu-id="bed8d-212">Example</span></span>

<span data-ttu-id="bed8d-213">下列範例會在類別中宣告屬性。</span><span class="sxs-lookup"><span data-stu-id="bed8d-213">The following example declares a property in a class.</span></span>

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="bed8d-214">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bed8d-214">See also</span></span>

- [<span data-ttu-id="bed8d-215">自動實作的屬性</span><span class="sxs-lookup"><span data-stu-id="bed8d-215">Auto-Implemented Properties</span></span>](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="bed8d-216">物件和類別</span><span class="sxs-lookup"><span data-stu-id="bed8d-216">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="bed8d-217">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="bed8d-217">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="bed8d-218">Set 陳述式</span><span class="sxs-lookup"><span data-stu-id="bed8d-218">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="bed8d-219">參數清單</span><span class="sxs-lookup"><span data-stu-id="bed8d-219">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="bed8d-220">預設值</span><span class="sxs-lookup"><span data-stu-id="bed8d-220">Default</span></span>](../modifiers/default.md)
