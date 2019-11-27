---
title: 模組 <keyword>
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: cd2f762181b5a702f0b0defd5b71bb7bdf129c7b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351557"
---
# <a name="module-keyword-visual-basic"></a><span data-ttu-id="6c68a-102">Module \<關鍵字 > （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="6c68a-102">Module \<keyword> (Visual Basic)</span></span>
<span data-ttu-id="6c68a-103">指定來源檔案開頭的屬性會套用至目前的元件模組。</span><span class="sxs-lookup"><span data-stu-id="6c68a-103">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c68a-104">備註</span><span class="sxs-lookup"><span data-stu-id="6c68a-104">Remarks</span></span>  
 <span data-ttu-id="6c68a-105">許多屬性都屬於個別的程式設計項目，例如類別或屬性。</span><span class="sxs-lookup"><span data-stu-id="6c68a-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="6c68a-106">您可以將屬性區塊（位於角括弧（`< >`）內）直接附加至宣告語句，以套用這類屬性。</span><span class="sxs-lookup"><span data-stu-id="6c68a-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="6c68a-107">如果屬性僅與下列專案有關，但對目前的元件模組不相關，您可以將屬性區塊放在原始程式檔的開頭，並使用 `Module` 關鍵字來識別該屬性。</span><span class="sxs-lookup"><span data-stu-id="6c68a-107">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="6c68a-108">如果它套用至整個元件，請使用[assembly](../../../visual-basic/language-reference/modifiers/assembly.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="6c68a-108">If it applies to the entire assembly, you use the [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="6c68a-109">`Module` 修飾詞與[Module 語句](../../../visual-basic/language-reference/statements/module-statement.md)不同。</span><span class="sxs-lookup"><span data-stu-id="6c68a-109">The `Module` modifier is not the same as the [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c68a-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="6c68a-110">See also</span></span>

- [<span data-ttu-id="6c68a-111">組件</span><span class="sxs-lookup"><span data-stu-id="6c68a-111">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)
- [<span data-ttu-id="6c68a-112">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="6c68a-112">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="6c68a-113">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="6c68a-113">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
