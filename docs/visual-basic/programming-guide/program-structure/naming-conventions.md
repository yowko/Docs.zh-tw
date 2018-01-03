---
title: "Visual Basic 命名慣例"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97f02fd85d4796d6799a8a5b40a9137eeb79a93f
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="b8212-102">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="b8212-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="b8212-103">當您在 Visual Basic 應用程式命名項目時，該名稱的第一個字元必須是英數字元或底線。</span><span class="sxs-lookup"><span data-stu-id="b8212-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="b8212-104">不過請注意，以底線開頭的名稱不符合[語言獨立性以及與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（cls） 標準。</span><span class="sxs-lookup"><span data-stu-id="b8212-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="b8212-105">下列建議適用於命名。</span><span class="sxs-lookup"><span data-stu-id="b8212-105">The following suggestions apply to naming.</span></span>  
  
-   <span data-ttu-id="b8212-106">在開始以大寫字母，名稱中的每個個別單字`FindLastRecord`和`RedrawMyForm`。</span><span class="sxs-lookup"><span data-stu-id="b8212-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
-   <span data-ttu-id="b8212-107">具有動詞的函式和方法名稱開頭與`InitNameArray`或`CloseDialog`。</span><span class="sxs-lookup"><span data-stu-id="b8212-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
-   <span data-ttu-id="b8212-108">在開始類別、 結構、 模組和屬性名稱和名詞，`EmployeeName`或`CarAccessory`。</span><span class="sxs-lookup"><span data-stu-id="b8212-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
-   <span data-ttu-id="b8212-109">介面名稱前置詞開頭的"I"，後面接著名詞或名詞片語，例如`IComponent`，或形容詞，例如描述介面的行為與`IPersistable`。</span><span class="sxs-lookup"><span data-stu-id="b8212-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="b8212-110">請勿使用底線，並且使用縮寫盡量少用，因為縮寫會造成混淆。</span><span class="sxs-lookup"><span data-stu-id="b8212-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
-   <span data-ttu-id="b8212-111">事件處理常式名稱開頭描述類型的事件，後面接著名詞 」`EventHandler`"後置詞，如下所示"`MouseEventHandler`"。</span><span class="sxs-lookup"><span data-stu-id="b8212-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
-   <span data-ttu-id="b8212-112">事件引數類別的名稱，包括 「`EventArgs`"後置詞。</span><span class="sxs-lookup"><span data-stu-id="b8212-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
-   <span data-ttu-id="b8212-113">如果事件的概念 「 之前 」 或 「 之後 」，請使用後置字元中式或過去式，像是 「`ControlAdd`「 或 」`ControlAdded`"。</span><span class="sxs-lookup"><span data-stu-id="b8212-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
-   <span data-ttu-id="b8212-114">長或常用的條款，請使用保留名稱長度很合理，因為的縮寫，例如"HTML"，而不是 「 超文字標記語言 」。</span><span class="sxs-lookup"><span data-stu-id="b8212-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="b8212-115">一般情況下，大於 32 個字元的變數名稱不容易讀取在設定為低解析度的監視器上。</span><span class="sxs-lookup"><span data-stu-id="b8212-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="b8212-116">此外，請確定您縮寫是整個應用程式一致。</span><span class="sxs-lookup"><span data-stu-id="b8212-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="b8212-117">隨機切換移入 「 HTML 」 和 「 超文字標記語言 」 之間的專案可能會造成混淆。</span><span class="sxs-lookup"><span data-stu-id="b8212-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
-   <span data-ttu-id="b8212-118">避免使用內部範圍內外部範圍中的名稱相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="b8212-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="b8212-119">如果存取錯誤的變數，可能會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="b8212-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="b8212-120">如果之變數與相同名稱的關鍵字之間發生衝突，您必須識別關鍵字前面使用適當的型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="b8212-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="b8212-121">例如，如果您擁有名為`Date`，您可以使用內建`Date`函式，只是藉由呼叫<xref:System.DateTime.Date%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b8212-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8212-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="b8212-122">See Also</span></span>  
 [<span data-ttu-id="b8212-123">程式碼中以關鍵字做為項目名稱</span><span class="sxs-lookup"><span data-stu-id="b8212-123">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 [<span data-ttu-id="b8212-124">Me、My、MyBase 和 MyClass</span><span class="sxs-lookup"><span data-stu-id="b8212-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="b8212-125">宣告項目名稱</span><span class="sxs-lookup"><span data-stu-id="b8212-125">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="b8212-126">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="b8212-126">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="b8212-127">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="b8212-127">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
