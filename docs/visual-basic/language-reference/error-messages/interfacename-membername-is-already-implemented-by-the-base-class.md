---
title: "'<interfacename>.<membername>'已實作的基底類別'<baseclassname>'。 重新實作<type>假設"
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 64bd7771820c2a4073350b7a5189d3a32c4775be
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832356"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a><span data-ttu-id="1cce0-103">'\<介面名稱 >。\<成員名稱 >' 已經由基底類別的實作\<基 >'。</span><span class="sxs-lookup"><span data-stu-id="1cce0-103">'\<interfacename>.\<membername>' is already implemented by the base class '\<baseclassname>'.</span></span> <span data-ttu-id="1cce0-104">重新實作\<類型 > 假設</span><span class="sxs-lookup"><span data-stu-id="1cce0-104">Re-implementation of \<type> assumed</span></span>
<span data-ttu-id="1cce0-105">屬性、 程序或在衍生類別中的事件使用`Implements`子句指定的基底類別中已實作介面成員。</span><span class="sxs-lookup"><span data-stu-id="1cce0-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="1cce0-106">衍生類別可以重新實作透過其基底類別所實作的介面成員。</span><span class="sxs-lookup"><span data-stu-id="1cce0-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="1cce0-107">這與覆寫基底類別實作不同。</span><span class="sxs-lookup"><span data-stu-id="1cce0-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="1cce0-108">如需詳細資訊，請參閱 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="1cce0-108">For more information, see [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="1cce0-109">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="1cce0-109">By default, this message is a warning.</span></span> <span data-ttu-id="1cce0-110">如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="1cce0-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="1cce0-111">**錯誤 ID:** BC42015</span><span class="sxs-lookup"><span data-stu-id="1cce0-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1cce0-112">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1cce0-112">To correct this error</span></span>  
  
-   <span data-ttu-id="1cce0-113">如果您要重新實作介面成員，則不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="1cce0-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="1cce0-114">在衍生類別中的程式碼會存取重新實作的成員，除非您使用`MyBase`關鍵字存取基底類別實作。</span><span class="sxs-lookup"><span data-stu-id="1cce0-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
-   <span data-ttu-id="1cce0-115">如果您不要重新實作介面成員，請從屬性、程序或事件宣告中移除 `Implements` 子句。</span><span class="sxs-lookup"><span data-stu-id="1cce0-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cce0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cce0-116">See also</span></span>

- [<span data-ttu-id="1cce0-117">介面</span><span class="sxs-lookup"><span data-stu-id="1cce0-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
