---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: 163ec17f3ea96744290c54a73054ab132f842127
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647666"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="6e459-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e459-102">WriteOnly (Visual Basic)</span></span>
<span data-ttu-id="6e459-103">指定可寫入屬性，但無法讀取。</span><span class="sxs-lookup"><span data-stu-id="6e459-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e459-104">備註</span><span class="sxs-lookup"><span data-stu-id="6e459-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6e459-105">規則</span><span class="sxs-lookup"><span data-stu-id="6e459-105">Rules</span></span>  
 <span data-ttu-id="6e459-106">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="6e459-106">**Declaration Context.**</span></span> <span data-ttu-id="6e459-107">您只能在模組層級使用 `WriteOnly`。</span><span class="sxs-lookup"><span data-stu-id="6e459-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="6e459-108">這表示的宣告內容`WriteOnly`屬性必須是類別、 結構或模組，並不能是原始程式檔、 命名空間或程序。</span><span class="sxs-lookup"><span data-stu-id="6e459-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="6e459-109">您可以宣告為屬性`WriteOnly`，但不是變數。</span><span class="sxs-lookup"><span data-stu-id="6e459-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="6e459-110">何時使用 WriteOnly</span><span class="sxs-lookup"><span data-stu-id="6e459-110">When to Use WriteOnly</span></span>  
 <span data-ttu-id="6e459-111">有時您想要能夠設定的值，但不是會探索什麼是使用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6e459-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="6e459-112">比方說，機密資料，例如社會的註冊碼或密碼，必須要防範未設定任何元件的存取。</span><span class="sxs-lookup"><span data-stu-id="6e459-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="6e459-113">在這些情況下，您可以使用`WriteOnly`屬性來設定的值。</span><span class="sxs-lookup"><span data-stu-id="6e459-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6e459-114">當您定義並使用`WriteOnly`屬性，請考慮下列的額外保護措施：</span><span class="sxs-lookup"><span data-stu-id="6e459-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
- <span data-ttu-id="6e459-115">**覆寫。**</span><span class="sxs-lookup"><span data-stu-id="6e459-115">**Overriding.**</span></span> <span data-ttu-id="6e459-116">如果屬性是類別的成員，讓它預設為[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)，並不會將宣告`Overridable`或`MustOverride`。</span><span class="sxs-lookup"><span data-stu-id="6e459-116">If the property is a member of a class, allow it to default to [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="6e459-117">這可防止衍生的類別進行覆寫透過不良的存取。</span><span class="sxs-lookup"><span data-stu-id="6e459-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
- <span data-ttu-id="6e459-118">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="6e459-118">**Access Level.**</span></span> <span data-ttu-id="6e459-119">如果您在兩個變數中有一或多個保留屬性的機密資料，請宣告這些[私人](../../../visual-basic/language-reference/modifiers/private.md)，讓其他的程式碼可以存取它們。</span><span class="sxs-lookup"><span data-stu-id="6e459-119">If you hold the property's sensitive data in one or more variables, declare them [Private](../../../visual-basic/language-reference/modifiers/private.md) so that no other code can access them.</span></span>  
  
- <span data-ttu-id="6e459-120">**加密。**</span><span class="sxs-lookup"><span data-stu-id="6e459-120">**Encryption.**</span></span> <span data-ttu-id="6e459-121">儲存所有的機密資料，以加密形式中，而不是以純文字。</span><span class="sxs-lookup"><span data-stu-id="6e459-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="6e459-122">如果惡意程式碼以某種方式取得對該區域的記憶體存取，就更難進行資料的使用。</span><span class="sxs-lookup"><span data-stu-id="6e459-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="6e459-123">也很有用，如果必須序列化的敏感性資料加密。</span><span class="sxs-lookup"><span data-stu-id="6e459-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
- <span data-ttu-id="6e459-124">**正在重設。**</span><span class="sxs-lookup"><span data-stu-id="6e459-124">**Resetting.**</span></span> <span data-ttu-id="6e459-125">正在終止類別、 結構或模組定義該屬性時，重設的敏感性資料，預設值或其他無意義的值。</span><span class="sxs-lookup"><span data-stu-id="6e459-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="6e459-126">釋放該記憶體區域的一般存取時，這會提供額外的保護。</span><span class="sxs-lookup"><span data-stu-id="6e459-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
- <span data-ttu-id="6e459-127">**持續性。**</span><span class="sxs-lookup"><span data-stu-id="6e459-127">**Persistence.**</span></span> <span data-ttu-id="6e459-128">不會保存任何敏感性資料，例如在磁碟上，如果您可以避免它。</span><span class="sxs-lookup"><span data-stu-id="6e459-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="6e459-129">此外，不寫入任何機密資料到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="6e459-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="6e459-130">`WriteOnly`修飾詞，請使用此內容中：</span><span class="sxs-lookup"><span data-stu-id="6e459-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="6e459-131">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="6e459-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6e459-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e459-132">See also</span></span>

- [<span data-ttu-id="6e459-133">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="6e459-133">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="6e459-134">Private</span><span class="sxs-lookup"><span data-stu-id="6e459-134">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="6e459-135">關鍵字</span><span class="sxs-lookup"><span data-stu-id="6e459-135">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
