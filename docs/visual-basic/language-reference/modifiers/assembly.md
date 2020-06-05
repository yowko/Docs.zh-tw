---
title: 組件
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
ms.openlocfilehash: 7d313dee1015362bd0215ed98ab7e898312cfbcd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373156"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="75ff3-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75ff3-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="75ff3-103">指定在原始程式檔開頭的屬性會套用至整個元件。</span><span class="sxs-lookup"><span data-stu-id="75ff3-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75ff3-104">備註</span><span class="sxs-lookup"><span data-stu-id="75ff3-104">Remarks</span></span>  
 <span data-ttu-id="75ff3-105">許多屬性都屬於個別的程式設計項目，例如類別或屬性。</span><span class="sxs-lookup"><span data-stu-id="75ff3-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="75ff3-106">您可以將屬性區塊（位於角括弧（）內）直接附加至宣告語句，以套用這類屬性 `< >` 。</span><span class="sxs-lookup"><span data-stu-id="75ff3-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="75ff3-107">如果屬性不只與下列專案有關，但對整個元件而言，您可以將屬性區塊放在原始程式檔的開頭，並使用關鍵字來識別該屬性 `Assembly` 。</span><span class="sxs-lookup"><span data-stu-id="75ff3-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="75ff3-108">如果它適用于目前的元件模組，您可以使用[module](module-keyword.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="75ff3-108">If it applies to the current assembly module, you use the [Module](module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="75ff3-109">您也可以將屬性（attribute）套用至 AssemblyInfo 檔案中的元件，在此情況下，您不需要在主要原始程式碼檔案中使用屬性區塊。</span><span class="sxs-lookup"><span data-stu-id="75ff3-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75ff3-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75ff3-110">See also</span></span>

- [<span data-ttu-id="75ff3-111">Module\<keyword></span><span class="sxs-lookup"><span data-stu-id="75ff3-111">Module \<keyword></span></span>](module-keyword.md)
- [<span data-ttu-id="75ff3-112">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="75ff3-112">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
