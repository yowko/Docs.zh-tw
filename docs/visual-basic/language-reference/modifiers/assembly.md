---
title: "組件 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
dev_langs:
- VB
helpviewer_keywords:
- Assembly modifier
- Assembly keyword
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
caps.latest.revision: 15
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
ms.openlocfilehash: b83102c24c80b7ee6ec4c0ffc4a446e26b7811cf
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="assembly-visual-basic"></a><span data-ttu-id="53c4d-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53c4d-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="53c4d-103">指定原始程式檔的開頭將屬性套用至整個組件。</span><span class="sxs-lookup"><span data-stu-id="53c4d-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53c4d-104">備註</span><span class="sxs-lookup"><span data-stu-id="53c4d-104">Remarks</span></span>  
 <span data-ttu-id="53c4d-105">許多屬性都屬於個別程式設計項目，例如類別或屬性。</span><span class="sxs-lookup"><span data-stu-id="53c4d-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="53c4d-106">藉由附加角括號內的屬性區塊套用這類屬性 (`< >`)，來宣告陳述式。</span><span class="sxs-lookup"><span data-stu-id="53c4d-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="53c4d-107">如果屬性屬於下列項目不僅整個組件，您將屬性區塊放在原始程式檔的開頭，並找出具有屬性`Assembly`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="53c4d-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="53c4d-108">適用於目前的組件模組時，如果您使用[模組](../../../visual-basic/language-reference/modifiers/module-keyword.md)關鍵字。</span><span class="sxs-lookup"><span data-stu-id="53c4d-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="53c4d-109">您也可以套用屬性至組件在 AssemblyInfo.vb 檔案中，在此情況下不需要主要原始程式檔中使用屬性區塊。</span><span class="sxs-lookup"><span data-stu-id="53c4d-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53c4d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53c4d-110">See Also</span></span>  
 <span data-ttu-id="53c4d-111">[模組\<關鍵字 >](../../../visual-basic/language-reference/modifiers/module-keyword.md) </span><span class="sxs-lookup"><span data-stu-id="53c4d-111">[Module \<keyword>](../../../visual-basic/language-reference/modifiers/module-keyword.md) </span></span>  
<span data-ttu-id="53c4d-112"> [屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)</span><span class="sxs-lookup"><span data-stu-id="53c4d-112"> [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md)</span></span>


