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
ms.openlocfilehash: 6c4f24ad161302835be683e9d324ce32b16c4087
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867986"
---
# <a name="module-keyword-visual-basic"></a><span data-ttu-id="bb50a-102">Module \<keyword> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb50a-102">Module \<keyword> (Visual Basic)</span></span>

<span data-ttu-id="bb50a-103">指定在原始程式檔開頭的屬性會套用至目前的元件模組。</span><span class="sxs-lookup"><span data-stu-id="bb50a-103">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb50a-104">備註</span><span class="sxs-lookup"><span data-stu-id="bb50a-104">Remarks</span></span>  

 <span data-ttu-id="bb50a-105">許多屬性都屬於個別的程式設計項目，例如類別或屬性。</span><span class="sxs-lookup"><span data-stu-id="bb50a-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="bb50a-106">您可以藉由將屬性區塊（在角)  (括弧內）直接附加至宣告語句，以套用這類屬性 `< >` 。</span><span class="sxs-lookup"><span data-stu-id="bb50a-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="bb50a-107">如果屬性不只與下列專案相關，而是與目前的元件模組有關，請將屬性區塊放在來源檔案的開頭，並使用關鍵字來識別屬性 `Module` 。</span><span class="sxs-lookup"><span data-stu-id="bb50a-107">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="bb50a-108">如果套用至整個元件，則您會使用 [assembly](assembly.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bb50a-108">If it applies to the entire assembly, you use the [Assembly](assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="bb50a-109">修飾詞與 `Module` [Module 語句](../statements/module-statement.md)不同。</span><span class="sxs-lookup"><span data-stu-id="bb50a-109">The `Module` modifier is not the same as the [Module Statement](../statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb50a-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb50a-110">See also</span></span>

- [<span data-ttu-id="bb50a-111">組件</span><span class="sxs-lookup"><span data-stu-id="bb50a-111">Assembly</span></span>](assembly.md)
- [<span data-ttu-id="bb50a-112">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="bb50a-112">Module Statement</span></span>](../statements/module-statement.md)
- [<span data-ttu-id="bb50a-113">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="bb50a-113">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
