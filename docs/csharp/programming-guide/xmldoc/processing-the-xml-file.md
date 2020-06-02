---
title: '處理 XML 檔案-c # 程式設計手冊'
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: 1e3d96f9398f2c08ed715111f01987e2d1948439
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287255"
---
# <a name="process-the-xml-file-c-programming-guide"></a><span data-ttu-id="6235c-102">處理 XML 檔案（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="6235c-102">Process the XML file (C# programming guide)</span></span>

<span data-ttu-id="6235c-103">編譯器會針對您的程式碼中標記為產生檔的每個結構，產生一個識別碼字串。</span><span class="sxs-lookup"><span data-stu-id="6235c-103">The compiler generates an ID string for each construct in your code that's tagged to generate documentation.</span></span> <span data-ttu-id="6235c-104">（如需如何標記程式碼的相關資訊，請參閱[建議的檔註解標記](./recommended-tags-for-documentation-comments.md)）。識別碼字串可唯一識別結構。</span><span class="sxs-lookup"><span data-stu-id="6235c-104">(For information about how to tag your code, see [Recommended Tags for Documentation Comments](./recommended-tags-for-documentation-comments.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="6235c-105">處理 XML 檔案的程式可以使用識別碼字串，來識別檔適用的對應 .NET 中繼資料或反映專案。</span><span class="sxs-lookup"><span data-stu-id="6235c-105">Programs that process the XML file can use the ID string to identify the corresponding .NET metadata or reflection item that the documentation applies to.</span></span>

## <a name="id-strings"></a><span data-ttu-id="6235c-106">識別碼字串</span><span class="sxs-lookup"><span data-stu-id="6235c-106">ID strings</span></span>

<span data-ttu-id="6235c-107">XML 檔案不是程式碼的階層式標記法。</span><span class="sxs-lookup"><span data-stu-id="6235c-107">The XML file is not a hierarchical representation of your code.</span></span> <span data-ttu-id="6235c-108">它是一個一般清單，其中包含為每個元素產生的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6235c-108">It's a flat list that has a generated ID for each element.</span></span>

<span data-ttu-id="6235c-109">編譯器在產生識別碼字串時會遵守下列規則：</span><span class="sxs-lookup"><span data-stu-id="6235c-109">The compiler observes the following rules when it generates the ID strings:</span></span>

- <span data-ttu-id="6235c-110">字串中沒有空白字元。</span><span class="sxs-lookup"><span data-stu-id="6235c-110">No white space is in the string.</span></span>

- <span data-ttu-id="6235c-111">字串的第一個部分會使用單一字元並在後面加上冒號來識別成員的種類。</span><span class="sxs-lookup"><span data-stu-id="6235c-111">The first part of the string identifies the kind of member using a single character followed by a colon.</span></span> <span data-ttu-id="6235c-112">使用的成員類型如下：</span><span class="sxs-lookup"><span data-stu-id="6235c-112">The following member types are used:</span></span>

    |<span data-ttu-id="6235c-113">字元</span><span class="sxs-lookup"><span data-stu-id="6235c-113">Character</span></span>|<span data-ttu-id="6235c-114">成員類型</span><span class="sxs-lookup"><span data-stu-id="6235c-114">Member type</span></span>|<span data-ttu-id="6235c-115">備忘稿</span><span class="sxs-lookup"><span data-stu-id="6235c-115">Notes</span></span>|
    |---------------|-----------------|-|
    |<span data-ttu-id="6235c-116">N</span><span class="sxs-lookup"><span data-stu-id="6235c-116">N</span></span>|<span data-ttu-id="6235c-117">namespace</span><span class="sxs-lookup"><span data-stu-id="6235c-117">namespace</span></span>|<span data-ttu-id="6235c-118">您無法將文件註解新增至命名空間，但可讓 cref 參考它們 (如果支援)。</span><span class="sxs-lookup"><span data-stu-id="6235c-118">You cannot add documentation comments to a namespace, but you can make cref references to them, where supported.</span></span>|
    |<span data-ttu-id="6235c-119">T</span><span class="sxs-lookup"><span data-stu-id="6235c-119">T</span></span>|<span data-ttu-id="6235c-120">類型</span><span class="sxs-lookup"><span data-stu-id="6235c-120">type</span></span>|<span data-ttu-id="6235c-121">型別可以是類別、介面、結構、列舉或委派。</span><span class="sxs-lookup"><span data-stu-id="6235c-121">A type can be a class, interface, struct, enum, or delegate.</span></span>|
    |<span data-ttu-id="6235c-122">F</span><span class="sxs-lookup"><span data-stu-id="6235c-122">F</span></span>|<span data-ttu-id="6235c-123">field</span><span class="sxs-lookup"><span data-stu-id="6235c-123">field</span></span>|
    |<span data-ttu-id="6235c-124">P</span><span class="sxs-lookup"><span data-stu-id="6235c-124">P</span></span>|<span data-ttu-id="6235c-125">屬性</span><span class="sxs-lookup"><span data-stu-id="6235c-125">property</span></span>|<span data-ttu-id="6235c-126">包含索引子或其他索引的屬性。</span><span class="sxs-lookup"><span data-stu-id="6235c-126">Includes indexers or other indexed properties.</span></span>|
    |<span data-ttu-id="6235c-127">M</span><span class="sxs-lookup"><span data-stu-id="6235c-127">M</span></span>|<span data-ttu-id="6235c-128">method</span><span class="sxs-lookup"><span data-stu-id="6235c-128">method</span></span>|<span data-ttu-id="6235c-129">包含特殊方法，例如，構造函式和運算子。</span><span class="sxs-lookup"><span data-stu-id="6235c-129">Includes special methods, such as constructors and operators.</span></span>|
    |<span data-ttu-id="6235c-130">E</span><span class="sxs-lookup"><span data-stu-id="6235c-130">E</span></span>|<span data-ttu-id="6235c-131">event</span><span class="sxs-lookup"><span data-stu-id="6235c-131">event</span></span>|
    |<span data-ttu-id="6235c-132">!</span><span class="sxs-lookup"><span data-stu-id="6235c-132">!</span></span>|<span data-ttu-id="6235c-133">錯誤字串</span><span class="sxs-lookup"><span data-stu-id="6235c-133">error string</span></span>|<span data-ttu-id="6235c-134">字串的其餘部分提供與錯誤相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="6235c-134">The rest of the string provides information about the error.</span></span> <span data-ttu-id="6235c-135">C# 編譯器會針對無法解析的連結產生錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="6235c-135">The C# compiler generates error information for links that cannot be resolved.</span></span>|

- <span data-ttu-id="6235c-136">字串的第二個部分是項目的完整名稱 (從命名空間的根開始)。</span><span class="sxs-lookup"><span data-stu-id="6235c-136">The second part of the string is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="6235c-137">項目名稱、其封入類型及命名空間會以句號來分隔。</span><span class="sxs-lookup"><span data-stu-id="6235c-137">The name of the item, its enclosing type(s), and namespace are separated by periods.</span></span> <span data-ttu-id="6235c-138">如果項目名稱本身包含句點，則會以雜湊符號 ('#') 來取代它們。</span><span class="sxs-lookup"><span data-stu-id="6235c-138">If the name of the item itself has periods, they are replaced by the hash-sign ('#').</span></span> <span data-ttu-id="6235c-139">假設沒有任何專案直接在其名稱中包含雜湊符號。</span><span class="sxs-lookup"><span data-stu-id="6235c-139">It's assumed that no item has a hash-sign directly in its name.</span></span> <span data-ttu-id="6235c-140">例如，字串構造函式的完整名稱是 "System.string. #ctor"。</span><span class="sxs-lookup"><span data-stu-id="6235c-140">For example, the fully qualified name of the String constructor is "System.String.#ctor".</span></span>

- <span data-ttu-id="6235c-141">若為屬性和方法，則後面會接著以括弧括住的參數清單。</span><span class="sxs-lookup"><span data-stu-id="6235c-141">For properties and methods, the parameter list enclosed in parentheses follows.</span></span> <span data-ttu-id="6235c-142">如果沒有參數，則不會有括弧。</span><span class="sxs-lookup"><span data-stu-id="6235c-142">If there are no parameters, no parentheses are present.</span></span> <span data-ttu-id="6235c-143">參數會以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="6235c-143">The parameters are separated by commas.</span></span> <span data-ttu-id="6235c-144">每個參數的編碼會直接遵循其在 .NET 簽章中的編碼方式：</span><span class="sxs-lookup"><span data-stu-id="6235c-144">The encoding of each parameter follows directly how it's encoded in a .NET signature:</span></span>

  - <span data-ttu-id="6235c-145">基底類型。</span><span class="sxs-lookup"><span data-stu-id="6235c-145">Base types.</span></span> <span data-ttu-id="6235c-146">一般類型 (ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE) 會表示為類型的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="6235c-146">Regular types (ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE) are represented as the fully qualified name of the type.</span></span>

  - <span data-ttu-id="6235c-147">內建類型（例如，ELEMENT_TYPE_I4、ELEMENT_TYPE_OBJECT、ELEMENT_TYPE_STRING、ELEMENT_TYPE_TYPEDBYREF 和 ELEMENT_TYPE_VOID）會表示為對應完整類型的完整名稱。</span><span class="sxs-lookup"><span data-stu-id="6235c-147">Intrinsic types (for example, ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF, and ELEMENT_TYPE_VOID) are represented as the fully qualified name of the corresponding full type.</span></span> <span data-ttu-id="6235c-148">例如，System.Int32 或 System.TypedReference。</span><span class="sxs-lookup"><span data-stu-id="6235c-148">For example, System.Int32 or System.TypedReference.</span></span>

  - <span data-ttu-id="6235c-149">ELEMENT_TYPE_PTR 會表示為 '\*'，緊接在已修改的類型之後。</span><span class="sxs-lookup"><span data-stu-id="6235c-149">ELEMENT_TYPE_PTR is represented as a '\*' following the modified type.</span></span>

  - <span data-ttu-id="6235c-150">ELEMENT_TYPE_BYREF 會表示為 '\@'，緊接在已修改的類型之後。</span><span class="sxs-lookup"><span data-stu-id="6235c-150">ELEMENT_TYPE_BYREF is represented as a '\@' following the modified type.</span></span>

  - <span data-ttu-id="6235c-151">ELEMENT_TYPE_PINNED 會表示為 '^'，緊接在已修改的類型之後。</span><span class="sxs-lookup"><span data-stu-id="6235c-151">ELEMENT_TYPE_PINNED is represented as a '^' following the modified type.</span></span> <span data-ttu-id="6235c-152">C# 編譯器永遠都不會產生這個。</span><span class="sxs-lookup"><span data-stu-id="6235c-152">The C# compiler never generates this.</span></span>

  - <span data-ttu-id="6235c-153">ELEMENT_TYPE_CMOD_REQ 會表示為 '&#124;' 和修飾詞類別的完整名稱，緊接在已修改的類型之後。</span><span class="sxs-lookup"><span data-stu-id="6235c-153">ELEMENT_TYPE_CMOD_REQ is represented as a '&#124;' and the fully qualified name of the modifier class, following the modified type.</span></span> <span data-ttu-id="6235c-154">C# 編譯器永遠都不會產生這個。</span><span class="sxs-lookup"><span data-stu-id="6235c-154">The C# compiler never generates this.</span></span>

  - <span data-ttu-id="6235c-155">ELEMENT_TYPE_CMOD_OPT 會表示為 '!' 和修飾詞類別的完整名稱，緊接在已修改的類型之後。</span><span class="sxs-lookup"><span data-stu-id="6235c-155">ELEMENT_TYPE_CMOD_OPT is represented as a '!' and the fully qualified name of the modifier class, following the modified type.</span></span>

  - <span data-ttu-id="6235c-156">ELEMENT_TYPE_SZARRAY 會表示為 "[]"，緊接在陣列的元素類型之後。</span><span class="sxs-lookup"><span data-stu-id="6235c-156">ELEMENT_TYPE_SZARRAY is represented as "[]" following the element type of the array.</span></span>

  - <span data-ttu-id="6235c-157">ELEMENT_TYPE_GENERICARRAY 會表示為 "[?]"，緊接在陣列的元素類型之後。</span><span class="sxs-lookup"><span data-stu-id="6235c-157">ELEMENT_TYPE_GENERICARRAY is represented as "[?]" following the element type of the array.</span></span> <span data-ttu-id="6235c-158">C# 編譯器永遠都不會產生這個。</span><span class="sxs-lookup"><span data-stu-id="6235c-158">The C# compiler never generates this.</span></span>

  - <span data-ttu-id="6235c-159">ELEMENT_TYPE_ARRAY 會表示為 [*lowerbound*： `size` ，*lowerbound*： `size` ]，其中逗號數目是次序1，而每個維度的下限和大小（如果已知）則以十進位表示。</span><span class="sxs-lookup"><span data-stu-id="6235c-159">ELEMENT_TYPE_ARRAY is represented as [*lowerbound*:`size`,*lowerbound*:`size`] where the number of commas is the rank - 1, and the lower bounds and size of each dimension, if known, are represented in decimal.</span></span> <span data-ttu-id="6235c-160">如果未指定下限或大小，則會省略。</span><span class="sxs-lookup"><span data-stu-id="6235c-160">If a lower bound or size is not specified, it's omitted.</span></span> <span data-ttu-id="6235c-161">如果省略了特定維度的下限和大小，也會省略 ':'。</span><span class="sxs-lookup"><span data-stu-id="6235c-161">If the lower bound and size for a particular dimension are omitted, the ':' is omitted as well.</span></span> <span data-ttu-id="6235c-162">例如，下限為 1 且未指定大小的 2 維度陣列是 [1:,1:]。</span><span class="sxs-lookup"><span data-stu-id="6235c-162">For example, a 2-dimensional array with 1 as the lower bounds and unspecified sizes is [1:,1:].</span></span>

  - <span data-ttu-id="6235c-163">ELEMENT_TYPE_FNPTR 會表示為 "=FUNC:`type`(*signature*)"，其中 `type` 是傳回類型，而 *signature* 是方法的引數。</span><span class="sxs-lookup"><span data-stu-id="6235c-163">ELEMENT_TYPE_FNPTR is represented as "=FUNC:`type`(*signature*)", where `type` is the return type, and *signature* is the arguments of the method.</span></span> <span data-ttu-id="6235c-164">如果沒有任何引數，就會省略括弧。</span><span class="sxs-lookup"><span data-stu-id="6235c-164">If there are no arguments, the parentheses are omitted.</span></span> <span data-ttu-id="6235c-165">C# 編譯器永遠都不會產生這個。</span><span class="sxs-lookup"><span data-stu-id="6235c-165">The C# compiler never generates this.</span></span>

  <span data-ttu-id="6235c-166">下列簽章元件不會呈現，因為它們不會用來區別多載的方法：</span><span class="sxs-lookup"><span data-stu-id="6235c-166">The following signature components aren't represented because they aren't used to differentiate overloaded methods:</span></span>

  - <span data-ttu-id="6235c-167">呼叫慣例</span><span class="sxs-lookup"><span data-stu-id="6235c-167">calling convention</span></span>

  - <span data-ttu-id="6235c-168">傳回類型</span><span class="sxs-lookup"><span data-stu-id="6235c-168">return type</span></span>

  - <span data-ttu-id="6235c-169">ELEMENT_TYPE_SENTINEL</span><span class="sxs-lookup"><span data-stu-id="6235c-169">ELEMENT_TYPE_SENTINEL</span></span>

- <span data-ttu-id="6235c-170">僅針對轉換運算子（ `op_Implicit` 和 `op_Explicit` ），方法的傳回值會編碼為 ' ~ '，後面接著傳回型別。</span><span class="sxs-lookup"><span data-stu-id="6235c-170">For conversion operators only (`op_Implicit` and `op_Explicit`), the return value of the method is encoded as a '~' followed by the return type.</span></span>

- <span data-ttu-id="6235c-171">針對泛型類型，類型的名稱後面會接著反引號，然後是表示泛型類型參數數目的數字。</span><span class="sxs-lookup"><span data-stu-id="6235c-171">For generic types, the name of the type is followed by a backtick and then a number that indicates the number of generic type parameters.</span></span> <span data-ttu-id="6235c-172">例如：</span><span class="sxs-lookup"><span data-stu-id="6235c-172">For example:</span></span>

     <span data-ttu-id="6235c-173">``<member name="T:SampleClass`2">`` 是類型的標籤，定義為 `public class SampleClass<T, U>`。</span><span class="sxs-lookup"><span data-stu-id="6235c-173">``<member name="T:SampleClass`2">`` is the tag for a type that is defined as `public class SampleClass<T, U>`.</span></span>

     <span data-ttu-id="6235c-174">針對採用泛型型別做為參數的方法，會將泛型型別參數指定為前面加上倒引號的數位（例如 \` 0、 \` 1）。</span><span class="sxs-lookup"><span data-stu-id="6235c-174">For methods that take generic types as parameters, the generic type parameters are specified as numbers prefaced with backticks (for example \`0,\`1).</span></span> <span data-ttu-id="6235c-175">每個數位代表類型的泛型參數之以零為基底的陣列標記法。</span><span class="sxs-lookup"><span data-stu-id="6235c-175">Each number represents a zero-based array notation for the type's generic parameters.</span></span>

## <a name="examples"></a><span data-ttu-id="6235c-176">範例</span><span class="sxs-lookup"><span data-stu-id="6235c-176">Examples</span></span>

<span data-ttu-id="6235c-177">下列範例顯示如何產生類別及其成員的識別碼字串：</span><span class="sxs-lookup"><span data-stu-id="6235c-177">The following examples show how the ID strings for a class and its members are generated:</span></span>

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a><span data-ttu-id="6235c-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6235c-178">See also</span></span>

- [<span data-ttu-id="6235c-179">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="6235c-179">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="6235c-180">-doc （c # 編譯器選項）</span><span class="sxs-lookup"><span data-stu-id="6235c-180">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="6235c-181">XML 文件註解</span><span class="sxs-lookup"><span data-stu-id="6235c-181">XML documentation comments</span></span>](./index.md)
