---
title: 類別不支援 Automation 或不支援預期的介面
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: d5b47b39742a995be6076ddc0edc17f1ec94dade
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534159"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a>類別不支援 Automation 或不支援預期的介面
您在 `GetObject` 或 `CreateObject` 函式呼叫中指定的類別沒有公開撰寫程式介面，或是您將專案從 .dll 變更為 .exe (反之亦然)。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  查看建立物件的應用程式文件，以取得此物件類別的自動化使用限制。  
  
2.  如果您將專案從 .dll 變更為 .exe (反之亦然)，則必須手動移除舊 .dll 或 .exe 的註冊。  
  
## <a name="see-also"></a>另請參閱
- [錯誤類型](../../../visual-basic/programming-guide/language-features/error-types.md)
- [告訴我們](/visualstudio/ide/talk-to-us)
