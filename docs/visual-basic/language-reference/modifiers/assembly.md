---
title: Assembly (Visual Basic)
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
ms.openlocfilehash: 7ee6cddefd5955ee76510ffeb23335f05460657b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="71cc1-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71cc1-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="71cc1-103">指定的原始程式檔開頭的屬性會套用到整個組件。</span><span class="sxs-lookup"><span data-stu-id="71cc1-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71cc1-104">備註</span><span class="sxs-lookup"><span data-stu-id="71cc1-104">Remarks</span></span>  
 <span data-ttu-id="71cc1-105">許多屬性適用於個別的程式設計元素，例如類別或屬性。</span><span class="sxs-lookup"><span data-stu-id="71cc1-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="71cc1-106">您套用這類屬性所附加的屬性區塊角括號內 (`< >`)，直接至宣告陳述式。</span><span class="sxs-lookup"><span data-stu-id="71cc1-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="71cc1-107">如果屬性屬於下列項目不僅整個組件，您將屬性區塊放在原始程式檔的開頭，然後找出具有屬性`Assembly`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="71cc1-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="71cc1-108">它會套用至目前的組件模組，如果您使用[模組](../../../visual-basic/language-reference/modifiers/module-keyword.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="71cc1-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="71cc1-109">您也可以套用屬性至組件在 AssemblyInfo.vb 檔案中，在此情況下您沒有主要原始程式檔中使用屬性區塊。</span><span class="sxs-lookup"><span data-stu-id="71cc1-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71cc1-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71cc1-110">See Also</span></span>  
 [<span data-ttu-id="71cc1-111">Module \<鍵字></span><span class="sxs-lookup"><span data-stu-id="71cc1-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [<span data-ttu-id="71cc1-112">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="71cc1-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

