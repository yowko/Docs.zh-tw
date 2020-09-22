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
# <a name="module-keyword-visual-basic"></a>Module \<keyword> (Visual Basic)

指定在原始程式檔開頭的屬性會套用至目前的元件模組。  
  
## <a name="remarks"></a>備註  

 許多屬性都屬於個別的程式設計項目，例如類別或屬性。 您可以藉由將屬性區塊（在角)  (括弧內）直接附加至宣告語句，以套用這類屬性 `< >` 。  
  
 如果屬性不只與下列專案相關，而是與目前的元件模組有關，請將屬性區塊放在來源檔案的開頭，並使用關鍵字來識別屬性 `Module` 。 如果套用至整個元件，則您會使用 [assembly](assembly.md) 關鍵字。  
  
 修飾詞與 `Module` [Module 語句](../statements/module-statement.md)不同。  
  
## <a name="see-also"></a>另請參閱

- [組件](assembly.md)
- [Module 陳述式](../statements/module-statement.md)
- [屬性概觀](../../programming-guide/concepts/attributes/index.md)
