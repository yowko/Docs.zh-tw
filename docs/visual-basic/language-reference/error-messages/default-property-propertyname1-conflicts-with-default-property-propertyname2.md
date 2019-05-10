---
title: 預設屬性 '<propertyname1>' 與基底 '<propertyname2>' 中的預設屬性 '<classname>' 產生衝突，所以必須宣告為 'Shadows'
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: c964003217e7b96cf25288e2ae6ae6a2fb07a6c3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651383"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="728e9-102">預設屬性 '\<屬性名稱 1&gt >' 衝突的預設屬性'\<propertyname2 >' 中 '\<類別名稱 >'，所以應宣告為 'Shadows'</span><span class="sxs-lookup"><span data-stu-id="728e9-102">Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>
<span data-ttu-id="728e9-103">屬性會宣告具有相同名稱做為基底類別中定義的屬性。</span><span class="sxs-lookup"><span data-stu-id="728e9-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="728e9-104">在此情況下，此類別中的屬性應該會遮蔽基底類別屬性。</span><span class="sxs-lookup"><span data-stu-id="728e9-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="728e9-105">這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="728e9-105">This message is a warning.</span></span> <span data-ttu-id="728e9-106">預設會假設為`Shadows` 。</span><span class="sxs-lookup"><span data-stu-id="728e9-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="728e9-107">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="728e9-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="728e9-108">**錯誤 ID:** BC40007</span><span class="sxs-lookup"><span data-stu-id="728e9-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="728e9-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="728e9-109">To correct this error</span></span>  
  
- <span data-ttu-id="728e9-110">新增`Shadows`關鍵字來宣告或變更所宣告的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="728e9-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="728e9-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="728e9-111">See also</span></span>

- [<span data-ttu-id="728e9-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="728e9-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="728e9-113">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="728e9-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
