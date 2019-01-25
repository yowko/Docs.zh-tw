---
title: 預設屬性&#39;&lt;屬性名稱 1&gt&gt; &#39;預設屬性 je v konfliktu &#39; &lt;propertyname2&gt; &#39;中&#39; &lt;classname&gt; &#39;，因此應該宣告為&#39;Shadows&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 3099467fa3c5a162c13c9235fb8d55375953ba3a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521422"
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a>預設屬性&#39;&lt;屬性名稱 1&gt&gt; &#39;預設屬性 je v konfliktu &#39; &lt;propertyname2&gt; &#39;中&#39; &lt;classname&gt; &#39;，因此應該宣告為&#39;Shadows&#39;
屬性會宣告具有相同名稱做為基底類別中定義的屬性。 在此情況下，此類別中的屬性應該會遮蔽基底類別屬性。  
  
 這個訊息是一個警告。 預設會假設為`Shadows` 。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC40007  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   新增`Shadows`關鍵字來宣告或變更所宣告的屬性名稱。  
  
## <a name="see-also"></a>另請參閱
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Visual Basic 中的遮蔽功能](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
