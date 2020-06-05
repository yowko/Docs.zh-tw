---
title: 專案層級 Imports '<qualifiedelementname>' 中指定的命名空間或類型不包含任何 Public 成員，或是找不到該命名空間或類型
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 0ee235252d69e6f77ce53b048f45e73d0969e864
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409448"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>專案層級 Imports '\<qualifiedelementname>' 中指定的命名空間或類型不包含任何 Public 成員，或是找不到該命名空間或類型
專案層級匯入 ' ' 中指定的命名空間或類型 \<qualifiedelementname> 不包含任何 public 成員，或找不到。 請確定已定義命名空間或類型，而且包含至少一個公用成員。 請確定別名名稱不包含其他別名。  
  
 專案的匯入屬性指定了找不到或未定義任何成員的包含元素 `Public` 。  
  
 *包含元素*可以是命名空間、類別、結構、模組、介面或列舉。 包含的元素包含成員，例如變數、程式或其他包含專案。  
  
 匯入的目的是要讓您的程式碼可以存取命名空間或類型成員，而不需要限定它們。 您的專案可能也需要加入命名空間或類型的參考。 如需詳細資訊，請參閱宣告專案[參考](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)中的「匯入包含元素」。  
  
 如果編譯器找不到指定的包含元素，就無法解析使用它的參考。 如果找到專案，但元素並未公開任何 `Public` 成員，則不會有任何參考成功。 在任一情況下，匯入元素都沒有意義。  
  
 您可以使用 [**專案設計**工具] 來指定要匯入的元素。 使用 [**參考**] 頁面的 [匯**入的命名空間**] 區段。 按兩下**方案總管**中的 [**我的專案**] 圖示，即可進入 [**專案設計**工具]。  
  
 **錯誤識別碼：** BC40057  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 開啟 [**專案設計**工具]，並切換至 [**參考**] 頁面。  
  
2. 在 [匯**入的命名空間**] 區段中，確認可從您的專案存取包含的元素。  
  
3. 請確認包含的元素至少會公開一個 `Public` 成員。  
  
## <a name="see-also"></a>另請參閱

- [專案設計工具，參考頁 (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
- [公開](../modifiers/public.md)
- [Visual Basic 中的命名空間](../../programming-guide/program-structure/namespaces.md)
- [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
