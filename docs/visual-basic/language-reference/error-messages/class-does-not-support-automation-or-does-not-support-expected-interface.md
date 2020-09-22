---
title: 類別不支援 Automation 或不支援預期的介面
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: aa97ae420a0a289979fe86db373c635361dc6475
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874635"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a>類別不支援 Automation 或不支援預期的介面

您在 `GetObject` 或 `CreateObject` 函式呼叫中指定的類別沒有公開撰寫程式介面，或是您將專案從 .dll 變更為 .exe (反之亦然)。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 查看建立物件的應用程式文件，以取得此物件類別的自動化使用限制。  
  
2. 如果您將專案從 .dll 變更為 .exe (反之亦然)，則必須手動移除舊 .dll 或 .exe 的註冊。  
  
## <a name="see-also"></a>另請參閱

- [錯誤類型](../../programming-guide/language-features/error-types.md)
- [與我們交談](/visualstudio/ide/feedback-options)
