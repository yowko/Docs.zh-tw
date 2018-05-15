---
title: '&#39;&lt;介面名稱&gt;。&lt;membername&gt; &#39;已經由基底類別實作&#39;&lt;基&gt;&#39;。 重新實作&lt;類型&gt;假設'
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 9054c293ede9db4637f23579407f2f76db29f2ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a><span data-ttu-id="c8125-103">&#39;&lt;介面名稱&gt;。&lt;membername&gt; &#39;已經由基底類別實作&#39;&lt;基&gt;&#39;。</span><span class="sxs-lookup"><span data-stu-id="c8125-103">&#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;.</span></span> <span data-ttu-id="c8125-104">重新實作&lt;類型&gt;假設</span><span class="sxs-lookup"><span data-stu-id="c8125-104">Re-implementation of &lt;type&gt; assumed</span></span>
<span data-ttu-id="c8125-105">屬性、 程序或在衍生類別中的事件使用`Implements`子句指定的基底類別中已實作介面成員。</span><span class="sxs-lookup"><span data-stu-id="c8125-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="c8125-106">衍生類別可以重新實作透過其基底類別所實作的介面成員。</span><span class="sxs-lookup"><span data-stu-id="c8125-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="c8125-107">這與覆寫基底類別實作不同。</span><span class="sxs-lookup"><span data-stu-id="c8125-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="c8125-108">如需詳細資訊，請參閱[實作](../../../visual-basic/language-reference/statements/implements-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="c8125-108">For more information, see [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="c8125-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="c8125-109">By default, this message is a warning.</span></span> <span data-ttu-id="c8125-110">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="c8125-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c8125-111">**錯誤 ID:** BC42015</span><span class="sxs-lookup"><span data-stu-id="c8125-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c8125-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c8125-112">To correct this error</span></span>  
  
-   <span data-ttu-id="c8125-113">如果您要重新實作介面成員，則不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="c8125-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="c8125-114">在衍生類別中的程式碼會存取重新實作的成員，除非您使用`MyBase`關鍵字存取基底類別實作。</span><span class="sxs-lookup"><span data-stu-id="c8125-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
-   <span data-ttu-id="c8125-115">如果您不要重新實作介面成員，請從屬性、程序或事件宣告中移除 `Implements` 子句。</span><span class="sxs-lookup"><span data-stu-id="c8125-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8125-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8125-116">See Also</span></span>  
 [<span data-ttu-id="c8125-117">介面</span><span class="sxs-lookup"><span data-stu-id="c8125-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
