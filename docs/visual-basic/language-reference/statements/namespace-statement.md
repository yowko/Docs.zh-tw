---
title: Namespace 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.Namespace
helpviewer_keywords:
- namespaces [Visual Basic], root
- Namespace statement [Visual Basic]
- namespaces [Visual Basic], nested
- declaring namespaces [Visual Basic], syntax
- namespaces [Visual Basic], declaring
- root namespaces
- declarations [Visual Basic], namespaces
ms.assetid: a31fbd95-9ace-4c3d-bbb1-51222a2272b2
ms.openlocfilehash: cef339a66458ee9657dc1706082c3c5328746dc6
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875220"
---
# <a name="namespace-statement"></a><span data-ttu-id="dcdf7-102">Namespace 陳述式</span><span class="sxs-lookup"><span data-stu-id="dcdf7-102">Namespace Statement</span></span>

<span data-ttu-id="dcdf7-103">宣告命名空間的名稱，並導致在該命名空間內編譯遵循宣告的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-103">Declares the name of a namespace and causes the source code that follows the declaration to be compiled within that namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcdf7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="dcdf7-104">Syntax</span></span>  
  
```vb  
Namespace [Global.] { name | name.name }  
    [ componenttypes ]  
End Namespace  
```  
  
## <a name="parts"></a><span data-ttu-id="dcdf7-105">組件</span><span class="sxs-lookup"><span data-stu-id="dcdf7-105">Parts</span></span>  

 <span data-ttu-id="dcdf7-106">全球</span><span class="sxs-lookup"><span data-stu-id="dcdf7-106">Global</span></span>  
 <span data-ttu-id="dcdf7-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-107">Optional.</span></span> <span data-ttu-id="dcdf7-108">可讓您從專案的根命名空間定義命名空間。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-108">Allows you to define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="dcdf7-109">請參閱 [Visual Basic 中的命名空間](../../programming-guide/program-structure/namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-109">See [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 `name`  
 <span data-ttu-id="dcdf7-110">必要。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-110">Required.</span></span> <span data-ttu-id="dcdf7-111">識別命名空間的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-111">A unique name that identifies the namespace.</span></span> <span data-ttu-id="dcdf7-112">必須是有效的 Visual Basic 識別碼。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-112">Must be a valid Visual Basic identifier.</span></span> <span data-ttu-id="dcdf7-113">如需詳細資訊，請參閱宣告的 [元素名稱](../../programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-113">For more information, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 `componenttypes`  
 <span data-ttu-id="dcdf7-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-114">Optional.</span></span> <span data-ttu-id="dcdf7-115">組成命名空間的元素。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-115">Elements that make up the namespace.</span></span> <span data-ttu-id="dcdf7-116">這些包括（但不限於）列舉、結構、介面、類別、模組、委派和其他命名空間。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-116">These include, but are not limited to, enumerations, structures, interfaces, classes, modules, delegates, and other namespaces.</span></span>  
  
 `End Namespace`  
 <span data-ttu-id="dcdf7-117">終止 `Namespace` 區塊。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-117">Terminates a `Namespace` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcdf7-118">備註</span><span class="sxs-lookup"><span data-stu-id="dcdf7-118">Remarks</span></span>  

 <span data-ttu-id="dcdf7-119">命名空間會當做組織系統來使用。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-119">Namespaces are used as an organizational system.</span></span> <span data-ttu-id="dcdf7-120">它們提供了一種方式來分類和呈現公開給其他程式和應用程式的程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-120">They provide a way to classify and present programming elements that are exposed to other programs and applications.</span></span> <span data-ttu-id="dcdf7-121">請注意，命名空間不是類別或結構的 *類型* ，因為您不能宣告程式設計專案具有命名空間的資料型別。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-121">Note that a namespace is not a *type* in the sense that a class or structure is—you cannot declare a programming element to have the data type of a namespace.</span></span>  
  
 <span data-ttu-id="dcdf7-122">在語句之後宣告的所有程式設計項目都 `Namespace` 屬於該命名空間。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-122">All programming elements declared after a `Namespace` statement belong to that namespace.</span></span> <span data-ttu-id="dcdf7-123">Visual Basic 繼續將專案編譯成最後宣告的命名空間，直到遇到 `End Namespace` 語句或其他 `Namespace` 語句為止。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-123">Visual Basic continues to compile elements into the last declared namespace until it encounters either an `End Namespace` statement or another `Namespace` statement.</span></span>  
  
 <span data-ttu-id="dcdf7-124">如果已定義命名空間，即使是在您的專案之外，您也可以在其中加入程式設計項目。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-124">If a namespace is already defined, even outside your project, you can add programming elements to it.</span></span> <span data-ttu-id="dcdf7-125">若要這樣做，您可以使用 `Namespace` 語句來指示 Visual Basic 將元素編譯到該命名空間中。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-125">To do this, you use a `Namespace` statement to direct Visual Basic to compile elements into that namespace.</span></span>  
  
 <span data-ttu-id="dcdf7-126">您只能在檔案 `Namespace` 或命名空間層級使用語句。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-126">You can use a `Namespace` statement only at the file or namespace level.</span></span> <span data-ttu-id="dcdf7-127">這表示命名空間的宣告 *內容* 必須是原始程式檔或另一個命名空間，而且不可以是類別、結構、模組、介面或程式。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-127">This means the *declaration context* for a namespace must be a source file or another namespace, and cannot be a class, structure, module, interface, or procedure.</span></span> <span data-ttu-id="dcdf7-128">如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-128">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="dcdf7-129">您可以在另一個命名空間中宣告。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-129">You can declare one namespace within another.</span></span> <span data-ttu-id="dcdf7-130">您可以宣告的嵌套層級沒有嚴格的限制，但請記住，當其他程式碼存取最內層命名空間中宣告的專案時，它必須使用包含所有嵌套階層中所有命名空間名稱的限定性字串。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-130">There is no strict limit to the levels of nesting you can declare, but remember that when other code accesses the elements declared in the innermost namespace, it must use a qualification string that contains all the namespace names in the nesting hierarchy.</span></span>  
  
## <a name="access-level"></a><span data-ttu-id="dcdf7-131">存取層級</span><span class="sxs-lookup"><span data-stu-id="dcdf7-131">Access Level</span></span>  

 <span data-ttu-id="dcdf7-132">將命名空間視為具有 `Public` 存取層級。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-132">Namespaces are treated as if they have a `Public` access level.</span></span> <span data-ttu-id="dcdf7-133">您可以從相同專案中任何位置的程式碼、參考專案的其他專案，以及從專案所建立的任何元件存取命名空間。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-133">A namespace can be accessed from code anywhere in the same project, from other projects that reference the project, and from any assembly built from the project.</span></span>  
  
 <span data-ttu-id="dcdf7-134">在命名空間層級宣告的程式設計專案（表示在命名空間中，但不在任何其他專案內）可以擁有 `Public` 或 `Friend` 存取。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-134">Programming elements declared at namespace level, meaning in a namespace but not inside any other element, can have `Public` or `Friend` access.</span></span> <span data-ttu-id="dcdf7-135">如果未指定，則預設會使用這類元素的存取層級 `Friend` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-135">If unspecified, the access level of such an element uses `Friend` by default.</span></span> <span data-ttu-id="dcdf7-136">您可以在命名空間層級宣告的元素包括類別、結構、模組、介面、列舉和委派。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-136">Elements you can declare at namespace level include classes, structures, modules, interfaces, enumerations, and delegates.</span></span> <span data-ttu-id="dcdf7-137">如需詳細資訊，請參閱[宣告內容和預設存取層級](declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-137">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
## <a name="root-namespace"></a><span data-ttu-id="dcdf7-138">根命名空間</span><span class="sxs-lookup"><span data-stu-id="dcdf7-138">Root Namespace</span></span>  

 <span data-ttu-id="dcdf7-139">專案中的所有命名空間名稱都是以 *根命名空間*為基礎。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-139">All namespace names in your project are based on a *root namespace*.</span></span> <span data-ttu-id="dcdf7-140">Visual Studio 會針對專案中的所有程式碼，將專案名稱指派為預設根命名空間。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-140">Visual Studio assigns your project name as the default root namespace for all code in your project.</span></span> <span data-ttu-id="dcdf7-141">例如，如果專案已命名為 `Payroll`，其程式設計項目會屬於命名空間 `Payroll`。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-141">For example, if your project is named `Payroll`, its programming elements belong to namespace `Payroll`.</span></span> <span data-ttu-id="dcdf7-142">如果您宣告 `Namespace funding` ，該命名空間的完整名稱就是 `Payroll.funding` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-142">If you declare `Namespace funding`, the full name of that namespace is `Payroll.funding`.</span></span>  
  
 <span data-ttu-id="dcdf7-143">如果您想要在語句中指定現有的命名空間（ `Namespace` 例如在泛型清單類別範例中），您可以將根命名空間設定為 null 值。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-143">If you want to specify an existing namespace in a `Namespace` statement, such as in the generic list class example, you can set your root namespace to a null value.</span></span> <span data-ttu-id="dcdf7-144">若要這樣做，請按一下 [**專案**] 功能表中的 [**專案屬性**]，然後清除 [**根命名空間**] 專案，讓方塊空白。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-144">To do this, click **Project Properties** from the **Project** menu and then clear the **Root namespace** entry so that the box is empty.</span></span> <span data-ttu-id="dcdf7-145">如果您未在泛型清單類別範例中執行這項作業，Visual Basic 編譯器會採用 `System.Collections.Generic` 專案內的新命名空間 `Payroll` ，其完整名稱為 `Payroll.System.Collections.Generic` 。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-145">If you did not do this in the generic list class example, the Visual Basic compiler would take `System.Collections.Generic` as a new namespace within project `Payroll`, with the full name of `Payroll.System.Collections.Generic`.</span></span>  
  
 <span data-ttu-id="dcdf7-146">或者，您也可以使用 `Global` 關鍵字來參考專案外所定義命名空間的元素。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-146">Alternatively, you can use the `Global` keyword to refer to elements of namespaces defined outside your project.</span></span> <span data-ttu-id="dcdf7-147">這麼做可讓您保留專案名稱做為根命名空間。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-147">Doing so lets you retain your project name as the root namespace.</span></span> <span data-ttu-id="dcdf7-148">這可減少不慎將程式設計專案與現有命名空間的程式合併在一起的機會。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-148">This reduces the chance of unintentionally merging your programming elements together with those of existing namespaces.</span></span> <span data-ttu-id="dcdf7-149">如需詳細資訊，請參閱 [Visual Basic 命名空間](../../programming-guide/program-structure/namespaces.md)中的「完整名稱的全域關鍵字」一節。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-149">For more information, see the "Global Keyword in Fully Qualified Names" section in [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="dcdf7-150">`Global`關鍵字也可以在 Namespace 語句中使用。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-150">The `Global` keyword can also be used in a Namespace statement.</span></span> <span data-ttu-id="dcdf7-151">這可讓您從專案的根命名空間定義一個命名空間。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-151">This lets you define a namespace out of the root namespace of your project.</span></span> <span data-ttu-id="dcdf7-152">如需詳細資訊，請參閱 [Visual Basic 的命名空間](../../programming-guide/program-structure/namespaces.md)中的「命名空間語句中的全域關鍵字」一節。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-152">For more information, see the "Global Keyword in Namespace Statements" section in [Namespaces in Visual Basic](../../programming-guide/program-structure/namespaces.md).</span></span>  
  
 <span data-ttu-id="dcdf7-153">**故障 排除。**</span><span class="sxs-lookup"><span data-stu-id="dcdf7-153">**Troubleshooting.**</span></span> <span data-ttu-id="dcdf7-154">根命名空間可能會導致非預期的命名空間名稱串連。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-154">The root namespace can lead to unexpected concatenations of namespace names.</span></span> <span data-ttu-id="dcdf7-155">如果您參考在專案之外定義的命名空間，Visual Basic 編譯器可以在根命名空間中將其 construe 為嵌套命名空間。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-155">If you make reference to namespaces defined outside your project, the Visual Basic compiler can construe them as nested namespaces in the root namespace.</span></span> <span data-ttu-id="dcdf7-156">在這種情況下，編譯器無法辨識外部命名空間中已定義的任何類型。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-156">In such a case, the compiler does not recognize any types that have been already defined in the external namespaces.</span></span> <span data-ttu-id="dcdf7-157">若要避免這種情況，請將您的根命名空間設定為 null 值（如「根命名空間」中所述），或使用 `Global` 關鍵字來存取外部命名空間的元素。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-157">To avoid this, either set your root namespace to a null value as described in "Root Namespace," or use the `Global` keyword to access elements of external namespaces.</span></span>  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="dcdf7-158">屬性和修飾詞</span><span class="sxs-lookup"><span data-stu-id="dcdf7-158">Attributes and Modifiers</span></span>  

 <span data-ttu-id="dcdf7-159">您無法將屬性套用至命名空間。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-159">You cannot apply attributes to a namespace.</span></span> <span data-ttu-id="dcdf7-160">屬性會將資訊提供給元件的中繼資料，這對來源分類器（例如命名空間）而言沒有意義。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-160">An attribute contributes information to the assembly's metadata, which is not meaningful for source classifiers such as namespaces.</span></span>  
  
 <span data-ttu-id="dcdf7-161">您無法將任何存取或程式修飾詞或任何其他修飾詞套用至命名空間。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-161">You cannot apply any access or procedure modifiers, or any other modifiers, to a namespace.</span></span> <span data-ttu-id="dcdf7-162">因為這不是型別，所以這些修飾詞沒有意義。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-162">Because it is not a type, these modifiers are not meaningful.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcdf7-163">範例</span><span class="sxs-lookup"><span data-stu-id="dcdf7-163">Example</span></span>  

 <span data-ttu-id="dcdf7-164">下列範例會宣告兩個命名空間，其中一個是嵌套在另一個。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-164">The following example declares two namespaces, one nested in the other.</span></span>  
  
 [!code-vb[VbVbalrStatements#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#43)]  
  
## <a name="example"></a><span data-ttu-id="dcdf7-165">範例</span><span class="sxs-lookup"><span data-stu-id="dcdf7-165">Example</span></span>  

 <span data-ttu-id="dcdf7-166">下列範例會在同一行宣告多個嵌套命名空間，而且它相當於先前的範例。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-166">The following example declares multiple nested namespaces on a single line, and it is equivalent to the previous example.</span></span>  
  
 [!code-vb[VbVbalrStatements#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="dcdf7-167">範例</span><span class="sxs-lookup"><span data-stu-id="dcdf7-167">Example</span></span>  

 <span data-ttu-id="dcdf7-168">下列範例會存取先前範例中所定義的類別。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-168">The following example accesses the class defined in the previous examples.</span></span>  
  
 [!code-vb[VbVbalrStatements#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#42)]  
  
## <a name="example"></a><span data-ttu-id="dcdf7-169">範例</span><span class="sxs-lookup"><span data-stu-id="dcdf7-169">Example</span></span>  

 <span data-ttu-id="dcdf7-170">下列範例會定義新泛型清單類別的基本架構，並將它新增至 <xref:System.Collections.Generic?displayProperty=nameWithType> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="dcdf7-170">The following example defines the skeleton of a new generic list class and adds it to the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Namespace System.Collections.Generic  
    Class specialSortedList(Of T)  
        Inherits List(Of T)  
        ' Insert code to define the special generic list class.  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="dcdf7-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcdf7-171">See also</span></span>

- [<span data-ttu-id="dcdf7-172">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="dcdf7-172">Imports Statement (.NET Namespace and Type)</span></span>](imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="dcdf7-173">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="dcdf7-173">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="dcdf7-174">Visual Basic 中的命名空間</span><span class="sxs-lookup"><span data-stu-id="dcdf7-174">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
