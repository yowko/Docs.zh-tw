---
title: 預設屬性 '<propertyname1>' 與基底 '<propertyname2>' 中的預設屬性 '<classname>' 產生衝突，所以必須宣告為 'Shadows'
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 37f98ce8120d5861552819690f9d5f22c9959a0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409721"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="e9a9a-102">預設屬性 '\<propertyname1>' 與基底 '\<propertyname2>' 中的預設屬性 '\<classname>' 產生衝突，所以必須宣告為 'Shadows'</span><span class="sxs-lookup"><span data-stu-id="e9a9a-102">Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>
<span data-ttu-id="e9a9a-103">使用與基類中所定義之屬性相同的名稱來宣告屬性。</span><span class="sxs-lookup"><span data-stu-id="e9a9a-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="e9a9a-104">在此情況下，此類別中的屬性應該遮蔽基類屬性。</span><span class="sxs-lookup"><span data-stu-id="e9a9a-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="e9a9a-105">這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="e9a9a-105">This message is a warning.</span></span> <span data-ttu-id="e9a9a-106">預設會假設為`Shadows` 。</span><span class="sxs-lookup"><span data-stu-id="e9a9a-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="e9a9a-107">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="e9a9a-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="e9a9a-108">**錯誤識別碼：** BC40007</span><span class="sxs-lookup"><span data-stu-id="e9a9a-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e9a9a-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e9a9a-109">To correct this error</span></span>  
  
- <span data-ttu-id="e9a9a-110">將 `Shadows` 關鍵字加入至宣告，或變更所宣告之屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="e9a9a-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a9a-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9a9a-111">See also</span></span>

- [<span data-ttu-id="e9a9a-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="e9a9a-112">Shadows</span></span>](../modifiers/shadows.md)
- [<span data-ttu-id="e9a9a-113">Visual Basic 中的遮蔽功能</span><span class="sxs-lookup"><span data-stu-id="e9a9a-113">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
