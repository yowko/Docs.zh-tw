---
title: 宣告項目名稱 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: 5b1f8ccc402f7f5928a33f434664b0f28d108e6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61828612"
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="c51d6-102">宣告項目名稱 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c51d6-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="c51d6-103">每個宣告的項目有一個名稱，也稱為*識別碼*，這是程式碼會使用來參考它。</span><span class="sxs-lookup"><span data-stu-id="c51d6-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="c51d6-104">規則</span><span class="sxs-lookup"><span data-stu-id="c51d6-104">Rules</span></span>  
 <span data-ttu-id="c51d6-105">在 Visual Basic 中的項目名稱必須遵守下列規則：</span><span class="sxs-lookup"><span data-stu-id="c51d6-105">An element name in Visual Basic must observe the following rules:</span></span>  
  
-   <span data-ttu-id="c51d6-106">它必須以字母字元或底線開頭 (`_`)。</span><span class="sxs-lookup"><span data-stu-id="c51d6-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="c51d6-107">它必須只包含字母字元、 十進位數字和底線。</span><span class="sxs-lookup"><span data-stu-id="c51d6-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
-   <span data-ttu-id="c51d6-108">如果它是以底線開頭，它必須包含至少一個字母字元或十進位數字。</span><span class="sxs-lookup"><span data-stu-id="c51d6-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
-   <span data-ttu-id="c51d6-109">它不能超過 1023年個字元。</span><span class="sxs-lookup"><span data-stu-id="c51d6-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="c51d6-110">長度超過 1023年個字元的限制也適用於整個字串的完整限定名稱，例如`outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`。</span><span class="sxs-lookup"><span data-stu-id="c51d6-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="c51d6-111">下列範例顯示一些有效的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="c51d6-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="c51d6-112">下列範例顯示一些無效的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="c51d6-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="c51d6-113">第一個包含只底線、 十進位數字，以開頭的第二個和第三個包含無效的字元 （$）。</span><span class="sxs-lookup"><span data-stu-id="c51d6-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  <span data-ttu-id="c51d6-114">項目名稱開頭為底線 (`_`) 不屬於[Language Independence and Language-independent Components](../../../../standard/language-independence-and-language-independent-components.md) （cls） 標準，所以符合 CLS 標準的程式碼無法使用定義這類名稱的元件。</span><span class="sxs-lookup"><span data-stu-id="c51d6-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="c51d6-115">不過，在項目名稱中的任何其他位置中的底線是符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="c51d6-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="c51d6-116">名稱長度指導方針</span><span class="sxs-lookup"><span data-stu-id="c51d6-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="c51d6-117">事實上，您的名稱應該越短越好時仍可清楚識別的項目。</span><span class="sxs-lookup"><span data-stu-id="c51d6-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="c51d6-118">這可改善程式碼的可讀性，並減少列長度和原始程式檔的大小。</span><span class="sxs-lookup"><span data-stu-id="c51d6-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="c51d6-119">相反地，您的名稱不應該簡短，它不會適當地描述項目所代表的意義和您的程式碼如何使用它。</span><span class="sxs-lookup"><span data-stu-id="c51d6-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="c51d6-120">這是很重要的程式碼的可讀性。</span><span class="sxs-lookup"><span data-stu-id="c51d6-120">This is important for the readability of your code.</span></span> <span data-ttu-id="c51d6-121">如果其他人嘗試了解它，或您自行查看它很長的時間之後您所撰寫,，適合的項目名稱可以節省花一些時間。</span><span class="sxs-lookup"><span data-stu-id="c51d6-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="c51d6-122">逸出的名稱</span><span class="sxs-lookup"><span data-stu-id="c51d6-122">Escaped Names</span></span>  
 <span data-ttu-id="c51d6-123">一般而言，項目名稱必須符合任何所保留的關鍵字 Visual Basic 中，這類`Case`或`Friend`。</span><span class="sxs-lookup"><span data-stu-id="c51d6-123">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="c51d6-124">不過，您可以定義*逸出名稱*，這加上括號 (`[ ]`)。</span><span class="sxs-lookup"><span data-stu-id="c51d6-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="c51d6-125">逸出的名稱可以比對任何 Visual Basic 關鍵字，因為在方括號移除任何模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="c51d6-125">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="c51d6-126">當您稍後在程式碼中參考名稱時，也可以使用方括號。</span><span class="sxs-lookup"><span data-stu-id="c51d6-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="c51d6-127">一般情況下，您應該使用逸出的名稱時，才：</span><span class="sxs-lookup"><span data-stu-id="c51d6-127">In general, you should use escaped names only when:</span></span>  
  
-   <span data-ttu-id="c51d6-128">移轉您的程式碼，從舊版的 Visual Basic，未保留關鍵字做為欄位名稱。或</span><span class="sxs-lookup"><span data-stu-id="c51d6-128">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
-   <span data-ttu-id="c51d6-129">您正在使用不會保留指定的關鍵字是另一種語言撰寫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c51d6-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="c51d6-130">否則，您應該考慮重新命名項目，如果其名稱與關鍵字相衝突。</span><span class="sxs-lookup"><span data-stu-id="c51d6-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="c51d6-131">整合式的開發環境 (IDE) 提供簡單的方法，若要這樣做。</span><span class="sxs-lookup"><span data-stu-id="c51d6-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="c51d6-132">如需詳細資訊，請參閱 <<c0> [ 重構](/visualstudio/vb-ide/refactoring-vb)。</span><span class="sxs-lookup"><span data-stu-id="c51d6-132">For more information, see [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="c51d6-133">在名稱中的區分大小寫</span><span class="sxs-lookup"><span data-stu-id="c51d6-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="c51d6-134">在 Visual Basic 中的項目名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c51d6-134">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="c51d6-135">這表示，當編譯器會比較兩個字母大小寫不同的名稱，它會將它們解譯成相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="c51d6-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="c51d6-136">例如，它會將 `ABC` 和 `abc` 視為相同的宣告元素。</span><span class="sxs-lookup"><span data-stu-id="c51d6-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="c51d6-137">不過，common language runtime (CLR) 會使用區分大小寫的繫結。</span><span class="sxs-lookup"><span data-stu-id="c51d6-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="c51d6-138">因此，當您產生一個組件或 DLL 並讓其他組件使用時，您的名稱將會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c51d6-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="c51d6-139">例如，如果您使用名為 `ABC`的元素來定義類別，而其他組件透過 Common Language Runtime 使用您的類別，則這些組件必須以 `ABC`來表示該元素。</span><span class="sxs-lookup"><span data-stu-id="c51d6-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="c51d6-140">如果您之後在重新編譯您的類別，而且變更的項目名稱，以`abc`，則使用您的類別的組件無法再存取該元素。</span><span class="sxs-lookup"><span data-stu-id="c51d6-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="c51d6-141">因此，當您發行組件的更新版本時，不應該變更任何公用元素的字母大小寫。</span><span class="sxs-lookup"><span data-stu-id="c51d6-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="c51d6-142">名稱和地區設定</span><span class="sxs-lookup"><span data-stu-id="c51d6-142">Names and Locales</span></span>  
 <span data-ttu-id="c51d6-143">比較名稱與地區設定無關。</span><span class="sxs-lookup"><span data-stu-id="c51d6-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="c51d6-144">如果兩個名稱符合在一個地區設定中，保證在所有地區設定中比對。</span><span class="sxs-lookup"><span data-stu-id="c51d6-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c51d6-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c51d6-145">See also</span></span>

- [<span data-ttu-id="c51d6-146">宣告項目</span><span class="sxs-lookup"><span data-stu-id="c51d6-146">Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [<span data-ttu-id="c51d6-147">宣告項目特性</span><span class="sxs-lookup"><span data-stu-id="c51d6-147">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="c51d6-148">對已宣告項目的參考</span><span class="sxs-lookup"><span data-stu-id="c51d6-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="c51d6-149">陳述式</span><span class="sxs-lookup"><span data-stu-id="c51d6-149">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
