---
title: WriteOnly
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
ms.openlocfilehash: 12a1030a423359a3e4122eea98e223a1a02f680c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867614"
---
# <a name="writeonly-visual-basic"></a><span data-ttu-id="04fc7-102">WriteOnly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04fc7-102">WriteOnly (Visual Basic)</span></span>

<span data-ttu-id="04fc7-103">指定可寫入但無法讀取的屬性。</span><span class="sxs-lookup"><span data-stu-id="04fc7-103">Specifies that a property can be written but not read.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04fc7-104">備註</span><span class="sxs-lookup"><span data-stu-id="04fc7-104">Remarks</span></span>  
  
## <a name="rules"></a><span data-ttu-id="04fc7-105">規則</span><span class="sxs-lookup"><span data-stu-id="04fc7-105">Rules</span></span>  

 <span data-ttu-id="04fc7-106">**宣告內容。**</span><span class="sxs-lookup"><span data-stu-id="04fc7-106">**Declaration Context.**</span></span> <span data-ttu-id="04fc7-107">您只能在模組層級使用 `WriteOnly`。</span><span class="sxs-lookup"><span data-stu-id="04fc7-107">You can use `WriteOnly` only at module level.</span></span> <span data-ttu-id="04fc7-108">這表示屬性的宣告內容 `WriteOnly` 必須是類別、結構或模組，且不能是原始程式檔、命名空間或程式。</span><span class="sxs-lookup"><span data-stu-id="04fc7-108">This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.</span></span>  
  
 <span data-ttu-id="04fc7-109">您可以將屬性宣告為 `WriteOnly` ，而不是變數。</span><span class="sxs-lookup"><span data-stu-id="04fc7-109">You can declare a property as `WriteOnly`, but not a variable.</span></span>  
  
## <a name="when-to-use-writeonly"></a><span data-ttu-id="04fc7-110">使用 WriteOnly 的時機</span><span class="sxs-lookup"><span data-stu-id="04fc7-110">When to Use WriteOnly</span></span>  

 <span data-ttu-id="04fc7-111">有時候您會想要使用程式碼來設定值，但不能找出它的值。</span><span class="sxs-lookup"><span data-stu-id="04fc7-111">Sometimes you want the consuming code to be able to set a value but not discover what it is.</span></span> <span data-ttu-id="04fc7-112">例如，機密資料（例如社交註冊號碼或密碼）必須受到保護，使其無法存取未設定它的任何元件。</span><span class="sxs-lookup"><span data-stu-id="04fc7-112">For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it.</span></span> <span data-ttu-id="04fc7-113">在這些情況下，您可以使用 `WriteOnly` 屬性來設定值。</span><span class="sxs-lookup"><span data-stu-id="04fc7-113">In these cases, you can use a `WriteOnly` property to set the value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="04fc7-114">當您定義並使用 `WriteOnly` 屬性時，請考慮下列額外的保護措施：</span><span class="sxs-lookup"><span data-stu-id="04fc7-114">When you define and use a `WriteOnly` property, consider the following additional protective measures:</span></span>  
  
- <span data-ttu-id="04fc7-115">**重寫。**</span><span class="sxs-lookup"><span data-stu-id="04fc7-115">**Overriding.**</span></span> <span data-ttu-id="04fc7-116">如果屬性是類別的成員，則可讓它預設為 [NotOverridable](notoverridable.md)，而且不會將它宣告為 `Overridable` 或 `MustOverride` 。</span><span class="sxs-lookup"><span data-stu-id="04fc7-116">If the property is a member of a class, allow it to default to [NotOverridable](notoverridable.md), and do not declare it `Overridable` or `MustOverride`.</span></span> <span data-ttu-id="04fc7-117">這可防止衍生類別透過覆寫進行不想要的存取。</span><span class="sxs-lookup"><span data-stu-id="04fc7-117">This prevents a derived class from making undesired access through an override.</span></span>  
  
- <span data-ttu-id="04fc7-118">**存取層級。**</span><span class="sxs-lookup"><span data-stu-id="04fc7-118">**Access Level.**</span></span> <span data-ttu-id="04fc7-119">如果您將屬性的機密資料保存在一或多個變數中，請將其宣告為 [私](private.md) 用，讓其他程式碼無法存取它們。</span><span class="sxs-lookup"><span data-stu-id="04fc7-119">If you hold the property's sensitive data in one or more variables, declare them [Private](private.md) so that no other code can access them.</span></span>  
  
- <span data-ttu-id="04fc7-120">**加密。**</span><span class="sxs-lookup"><span data-stu-id="04fc7-120">**Encryption.**</span></span> <span data-ttu-id="04fc7-121">以加密形式儲存所有機密資料，而不是以純文字格式儲存。</span><span class="sxs-lookup"><span data-stu-id="04fc7-121">Store all sensitive data in encrypted form rather than in plain text.</span></span> <span data-ttu-id="04fc7-122">如果惡意程式碼會以某種方式取得該記憶體區域的存取權，就會更難利用資料。</span><span class="sxs-lookup"><span data-stu-id="04fc7-122">If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data.</span></span> <span data-ttu-id="04fc7-123">如果必須序列化機密資料，加密也會很有用。</span><span class="sxs-lookup"><span data-stu-id="04fc7-123">Encryption is also useful if it is necessary to serialize the sensitive data.</span></span>  
  
- <span data-ttu-id="04fc7-124">**重 置。**</span><span class="sxs-lookup"><span data-stu-id="04fc7-124">**Resetting.**</span></span> <span data-ttu-id="04fc7-125">當定義屬性的類別、結構或模組結束時，請將機密資料重設為預設值或其他無意義的值。</span><span class="sxs-lookup"><span data-stu-id="04fc7-125">When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values.</span></span> <span data-ttu-id="04fc7-126">當釋放該記憶體區域以進行一般存取時，這會提供額外的保護。</span><span class="sxs-lookup"><span data-stu-id="04fc7-126">This gives extra protection when that area of memory is freed for general access.</span></span>  
  
- <span data-ttu-id="04fc7-127">**堅持。**</span><span class="sxs-lookup"><span data-stu-id="04fc7-127">**Persistence.**</span></span> <span data-ttu-id="04fc7-128">請勿保存任何機密資料（例如，在磁片上，如果您可以避免的話）。</span><span class="sxs-lookup"><span data-stu-id="04fc7-128">Do not persist any sensitive data, for example on disk, if you can avoid it.</span></span> <span data-ttu-id="04fc7-129">此外，請勿將任何敏感性資料寫入剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="04fc7-129">Also, do not write any sensitive data to the Clipboard.</span></span>  
  
 <span data-ttu-id="04fc7-130">`WriteOnly`修飾詞可用於此內容中：</span><span class="sxs-lookup"><span data-stu-id="04fc7-130">The `WriteOnly` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="04fc7-131">Property Statement</span><span class="sxs-lookup"><span data-stu-id="04fc7-131">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="04fc7-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04fc7-132">See also</span></span>

- [<span data-ttu-id="04fc7-133">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="04fc7-133">ReadOnly</span></span>](readonly.md)
- [<span data-ttu-id="04fc7-134">私人</span><span class="sxs-lookup"><span data-stu-id="04fc7-134">Private</span></span>](private.md)
- [<span data-ttu-id="04fc7-135">關鍵字</span><span class="sxs-lookup"><span data-stu-id="04fc7-135">Keywords</span></span>](../keywords/index.md)
