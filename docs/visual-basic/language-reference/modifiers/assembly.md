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
# <a name="assembly-visual-basic"></a>Assembly (Visual Basic)

指定在原始程式檔開頭的屬性會套用至整個元件。  
  
## <a name="remarks"></a>備註  

 許多屬性都屬於個別的程式設計項目，例如類別或屬性。 您可以藉由將屬性區塊（在角)  (括弧內）直接附加至宣告語句，以套用這類屬性 `< >` 。  
  
 如果屬性不只與下列專案相關，但對整個元件而言，您可以將屬性區塊放在來源檔案的開頭，並使用關鍵字來識別屬性 `Assembly` 。 如果套用至目前的元件模組，您可以使用 [module](module-keyword.md) 關鍵字。  
  
 您也可以將屬性套用至 AssemblyInfo 檔中的元件，在此情況下，您不需要在主要的原始程式碼檔中使用屬性區塊。  
  
## <a name="see-also"></a>另請參閱

- [模組 \<keyword>](module-keyword.md)
- [屬性概觀](../../programming-guide/concepts/attributes/index.md)
