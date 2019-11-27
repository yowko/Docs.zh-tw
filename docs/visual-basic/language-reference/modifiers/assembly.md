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
# <a name="assembly-visual-basic"></a>Assembly (Visual Basic)
指定在原始程式檔開頭的屬性會套用至整個元件。  
  
## <a name="remarks"></a>備註  
 許多屬性都屬於個別的程式設計項目，例如類別或屬性。 您可以將屬性區塊（位於角括弧（`< >`）內）直接附加至宣告語句，以套用這類屬性。  
  
 如果屬性不只與下列專案有關，但對整個元件而言，您可以將屬性區塊放在原始程式檔的開頭，並使用 `Assembly` 關鍵字來識別該屬性。 如果它適用于目前的元件模組，您可以使用[module](../../../visual-basic/language-reference/modifiers/module-keyword.md)關鍵字。  
  
 您也可以將屬性（attribute）套用至 AssemblyInfo 檔案中的元件，在此情況下，您不需要在主要原始程式碼檔案中使用屬性區塊。  
  
## <a name="see-also"></a>請參閱

- [Module \<鍵字>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)
