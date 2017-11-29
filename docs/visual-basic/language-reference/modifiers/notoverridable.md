---
title: NotOverridable (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6fc5fb006b36cda1b6ad0e128604bc3bb427fd94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="411af-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="411af-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="411af-103">指定的屬性或程序無法覆寫衍生類別中。</span><span class="sxs-lookup"><span data-stu-id="411af-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="411af-104">備註</span><span class="sxs-lookup"><span data-stu-id="411af-104">Remarks</span></span>  
 <span data-ttu-id="411af-105">`NotOverridable`修飾詞可防止屬性或方法在衍生類別中覆寫。</span><span class="sxs-lookup"><span data-stu-id="411af-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="411af-106">[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)修飾詞允許在衍生類別中覆寫類別中的屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="411af-106">The [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="411af-107">如需詳細資訊，請參閱[繼承的基本概念](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="411af-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="411af-108">如果`Overridable`或`NotOverridable`修飾詞未指定，預設值取決於是否屬性或方法會覆寫基底類別屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="411af-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="411af-109">如果屬性或方法覆寫基底類別屬性或方法，預設值是`Overridable`; 否則它是`NotOverridable`。</span><span class="sxs-lookup"><span data-stu-id="411af-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="411af-110">無法覆寫的項目有時稱為*密封*項目。</span><span class="sxs-lookup"><span data-stu-id="411af-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="411af-111">您只能在屬性或程序宣告陳述式中使用 `NotOverridable`。</span><span class="sxs-lookup"><span data-stu-id="411af-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="411af-112">您可以指定`NotOverridable`只能在屬性或程序會覆寫另一個屬性或程序，也就是只有在搭配`Overrides`。</span><span class="sxs-lookup"><span data-stu-id="411af-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="411af-113">結合的修飾詞</span><span class="sxs-lookup"><span data-stu-id="411af-113">Combined Modifiers</span></span>  
 <span data-ttu-id="411af-114">您無法指定`Overridable`或`NotOverridable`如`Private`方法。</span><span class="sxs-lookup"><span data-stu-id="411af-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="411af-115">您無法指定`NotOverridable`搭配`MustOverride`， `Overridable`，或`Shared`相同宣告中。</span><span class="sxs-lookup"><span data-stu-id="411af-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="411af-116">使用方式</span><span class="sxs-lookup"><span data-stu-id="411af-116">Usage</span></span>  
 <span data-ttu-id="411af-117">`NotOverridable` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="411af-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="411af-118">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="411af-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="411af-119">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="411af-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="411af-120">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="411af-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="411af-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="411af-121">See Also</span></span>  
 [<span data-ttu-id="411af-122">修飾詞</span><span class="sxs-lookup"><span data-stu-id="411af-122">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)  
 [<span data-ttu-id="411af-123">繼承的基本概念</span><span class="sxs-lookup"><span data-stu-id="411af-123">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="411af-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="411af-124">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="411af-125">Overridable</span><span class="sxs-lookup"><span data-stu-id="411af-125">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="411af-126">Overrides</span><span class="sxs-lookup"><span data-stu-id="411af-126">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="411af-127">關鍵字</span><span class="sxs-lookup"><span data-stu-id="411af-127">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="411af-128">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="411af-128">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
