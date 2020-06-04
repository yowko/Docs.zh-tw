---
title: 命名規範
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: 20531e379ddf9b93a278795e9b3c0eb91b47e077
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398340"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="b3d87-102">Visual Basic 命名慣例</span><span class="sxs-lookup"><span data-stu-id="b3d87-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="b3d87-103">當您在 Visual Basic 應用程式中為元素命名時，該名稱的第一個字元必須是字母字元或底線。</span><span class="sxs-lookup"><span data-stu-id="b3d87-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="b3d87-104">不過，請注意，以底線開頭的名稱不符合[語言獨立性和與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（CLS）。</span><span class="sxs-lookup"><span data-stu-id="b3d87-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="b3d87-105">下列建議適用于命名。</span><span class="sxs-lookup"><span data-stu-id="b3d87-105">The following suggestions apply to naming.</span></span>  
  
- <span data-ttu-id="b3d87-106">以大寫字母開頭的名稱中的每個個別單字，如同 `FindLastRecord` 和 `RedrawMyForm` 。</span><span class="sxs-lookup"><span data-stu-id="b3d87-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
- <span data-ttu-id="b3d87-107">使用動詞來開始函式和方法名稱，如同 `InitNameArray` 或 `CloseDialog` 。</span><span class="sxs-lookup"><span data-stu-id="b3d87-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
- <span data-ttu-id="b3d87-108">以名詞開頭的類別、結構、模組和屬性名稱，例如 `EmployeeName` 或 `CarAccessory` 。</span><span class="sxs-lookup"><span data-stu-id="b3d87-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
- <span data-ttu-id="b3d87-109">以前置詞 "I" 開頭，後面接著名詞或名詞片語（例如 `IComponent` ），或使用描述介面行為（例如）的形容詞來開始介面名稱 `IPersistable` 。</span><span class="sxs-lookup"><span data-stu-id="b3d87-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="b3d87-110">請勿使用底線，並謹慎使用縮寫，因為縮寫可能會造成混淆。</span><span class="sxs-lookup"><span data-stu-id="b3d87-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
- <span data-ttu-id="b3d87-111">以名詞開頭的事件處理常式名稱，描述後面接著 "" 後置詞的事件種類 `EventHandler` ，如 "" `MouseEventHandler` 。</span><span class="sxs-lookup"><span data-stu-id="b3d87-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
- <span data-ttu-id="b3d87-112">在事件引數類別的名稱中，包含 " `EventArgs` " 尾碼。</span><span class="sxs-lookup"><span data-stu-id="b3d87-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
- <span data-ttu-id="b3d87-113">如果事件具有 "before" 或 "after" 的概念，請使用存在或過去時態的尾碼，如 " `ControlAdd` " 或 " `ControlAdded` "。</span><span class="sxs-lookup"><span data-stu-id="b3d87-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
- <span data-ttu-id="b3d87-114">若為長時間或經常使用的詞彙，請使用縮寫來保留名稱長度合理，例如 "HTML"，而不是 "超文字標記語言 (HTML)"。</span><span class="sxs-lookup"><span data-stu-id="b3d87-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="b3d87-115">一般而言，大於32個字元的變數名稱很容易讀取到設定為低解析度的監視器上。</span><span class="sxs-lookup"><span data-stu-id="b3d87-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="b3d87-116">此外，請確定您的縮寫在整個應用程式中都是一致的。</span><span class="sxs-lookup"><span data-stu-id="b3d87-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="b3d87-117">在「HTML」和「超文字標記語言 (HTML)」之間隨機切換專案可能會造成混淆。</span><span class="sxs-lookup"><span data-stu-id="b3d87-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
- <span data-ttu-id="b3d87-118">避免在內部範圍中使用與外部範圍中的名稱相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="b3d87-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="b3d87-119">如果存取錯誤的變數，可能會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b3d87-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="b3d87-120">如果變數與相同名稱的關鍵字之間發生衝突，您必須在其前面加上適當的類型程式庫，以識別關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b3d87-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="b3d87-121">例如，如果您有一個名為的變數 `Date` ，您只能藉由呼叫來使用內部 `Date` 函數 <xref:System.DateTime.Date%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="b3d87-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3d87-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3d87-122">See also</span></span>

- [<span data-ttu-id="b3d87-123">程式碼中的項目名稱關鍵字</span><span class="sxs-lookup"><span data-stu-id="b3d87-123">Keywords as Element Names in Code</span></span>](keywords-as-element-names-in-code.md)
- [<span data-ttu-id="b3d87-124">Me、My、MyBase 及 MyClass</span><span class="sxs-lookup"><span data-stu-id="b3d87-124">Me, My, MyBase, and MyClass</span></span>](me-my-mybase-and-myclass.md)
- [<span data-ttu-id="b3d87-125">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="b3d87-125">Declared Element Names</span></span>](../language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="b3d87-126">程式結構和程式碼慣例</span><span class="sxs-lookup"><span data-stu-id="b3d87-126">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="b3d87-127">Visual Basic 語言參考</span><span class="sxs-lookup"><span data-stu-id="b3d87-127">Visual Basic Language Reference</span></span>](../../language-reference/index.md)
