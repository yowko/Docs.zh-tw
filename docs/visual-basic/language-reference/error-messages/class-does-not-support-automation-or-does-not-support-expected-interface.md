---
title: "類別不支援 Automation 或不支援預期的介面 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID430
dev_langs:
- VB
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
caps.latest.revision: 11
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
ms.openlocfilehash: a5bdce085c676f5c9c20932939486e879bb13a36
ms.lasthandoff: 03/13/2017

---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a>類別不支援 Automation 或不支援預期的介面
您在 `GetObject` 或 `CreateObject` 函式呼叫中指定的類別沒有公開撰寫程式介面，或是您將專案從 .dll 變更為 .exe (反之亦然)。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  查看建立物件的應用程式文件，以取得此物件類別的自動化使用限制。  
  
2.  如果您將專案從 .dll 變更為 .exe (反之亦然)，則必須手動移除舊 .dll 或 .exe 的註冊。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [告訴我們](https://docs.microsoft.com/visualstudio/ide/talk-to-us)
