---
title: 預設屬性 '<propertyname1>' 與基底 '<propertyname2>' 中的預設屬性 '<classname>' 產生衝突，所以必須宣告為 'Shadows'
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 290971a3173c59f08fbd279b6fffe3bcb618cb72
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160603"
---
# <a name="bc40007-default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a>BC40007：預設屬性 ' \<propertyname1> ' 與 ' ' 中的預設屬性 ' \<propertyname2> ' 衝突 \<classname> ，所以應該宣告為 ' Shadows '

宣告屬性時所使用的名稱，與基類中所定義的屬性相同。 在此情況下，這個類別中的屬性應該會遮蔽基類屬性。

 這個訊息是一個警告。 預設會假設為`Shadows` 。 如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。

 **錯誤識別碼：** BC40007

## <a name="to-correct-this-error"></a>更正這個錯誤

- 將 `Shadows` 關鍵字加入至宣告，或變更所宣告的屬性名稱。

## <a name="see-also"></a>另請參閱

- [陰影](../modifiers/shadows.md)
- [Visual Basic 中的遮蔽功能](../../programming-guide/language-features/declared-elements/shadowing.md)
