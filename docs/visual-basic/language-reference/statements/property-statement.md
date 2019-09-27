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
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332740"
---
# <a name="property-statement"></a><span data-ttu-id="c83d3-102">Property Statement</span><span class="sxs-lookup"><span data-stu-id="c83d3-102">Property Statement</span></span>

<span data-ttu-id="c83d3-103">宣告屬性的名稱，以及用來儲存和取出屬性值的屬性程式。</span><span class="sxs-lookup"><span data-stu-id="c83d3-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>

## <a name="syntax"></a><span data-ttu-id="c83d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="c83d3-104">Syntax</span></span>

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

## <a name="parts"></a><span data-ttu-id="c83d3-105">組件</span><span class="sxs-lookup"><span data-stu-id="c83d3-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="c83d3-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c83d3-106">Optional.</span></span> <span data-ttu-id="c83d3-107">套用至這個屬性或 `Get` 或 @no__t 1 程式的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="c83d3-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="c83d3-108">請參閱[屬性清單](attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="c83d3-108">See [Attribute List](attribute-list.md).</span></span>

- `Default`

  <span data-ttu-id="c83d3-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c83d3-109">Optional.</span></span> <span data-ttu-id="c83d3-110">指定此屬性為其定義所在之類別或結構的預設屬性。</span><span class="sxs-lookup"><span data-stu-id="c83d3-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="c83d3-111">預設屬性必須接受參數，而且可以在不指定屬性名稱的情況下設定和抓取。</span><span class="sxs-lookup"><span data-stu-id="c83d3-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="c83d3-112">如果您將屬性宣告為 `Default`，則不能在屬性或其任何屬性程式上使用 `Private`。</span><span class="sxs-lookup"><span data-stu-id="c83d3-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>

- `accessmodifier`

  <span data-ttu-id="c83d3-113">選擇性在 `Property` 語句和最多一個 `Get` 和 @no__t 2 語句上。</span><span class="sxs-lookup"><span data-stu-id="c83d3-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="c83d3-114">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="c83d3-114">Can be one of the following:</span></span>

  - [<span data-ttu-id="c83d3-115">Public</span><span class="sxs-lookup"><span data-stu-id="c83d3-115">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="c83d3-116">Protected</span><span class="sxs-lookup"><span data-stu-id="c83d3-116">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="c83d3-117">Friend</span><span class="sxs-lookup"><span data-stu-id="c83d3-117">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="c83d3-118">Private</span><span class="sxs-lookup"><span data-stu-id="c83d3-118">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="c83d3-119">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="c83d3-119">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="c83d3-120">Private Protected</span><span class="sxs-lookup"><span data-stu-id="c83d3-120">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="c83d3-121">請參閱 [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="c83d3-121">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `propertymodifiers`

  <span data-ttu-id="c83d3-122">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c83d3-122">Optional.</span></span> <span data-ttu-id="c83d3-123">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="c83d3-123">Can be one of the following:</span></span>

  - [<span data-ttu-id="c83d3-124">多載</span><span class="sxs-lookup"><span data-stu-id="c83d3-124">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="c83d3-125">Overrides</span><span class="sxs-lookup"><span data-stu-id="c83d3-125">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="c83d3-126">Overridable</span><span class="sxs-lookup"><span data-stu-id="c83d3-126">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="c83d3-127">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="c83d3-127">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="c83d3-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="c83d3-128">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="c83d3-129">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c83d3-129">Optional.</span></span> <span data-ttu-id="c83d3-130">請參閱[共用](../modifiers/shared.md)。</span><span class="sxs-lookup"><span data-stu-id="c83d3-130">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="c83d3-131">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c83d3-131">Optional.</span></span> <span data-ttu-id="c83d3-132">請參閱[Shadows](../modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="c83d3-132">See [Shadows](../modifiers/shadows.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="c83d3-133">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c83d3-133">Optional.</span></span> <span data-ttu-id="c83d3-134">請參閱[ReadOnly](../modifiers/readonly.md)。</span><span class="sxs-lookup"><span data-stu-id="c83d3-134">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WriteOnly`

  <span data-ttu-id="c83d3-135">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c83d3-135">Optional.</span></span> <span data-ttu-id="c83d3-136">請參閱[WriteOnly](../modifiers/writeonly.md)。</span><span class="sxs-lookup"><span data-stu-id="c83d3-136">See [WriteOnly](../modifiers/writeonly.md).</span></span>

- `Iterator`

  <span data-ttu-id="c83d3-137">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c83d3-137">Optional.</span></span> <span data-ttu-id="c83d3-138">請參閱[Iterator](../modifiers/iterator.md)。</span><span class="sxs-lookup"><span data-stu-id="c83d3-138">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="c83d3-139">必要項。</span><span class="sxs-lookup"><span data-stu-id="c83d3-139">Required.</span></span> <span data-ttu-id="c83d3-140">屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="c83d3-140">Name of the property.</span></span> <span data-ttu-id="c83d3-141">請參閱 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="c83d3-141">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `parameterlist`

  <span data-ttu-id="c83d3-142">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c83d3-142">Optional.</span></span> <span data-ttu-id="c83d3-143">本機變數名稱的清單，代表這個屬性的參數，以及可能的 `Set` 程式的其他參數。</span><span class="sxs-lookup"><span data-stu-id="c83d3-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="c83d3-144">請參閱[參數清單](parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="c83d3-144">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="c83d3-145">如果 `Option Strict` `On` 則為必要。</span><span class="sxs-lookup"><span data-stu-id="c83d3-145">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="c83d3-146">這個屬性所傳回之值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c83d3-146">Data type of the value returned by this property.</span></span>

- `Implements`

  <span data-ttu-id="c83d3-147">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c83d3-147">Optional.</span></span> <span data-ttu-id="c83d3-148">指出此屬性會執行一或多個屬性，每個屬性都是由這個屬性的包含類別或結構所實的介面所定義。</span><span class="sxs-lookup"><span data-stu-id="c83d3-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="c83d3-149">請參閱[Implements 語句](implements-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="c83d3-149">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="c83d3-150">如果使用 `Implements`，則為必要項。</span><span class="sxs-lookup"><span data-stu-id="c83d3-150">Required if `Implements` is supplied.</span></span> <span data-ttu-id="c83d3-151">要實作為屬性的清單。</span><span class="sxs-lookup"><span data-stu-id="c83d3-151">List of properties being implemented.</span></span>

  `implementedproperty [ , implementedproperty ... ]`

  <span data-ttu-id="c83d3-152">每個 `implementedproperty` 都具有下列語法和組件：</span><span class="sxs-lookup"><span data-stu-id="c83d3-152">Each `implementedproperty` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="c83d3-153">組件</span><span class="sxs-lookup"><span data-stu-id="c83d3-153">Part</span></span>|<span data-ttu-id="c83d3-154">描述</span><span class="sxs-lookup"><span data-stu-id="c83d3-154">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="c83d3-155">必要項。</span><span class="sxs-lookup"><span data-stu-id="c83d3-155">Required.</span></span> <span data-ttu-id="c83d3-156">這個屬性的包含類別或結構所實作為介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="c83d3-156">Name of an interface implemented by this property's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="c83d3-157">必要項。</span><span class="sxs-lookup"><span data-stu-id="c83d3-157">Required.</span></span> <span data-ttu-id="c83d3-158">用來定義屬性的名稱 `interface`。</span><span class="sxs-lookup"><span data-stu-id="c83d3-158">Name by which the property is defined in `interface`.</span></span>|

- `Get`

  <span data-ttu-id="c83d3-159">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c83d3-159">Optional.</span></span> <span data-ttu-id="c83d3-160">如果屬性標示為 `ReadOnly`，則為必要。</span><span class="sxs-lookup"><span data-stu-id="c83d3-160">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="c83d3-161">啟動用來傳回屬性值的 `Get` 屬性程式。</span><span class="sxs-lookup"><span data-stu-id="c83d3-161">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  <span data-ttu-id="c83d3-162">@No__t-0 語句不會與[自動執行的屬性](../../programming-guide/language-features/procedures/auto-implemented-properties.md)搭配使用。</span><span class="sxs-lookup"><span data-stu-id="c83d3-162">The `Get` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `statements`

  <span data-ttu-id="c83d3-163">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c83d3-163">Optional.</span></span> <span data-ttu-id="c83d3-164">要在 `Get` 或 `Set` 程式內執行的語句區塊。</span><span class="sxs-lookup"><span data-stu-id="c83d3-164">Block of statements to run within the `Get` or `Set` procedure.</span></span>

- `End Get`

  <span data-ttu-id="c83d3-165">終止 `Get` 屬性程式。</span><span class="sxs-lookup"><span data-stu-id="c83d3-165">Terminates the `Get` property procedure.</span></span>

- `Set`

  <span data-ttu-id="c83d3-166">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c83d3-166">Optional.</span></span> <span data-ttu-id="c83d3-167">如果屬性標示為 `WriteOnly`，則為必要。</span><span class="sxs-lookup"><span data-stu-id="c83d3-167">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="c83d3-168">啟動用來儲存屬性值的 `Set` 屬性程式。</span><span class="sxs-lookup"><span data-stu-id="c83d3-168">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  <span data-ttu-id="c83d3-169">@No__t-0 語句不會與[自動執行的屬性](../../programming-guide/language-features/procedures/auto-implemented-properties.md)搭配使用。</span><span class="sxs-lookup"><span data-stu-id="c83d3-169">The `Set` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `End Set`

  <span data-ttu-id="c83d3-170">終止 `Set` 屬性程式。</span><span class="sxs-lookup"><span data-stu-id="c83d3-170">Terminates the `Set` property procedure.</span></span>

- `End Property`

  <span data-ttu-id="c83d3-171">終止這個屬性的定義。</span><span class="sxs-lookup"><span data-stu-id="c83d3-171">Terminates the definition of this property.</span></span>

## <a name="remarks"></a><span data-ttu-id="c83d3-172">備註</span><span class="sxs-lookup"><span data-stu-id="c83d3-172">Remarks</span></span>

<span data-ttu-id="c83d3-173">@No__t-0 語句引進了屬性的宣告。</span><span class="sxs-lookup"><span data-stu-id="c83d3-173">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="c83d3-174">屬性可以有 `Get` 程式（唯讀）、@no__t 1 程式（僅限寫入）或兩者（讀寫）。</span><span class="sxs-lookup"><span data-stu-id="c83d3-174">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="c83d3-175">使用自動執行的屬性時，您可以省略 `Get` 和 @no__t 1 程式。</span><span class="sxs-lookup"><span data-stu-id="c83d3-175">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="c83d3-176">如需詳細資訊，請參閱[自動實作的屬性](../../programming-guide/language-features/procedures/auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="c83d3-176">For more information, see [Auto-Implemented Properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

<span data-ttu-id="c83d3-177">您只能在類別層級使用 `Property`。</span><span class="sxs-lookup"><span data-stu-id="c83d3-177">You can use `Property` only at class level.</span></span> <span data-ttu-id="c83d3-178">這表示屬性的宣告*內容*必須是類別、結構、模組或介面，而且不能是原始程式檔、命名空間、程式或區塊。</span><span class="sxs-lookup"><span data-stu-id="c83d3-178">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="c83d3-179">如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="c83d3-179">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="c83d3-180">根據預設，屬性會使用公用存取。</span><span class="sxs-lookup"><span data-stu-id="c83d3-180">By default, properties use public access.</span></span> <span data-ttu-id="c83d3-181">您可以使用 `Property` 語句上的存取修飾詞來調整屬性的存取層級，也可以選擇性地將其中一個屬性程式調整為更嚴格的存取層級。</span><span class="sxs-lookup"><span data-stu-id="c83d3-181">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>

<span data-ttu-id="c83d3-182">Visual Basic 在屬性指派期間，將參數傳遞給 @no__t 0 程式。</span><span class="sxs-lookup"><span data-stu-id="c83d3-182">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="c83d3-183">如果您未提供 `Set` 的參數，整合式開發環境（IDE）會使用名為 `value` 的隱含參數。</span><span class="sxs-lookup"><span data-stu-id="c83d3-183">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="c83d3-184">這個參數會保留要指派給屬性的值。</span><span class="sxs-lookup"><span data-stu-id="c83d3-184">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="c83d3-185">您通常會將此值儲存在私用區域變數中，並在每次呼叫 @no__t 0 程式時傳回它。</span><span class="sxs-lookup"><span data-stu-id="c83d3-185">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>

## <a name="rules"></a><span data-ttu-id="c83d3-186">規則</span><span class="sxs-lookup"><span data-stu-id="c83d3-186">Rules</span></span>

- <span data-ttu-id="c83d3-187">**混合存取層級。**</span><span class="sxs-lookup"><span data-stu-id="c83d3-187">**Mixed Access Levels.**</span></span> <span data-ttu-id="c83d3-188">如果您要定義讀寫屬性，您可以選擇性地為 `Get` 或 `Set` 程式指定不同的存取層級，但不能同時為兩者。</span><span class="sxs-lookup"><span data-stu-id="c83d3-188">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="c83d3-189">如果您這樣做，程式存取層級必須比屬性的存取層級更嚴格。</span><span class="sxs-lookup"><span data-stu-id="c83d3-189">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="c83d3-190">例如，如果將屬性宣告 `Friend`，您可以將 `Set` 程式宣告為 `Private`，但不會 `Public`。</span><span class="sxs-lookup"><span data-stu-id="c83d3-190">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>

  <span data-ttu-id="c83d3-191">如果您要定義 `ReadOnly` 或 @no__t 1 屬性，則單一屬性程式（分別為 `Get` 或 `Set`）代表所有屬性。</span><span class="sxs-lookup"><span data-stu-id="c83d3-191">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="c83d3-192">您不能為這類程式宣告不同的存取層級，因為這會為屬性設定兩個存取層級。</span><span class="sxs-lookup"><span data-stu-id="c83d3-192">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>

- <span data-ttu-id="c83d3-193">**傳回類型。**</span><span class="sxs-lookup"><span data-stu-id="c83d3-193">**Return Type.**</span></span> <span data-ttu-id="c83d3-194">@No__t-0 語句可以宣告它所傳回之值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="c83d3-194">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="c83d3-195">您可以指定任何資料類型，或是列舉、結構、類別或介面的名稱。</span><span class="sxs-lookup"><span data-stu-id="c83d3-195">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

  <span data-ttu-id="c83d3-196">如果您未指定 `returntype`，此屬性會傳回 `Object`。</span><span class="sxs-lookup"><span data-stu-id="c83d3-196">If you do not specify `returntype`, the property returns `Object`.</span></span>

- <span data-ttu-id="c83d3-197">**實作.**</span><span class="sxs-lookup"><span data-stu-id="c83d3-197">**Implementation.**</span></span> <span data-ttu-id="c83d3-198">如果此屬性使用 `Implements` 關鍵字，則包含的類別或結構必須緊接在其 `Class` 或 `Structure` 語句之後的 `Implements` 語句。</span><span class="sxs-lookup"><span data-stu-id="c83d3-198">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="c83d3-199">@No__t-0 語句必須包含 `implementslist` 中指定的每個介面。</span><span class="sxs-lookup"><span data-stu-id="c83d3-199">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="c83d3-200">不過，介面用來定義 `Property` （在 `definedname`）的名稱不一定要與這個屬性的名稱相同（在 `name`）。</span><span class="sxs-lookup"><span data-stu-id="c83d3-200">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>

## <a name="behavior"></a><span data-ttu-id="c83d3-201">行為</span><span class="sxs-lookup"><span data-stu-id="c83d3-201">Behavior</span></span>

- <span data-ttu-id="c83d3-202">**從屬性程式傳回。**</span><span class="sxs-lookup"><span data-stu-id="c83d3-202">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="c83d3-203">當 `Get` 或 @no__t 1 程式回到呼叫程式碼時，執行會在叫用它的語句後面繼續進行語句。</span><span class="sxs-lookup"><span data-stu-id="c83d3-203">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>

  <span data-ttu-id="c83d3-204">@No__t-0 和 @no__t 1 語句會導致立即離開屬性程式。</span><span class="sxs-lookup"><span data-stu-id="c83d3-204">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="c83d3-205">任何數目的 `Exit Property` 和 @no__t 1 語句都可以出現在程式中的任何位置，您可以混用 `Exit Property` 和 `Return` 語句。</span><span class="sxs-lookup"><span data-stu-id="c83d3-205">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>

- <span data-ttu-id="c83d3-206">**傳回值。**</span><span class="sxs-lookup"><span data-stu-id="c83d3-206">**Return Value.**</span></span> <span data-ttu-id="c83d3-207">若要從 `Get` 程式傳回值，您可以將值指派給屬性名稱，或將它包含在 @no__t 1 語句中。</span><span class="sxs-lookup"><span data-stu-id="c83d3-207">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="c83d3-208">下列範例會將傳回值指派給屬性名稱 `quoteForTheDay`，然後使用 `Exit Property` 語句傳回。</span><span class="sxs-lookup"><span data-stu-id="c83d3-208">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  <span data-ttu-id="c83d3-209">如果您使用 `Exit Property`，但未指派值給 `name`，則 @no__t 2 程式會傳回屬性之資料類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="c83d3-209">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>

  <span data-ttu-id="c83d3-210">同時 `Return` 語句會指派 `Get` 程式傳回值並結束程式。</span><span class="sxs-lookup"><span data-stu-id="c83d3-210">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="c83d3-211">下列範例會顯示這種情況。</span><span class="sxs-lookup"><span data-stu-id="c83d3-211">The following example shows this.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a><span data-ttu-id="c83d3-212">範例</span><span class="sxs-lookup"><span data-stu-id="c83d3-212">Example</span></span>

<span data-ttu-id="c83d3-213">下列範例會在類別中宣告屬性。</span><span class="sxs-lookup"><span data-stu-id="c83d3-213">The following example declares a property in a class.</span></span>

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="c83d3-214">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c83d3-214">See also</span></span>

- [<span data-ttu-id="c83d3-215">自動實作的屬性</span><span class="sxs-lookup"><span data-stu-id="c83d3-215">Auto-Implemented Properties</span></span>](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="c83d3-216">物件和類別</span><span class="sxs-lookup"><span data-stu-id="c83d3-216">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="c83d3-217">Get 陳述式</span><span class="sxs-lookup"><span data-stu-id="c83d3-217">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="c83d3-218">Set 陳述式</span><span class="sxs-lookup"><span data-stu-id="c83d3-218">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="c83d3-219">參數清單</span><span class="sxs-lookup"><span data-stu-id="c83d3-219">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="c83d3-220">Default</span><span class="sxs-lookup"><span data-stu-id="c83d3-220">Default</span></span>](../modifiers/default.md)
