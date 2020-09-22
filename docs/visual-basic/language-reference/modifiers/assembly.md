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
ms.openlocfilehash: 34d6b94f31336e3e99b8ca981a9c4899e5a3d912
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875528"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="7ed81-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ed81-102">Assembly (Visual Basic)</span></span>

<span data-ttu-id="7ed81-103">指定在原始程式檔開頭的屬性會套用至整個元件。</span><span class="sxs-lookup"><span data-stu-id="7ed81-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ed81-104">備註</span><span class="sxs-lookup"><span data-stu-id="7ed81-104">Remarks</span></span>  

 <span data-ttu-id="7ed81-105">許多屬性都屬於個別的程式設計項目，例如類別或屬性。</span><span class="sxs-lookup"><span data-stu-id="7ed81-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="7ed81-106">您可以藉由將屬性區塊（在角)  (括弧內）直接附加至宣告語句，以套用這類屬性 `< >` 。</span><span class="sxs-lookup"><span data-stu-id="7ed81-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="7ed81-107">如果屬性不只與下列專案相關，但對整個元件而言，您可以將屬性區塊放在來源檔案的開頭，並使用關鍵字來識別屬性 `Assembly` 。</span><span class="sxs-lookup"><span data-stu-id="7ed81-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="7ed81-108">如果套用至目前的元件模組，您可以使用 [module](module-keyword.md) 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7ed81-108">If it applies to the current assembly module, you use the [Module](module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="7ed81-109">您也可以將屬性套用至 AssemblyInfo 檔中的元件，在此情況下，您不需要在主要的原始程式碼檔中使用屬性區塊。</span><span class="sxs-lookup"><span data-stu-id="7ed81-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ed81-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ed81-110">See also</span></span>

- [<span data-ttu-id="7ed81-111">模組 \<keyword></span><span class="sxs-lookup"><span data-stu-id="7ed81-111">Module \<keyword></span></span>](module-keyword.md)
- [<span data-ttu-id="7ed81-112">屬性概觀</span><span class="sxs-lookup"><span data-stu-id="7ed81-112">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
