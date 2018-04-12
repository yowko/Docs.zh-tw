---
title: 預設屬性 &#39;&lt;propertyname1&gt;&#39; 與預設屬性 &#39; 衝突&lt;propertyname2&gt;&#39; 在 &#39;&lt;classname&gt;&#39;，所以應該宣告為 &#39;Shadows &#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af92c06f6d07b6ea64a05b9043547a46e3679111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="d82e3-102">預設屬性 &#39;&lt;propertyname1&gt;&#39; 與預設屬性 &#39; 衝突&lt;propertyname2&gt;&#39; 在 &#39;&lt;classname&gt;&#39;，所以應該宣告為 &#39;Shadows &#39;</span><span class="sxs-lookup"><span data-stu-id="d82e3-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="d82e3-103">屬性會宣告具有相同名稱做為基底類別中定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="d82e3-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="d82e3-104">在此情況下，此類別中的屬性應該會遮蔽基底類別屬性。</span><span class="sxs-lookup"><span data-stu-id="d82e3-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="d82e3-105">這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="d82e3-105">This message is a warning.</span></span> <span data-ttu-id="d82e3-106">預設會假設為`Shadows` 。</span><span class="sxs-lookup"><span data-stu-id="d82e3-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="d82e3-107">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="d82e3-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d82e3-108">**錯誤 ID:** BC40007</span><span class="sxs-lookup"><span data-stu-id="d82e3-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d82e3-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d82e3-109">To correct this error</span></span>  
  
-   <span data-ttu-id="d82e3-110">新增`Shadows`關鍵字來宣告或變更所宣告的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="d82e3-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82e3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d82e3-111">See Also</span></span>  
 [<span data-ttu-id="d82e3-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="d82e3-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="d82e3-113">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="d82e3-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
