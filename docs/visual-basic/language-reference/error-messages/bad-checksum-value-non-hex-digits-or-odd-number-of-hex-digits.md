---
title: 錯誤的總和檢查碼值，非十六進位數字或奇數的十六進位數字
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: e380033f9353781ee7dc86696e93c8d0f18a1a73
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162969"
---
# <a name="bc42033-bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a>BC42033：不正確的總和檢查碼值、非十六進位數位或奇數的十六進位數位

總和檢查碼值包含無效的十六進位數字，或是有奇數個數字。

 當 ASP.NET 產生 Visual Basic 原始程式檔 (副檔名為 .vb) 時，它會計算總和檢查碼並將它放在 `#externalchecksum` 所識別的隱藏原始程式檔中。 使用者產生 .vb 檔案也可能這麼做，但這個流程最好留供內部使用。

 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。

 **錯誤識別碼：** BC42033

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 如果 ASP.NET 正在產生 Visual Basic 原始程式檔，請重新啟動專案建置。

2. 如果這個警告在重新啟動之後持續發生，請重新安裝 ASP.NET 然後重試建置。

3. 如果警告仍然持續發生，或您未使用 ASP.NET，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。

## <a name="see-also"></a>另請參閱

- [ASP.NET 總覽](/aspnet/overview)
- [與我們交談](/visualstudio/ide/feedback-options)
