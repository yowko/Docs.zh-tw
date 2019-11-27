---
title: Assembly
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 1385919a1205a60104125fff1bdd24f409a091df
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351640"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="c82c1-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c82c1-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="c82c1-103">指定在原始程式檔開頭的屬性會套用至整個元件。</span><span class="sxs-lookup"><span data-stu-id="c82c1-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c82c1-104">備註</span><span class="sxs-lookup"><span data-stu-id="c82c1-104">Remarks</span></span>  
 <span data-ttu-id="c82c1-105">許多屬性都屬於個別的程式設計項目，例如類別或屬性。</span><span class="sxs-lookup"><span data-stu-id="c82c1-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="c82c1-106">您可以將屬性區塊（位於角括弧（`< >`）內）直接附加至宣告語句，以套用這類屬性。</span><span class="sxs-lookup"><span data-stu-id="c82c1-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="c82c1-107">如果屬性不只與下列專案有關，但對整個元件而言，您可以將屬性區塊放在原始程式檔的開頭，並使用 `Assembly` 關鍵字來識別該屬性。</span><span class="sxs-lookup"><span data-stu-id="c82c1-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="c82c1-108">如果它適用于目前的元件模組，您可以使用[module](../../../visual-basic/language-reference/modifiers/module-keyword.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c82c1-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="c82c1-109">您也可以將屬性（attribute）套用至 AssemblyInfo 檔案中的元件，在此情況下，您不需要在主要原始程式碼檔案中使用屬性區塊。</span><span class="sxs-lookup"><span data-stu-id="c82c1-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c82c1-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="c82c1-110">See also</span></span>

- [<span data-ttu-id="c82c1-111">Module \<鍵字></span><span class="sxs-lookup"><span data-stu-id="c82c1-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [<span data-ttu-id="c82c1-112">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="c82c1-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
