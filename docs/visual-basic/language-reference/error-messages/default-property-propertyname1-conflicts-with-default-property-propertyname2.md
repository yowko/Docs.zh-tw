---
title: "預設屬性 &quot;&lt;propertyname1&gt;&quot;衝突的預設屬性&quot;&lt;propertyname2&gt;&quot;在&quot;&lt;classname&gt;&quot;，所以必須宣告為 &quot;Shadows&quot; |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
dev_langs:
- VB
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 9
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 803b42b7659c16fd97251635e4b6ba49362e0a02
ms.lasthandoff: 03/13/2017

---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a>預設屬性 '&lt;propertyname1&gt;'衝突的預設屬性'&lt;propertyname2&gt;'在'&lt;classname&gt;'，所以必須宣告為 'Shadows'
屬性會宣告具有相同名稱做為基底類別中定義的屬性。 在此情況下，此類別中的屬性會遮蔽基底類別屬性。  
  
 這個訊息是一個警告。 `Shadows`預設會假設。 如需隱藏警告，或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼︰** BC40007  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   新增`Shadows`關鍵字來宣告或變更所宣告的屬性名稱。  
  
## <a name="see-also"></a>另請參閱  
 [陰影](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [在 Visual Basic 中，以遮蔽](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
