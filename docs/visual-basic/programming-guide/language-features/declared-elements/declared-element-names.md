---
title: Declared Element Names
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
ms.openlocfilehash: 327a18644c1dc1d8dae59016b8e30600357d2ca9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086175"
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="092de-102">宣告項目名稱 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="092de-102">Declared Element Names (Visual Basic)</span></span>

<span data-ttu-id="092de-103">每個宣告的專案都有名稱，也稱為 *識別碼*，程式碼會使用它來參考它。</span><span class="sxs-lookup"><span data-stu-id="092de-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="092de-104">規則</span><span class="sxs-lookup"><span data-stu-id="092de-104">Rules</span></span>  

 <span data-ttu-id="092de-105">Visual Basic 中的元素名稱必須遵守下列規則：</span><span class="sxs-lookup"><span data-stu-id="092de-105">An element name in Visual Basic must observe the following rules:</span></span>  
  
- <span data-ttu-id="092de-106">它必須以字母字元或底線 (`_`) 開頭。</span><span class="sxs-lookup"><span data-stu-id="092de-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="092de-107">它只能包含字母字元、小數位數和底線。</span><span class="sxs-lookup"><span data-stu-id="092de-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
- <span data-ttu-id="092de-108">如果開頭為底線，則必須包含至少一個字母字元或十進位數。</span><span class="sxs-lookup"><span data-stu-id="092de-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
- <span data-ttu-id="092de-109">長度不得超過1023個字元。</span><span class="sxs-lookup"><span data-stu-id="092de-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="092de-110">1023個字元的長度限制也適用于完整名稱的整個字串，例如 `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement` 。</span><span class="sxs-lookup"><span data-stu-id="092de-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="092de-111">下列範例顯示一些有效的元素名稱。</span><span class="sxs-lookup"><span data-stu-id="092de-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="092de-112">下列範例顯示一些不正確元素名稱。</span><span class="sxs-lookup"><span data-stu-id="092de-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="092de-113">第一個只包含底線，第二個開頭是十進位數，而第三個則包含不正確字元 ($) 。</span><span class="sxs-lookup"><span data-stu-id="092de-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
> <span data-ttu-id="092de-114">以底線 (開頭的元素名稱 `_`) 不是 [語言獨立性和語言獨立元件](../../../../standard/language-independence-and-language-independent-components.md) (CLS) 的一部分，因此符合 cls 標準的程式碼無法使用定義這類名稱的元件。</span><span class="sxs-lookup"><span data-stu-id="092de-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="092de-115">不過，專案名稱中其他位置的底線符合 CLS 標準。</span><span class="sxs-lookup"><span data-stu-id="092de-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="092de-116">名稱長度指導方針</span><span class="sxs-lookup"><span data-stu-id="092de-116">Name Length Guidelines</span></span>  

 <span data-ttu-id="092de-117">實際來說，您的名稱應該越短越好，同時仍然清楚地識別元素的本質。</span><span class="sxs-lookup"><span data-stu-id="092de-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="092de-118">這可提升程式碼的可讀性，並減少行長度和原始程式檔大小。</span><span class="sxs-lookup"><span data-stu-id="092de-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="092de-119">另一方面，您的名稱應該不太簡短，因為它不會充分描述專案所代表的專案，以及您的程式碼使用它的方式。</span><span class="sxs-lookup"><span data-stu-id="092de-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="092de-120">這對您的程式碼可讀性相當重要。</span><span class="sxs-lookup"><span data-stu-id="092de-120">This is important for the readability of your code.</span></span> <span data-ttu-id="092de-121">如果有其他人嘗試瞭解它，或您想要在撰寫後很長一段時間，則適當的專案名稱可以節省相當長的時間。</span><span class="sxs-lookup"><span data-stu-id="092de-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="092de-122">轉義名稱</span><span class="sxs-lookup"><span data-stu-id="092de-122">Escaped Names</span></span>  

 <span data-ttu-id="092de-123">一般來說，元素名稱不能符合 Visual Basic 所保留的任何關鍵字，例如 `Case` 或 `Friend` 。</span><span class="sxs-lookup"><span data-stu-id="092de-123">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="092de-124">不過，您可以定義以括弧括住的 *轉義名稱* (`[ ]`) 。</span><span class="sxs-lookup"><span data-stu-id="092de-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="092de-125">因為括弧移除任何不明確的，所以可將任何 Visual Basic 關鍵字對應到一個轉義名稱。</span><span class="sxs-lookup"><span data-stu-id="092de-125">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="092de-126">當您稍後在程式碼中參考該名稱時，您也可以使用括弧。</span><span class="sxs-lookup"><span data-stu-id="092de-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="092de-127">一般而言，您應該只在下列情況使用轉義名稱：</span><span class="sxs-lookup"><span data-stu-id="092de-127">In general, you should use escaped names only when:</span></span>  
  
- <span data-ttu-id="092de-128">您的程式碼已從舊版的 Visual Basic 遷移，而該版本並未保留作為名稱使用的關鍵字;或</span><span class="sxs-lookup"><span data-stu-id="092de-128">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
- <span data-ttu-id="092de-129">您正在使用以另一種語言撰寫的程式碼，而不會保留指定的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="092de-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="092de-130">否則，如果專案的名稱與關鍵字衝突，您應該考慮重新命名元素。</span><span class="sxs-lookup"><span data-stu-id="092de-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="092de-131">整合式開發環境 (IDE) 提供簡單的方法來進行這種作法。</span><span class="sxs-lookup"><span data-stu-id="092de-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="092de-132">如需詳細資訊，請參閱 [重構](/visualstudio/ide/refactoring-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="092de-132">For more information, see [Refactoring](/visualstudio/ide/refactoring-in-visual-studio).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="092de-133">名稱中的區分大小寫</span><span class="sxs-lookup"><span data-stu-id="092de-133">Case Sensitivity in Names</span></span>  

 <span data-ttu-id="092de-134">Visual Basic 中的元素名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="092de-134">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="092de-135">這表示當編譯器比較兩個名稱（僅限字母大小寫不同）時，它會將它們解釋為相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="092de-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="092de-136">例如，它會將 `ABC` 和 `abc` 視為相同的宣告元素。</span><span class="sxs-lookup"><span data-stu-id="092de-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="092de-137">不過，Common Language Runtime (CLR) 使用區分大小寫 的繫結。</span><span class="sxs-lookup"><span data-stu-id="092de-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="092de-138">因此，當您產生一個組件或 DLL 並讓其他組件使用時，您的名稱將會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="092de-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="092de-139">例如，如果您使用名為 `ABC`的元素來定義類別，而其他組件透過 Common Language Runtime 使用您的類別，則這些組件必須以 `ABC`來表示該元素。</span><span class="sxs-lookup"><span data-stu-id="092de-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="092de-140">如果您接著重新編譯類別，並將元素的名稱變更為 `abc` ，其他使用您類別的元件就無法再存取該專案。</span><span class="sxs-lookup"><span data-stu-id="092de-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="092de-141">因此，當您發行組件的更新版本時，不應該變更任何公用元素的字母大小寫。</span><span class="sxs-lookup"><span data-stu-id="092de-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="092de-142">名稱和地區設定</span><span class="sxs-lookup"><span data-stu-id="092de-142">Names and Locales</span></span>  

 <span data-ttu-id="092de-143">名稱的比較與地區設定無關。</span><span class="sxs-lookup"><span data-stu-id="092de-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="092de-144">如果兩個名稱在一個地區設定中相符，它們保證會在所有地區設定中相符。</span><span class="sxs-lookup"><span data-stu-id="092de-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="092de-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="092de-145">See also</span></span>

- [<span data-ttu-id="092de-146">宣告的元素</span><span class="sxs-lookup"><span data-stu-id="092de-146">Declared Elements</span></span>](index.md)
- [<span data-ttu-id="092de-147">宣告項目特性</span><span class="sxs-lookup"><span data-stu-id="092de-147">Declared Element Characteristics</span></span>](declared-element-characteristics.md)
- [<span data-ttu-id="092de-148">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="092de-148">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="092de-149">陳述式</span><span class="sxs-lookup"><span data-stu-id="092de-149">Statements</span></span>](../../../language-reference/statements/index.md)
