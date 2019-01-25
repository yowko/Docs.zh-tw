---
title: 預設屬性&#39;&lt;屬性名稱 1&gt&gt; &#39;預設屬性 je v konfliktu &#39; &lt;propertyname2&gt; &#39;中&#39; &lt;classname&gt; &#39;，因此應該宣告為&#39;Shadows&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 3099467fa3c5a162c13c9235fb8d55375953ba3a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521422"
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="cbb6b-102">預設屬性&#39;&lt;屬性名稱 1&gt&gt; &#39;預設屬性 je v konfliktu &#39; &lt;propertyname2&gt; &#39;中&#39; &lt;classname&gt; &#39;，因此應該宣告為&#39;Shadows&#39;</span><span class="sxs-lookup"><span data-stu-id="cbb6b-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="cbb6b-103">屬性會宣告具有相同名稱做為基底類別中定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="cbb6b-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="cbb6b-104">在此情況下，此類別中的屬性應該會遮蔽基底類別屬性。</span><span class="sxs-lookup"><span data-stu-id="cbb6b-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="cbb6b-105">這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="cbb6b-105">This message is a warning.</span></span> <span data-ttu-id="cbb6b-106">預設會假設為`Shadows` 。</span><span class="sxs-lookup"><span data-stu-id="cbb6b-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="cbb6b-107">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="cbb6b-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="cbb6b-108">**錯誤 ID:** BC40007</span><span class="sxs-lookup"><span data-stu-id="cbb6b-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cbb6b-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="cbb6b-109">To correct this error</span></span>  
  
-   <span data-ttu-id="cbb6b-110">新增`Shadows`關鍵字來宣告或變更所宣告的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="cbb6b-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb6b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbb6b-111">See also</span></span>
- [<span data-ttu-id="cbb6b-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="cbb6b-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="cbb6b-113">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="cbb6b-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
