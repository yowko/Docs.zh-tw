---
title: "名稱 &quot;&lt;名稱&gt;&quot; 未宣告 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
dev_langs:
- VB
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 11
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
ms.openlocfilehash: 1396f24a34a37db064e73d7e259c04050f409ad2
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="name-39ltnamegt39-is-not-declared"></a><span data-ttu-id="039d6-102">名稱 '&lt;名稱&gt;' 未宣告</span><span class="sxs-lookup"><span data-stu-id="039d6-102">Name &#39;&lt;name&gt;&#39; is not declared</span></span>
<span data-ttu-id="039d6-103">陳述式參考程式設計項目，但編譯器找不到具有相同名稱的項目。</span><span class="sxs-lookup"><span data-stu-id="039d6-103">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>  
  
 <span data-ttu-id="039d6-104">**錯誤識別碼︰** BC30451</span><span class="sxs-lookup"><span data-stu-id="039d6-104">**Error ID:** BC30451</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="039d6-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="039d6-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="039d6-106">請檢查參考陳述式中的名稱拼寫。</span><span class="sxs-lookup"><span data-stu-id="039d6-106">Check the spelling of the name in the referring statement.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="039d6-107">不區分大小寫，但其他的拼字變化會視為完全不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="039d6-107"> is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="039d6-108">請注意，底線 (`_`) 是名稱的一部分，因此也是拼字的一部分。</span><span class="sxs-lookup"><span data-stu-id="039d6-108">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>  
  
2.  <span data-ttu-id="039d6-109">請檢查您是否具有成員存取運算子 (`.`) 之間的物件和其成員。</span><span class="sxs-lookup"><span data-stu-id="039d6-109">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="039d6-110">例如，如果您有<xref:System.Windows.Forms.TextBox>控制項，名為`TextBox1`，以存取其<xref:System.Windows.Forms.TextBoxBase.Text%2A>屬性應該輸入`TextBox1.Text`。</xref:System.Windows.Forms.TextBoxBase.Text%2A> </xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="039d6-110">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="039d6-111">如果您改為輸入 `TextBox1Text`，便會建立不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="039d6-111">If instead you type `TextBox1Text`, you have created a different name.</span></span>  
  
3.  <span data-ttu-id="039d6-112">如果拼字正確，且任何物件的成員存取的語法正確，請確認已宣告的項目。</span><span class="sxs-lookup"><span data-stu-id="039d6-112">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="039d6-113">如需詳細資訊，請參閱[宣告項目](../../../visual-basic/programming-guide/language-features/declared-elements/index.md)。</span><span class="sxs-lookup"><span data-stu-id="039d6-113">For more information, see [Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).</span></span>  
  
4.  <span data-ttu-id="039d6-114">如果已宣告的程式設計項目，請檢查它位於範圍內。</span><span class="sxs-lookup"><span data-stu-id="039d6-114">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="039d6-115">如果參考陳述式外部宣告的程式設計項目區域中，您可能需要限定的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="039d6-115">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="039d6-116">如需詳細資訊，請參閱[Visual Basic 中的範圍](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)。</span><span class="sxs-lookup"><span data-stu-id="039d6-116">For more information, see [Scope in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="039d6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="039d6-117">See Also</span></span>  
 <span data-ttu-id="039d6-118">[宣告和常數摘要](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md) </span><span class="sxs-lookup"><span data-stu-id="039d6-118">[Declarations and Constants Summary](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md) </span></span>  
<span data-ttu-id="039d6-119"> [Visual Basic 命名慣例](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="039d6-119"> [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span></span>  
<span data-ttu-id="039d6-120"> [宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="039d6-120"> [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="039d6-121"> [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span><span class="sxs-lookup"><span data-stu-id="039d6-121"> [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span></span>
