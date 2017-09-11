---
title: "預設屬性 &quot;&lt;propertyname1&gt;&quot;衝突的預設屬性&quot;&lt;propertyname2&gt;&quot;在&quot;&lt;classname&gt;&quot;，所以必須宣告為 &quot;Shadows&quot; |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
dev_langs:
- VB
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6eac9e0fdc468e27afac82a8a7c9b2251a8f7317
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="b41c1-102">預設屬性 '&lt;propertyname1&gt;'衝突的預設屬性'&lt;propertyname2&gt;'在'&lt;classname&gt;'，所以必須宣告為 'Shadows'</span><span class="sxs-lookup"><span data-stu-id="b41c1-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="b41c1-103">屬性會宣告具有相同名稱做為基底類別中定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="b41c1-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="b41c1-104">在此情況下，此類別中的屬性會遮蔽基底類別屬性。</span><span class="sxs-lookup"><span data-stu-id="b41c1-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="b41c1-105">這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="b41c1-105">This message is a warning.</span></span> <span data-ttu-id="b41c1-106">`Shadows`預設會假設。</span><span class="sxs-lookup"><span data-stu-id="b41c1-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="b41c1-107">如需隱藏警告，或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="b41c1-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b41c1-108">**錯誤識別碼︰** BC40007</span><span class="sxs-lookup"><span data-stu-id="b41c1-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b41c1-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="b41c1-109">To correct this error</span></span>  
  
-   <span data-ttu-id="b41c1-110">新增`Shadows`關鍵字來宣告或變更所宣告的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="b41c1-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b41c1-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b41c1-111">See Also</span></span>  
 <span data-ttu-id="b41c1-112">[陰影](../../../visual-basic/language-reference/modifiers/shadows.md) </span><span class="sxs-lookup"><span data-stu-id="b41c1-112">[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) </span></span>  
<span data-ttu-id="b41c1-113"> [在 Visual Basic 中，以遮蔽](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)</span><span class="sxs-lookup"><span data-stu-id="b41c1-113"> [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)</span></span>
