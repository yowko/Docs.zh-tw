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
# <a name="assembly-visual-basic"></a>Assembly (Visual Basic)
指定在原始程式檔開頭的屬性會套用至整個元件。  
  
## <a name="remarks"></a>備註  
 許多屬性都屬於個別的程式設計項目，例如類別或屬性。 您可以將屬性區塊（位於角括弧（）內）直接附加至宣告語句，以套用這類屬性 `< >` 。  
  
 如果屬性不只與下列專案有關，但對整個元件而言，您可以將屬性區塊放在原始程式檔的開頭，並使用關鍵字來識別該屬性 `Assembly` 。 如果它適用于目前的元件模組，您可以使用[module](module-keyword.md)關鍵字。  
  
 您也可以將屬性（attribute）套用至 AssemblyInfo 檔案中的元件，在此情況下，您不需要在主要原始程式碼檔案中使用屬性區塊。  
  
## <a name="see-also"></a>另請參閱

- [Module\<keyword>](module-keyword.md)
- [屬性概觀](../../programming-guide/concepts/attributes/index.md)
