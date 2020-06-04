---
title: 預設屬性 '<propertyname1>' 與基底 '<propertyname2>' 中的預設屬性 '<classname>' 產生衝突，所以必須宣告為 'Shadows'
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 37f98ce8120d5861552819690f9d5f22c9959a0e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409721"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a>預設屬性 '\<propertyname1>' 與基底 '\<propertyname2>' 中的預設屬性 '\<classname>' 產生衝突，所以必須宣告為 'Shadows'
使用與基類中所定義之屬性相同的名稱來宣告屬性。 在此情況下，此類別中的屬性應該遮蔽基類屬性。  
  
 這個訊息是一個警告。 預設會假設為`Shadows` 。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼：** BC40007  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將 `Shadows` 關鍵字加入至宣告，或變更所宣告之屬性的名稱。  
  
## <a name="see-also"></a>另請參閱

- [Shadows](../modifiers/shadows.md)
- [Visual Basic 中的遮蔽功能](../../programming-guide/language-features/declared-elements/shadowing.md)
