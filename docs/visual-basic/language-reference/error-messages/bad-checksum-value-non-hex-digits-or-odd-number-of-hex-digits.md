---
title: "總和檢查碼錯誤值，非十六進位數字或奇數的十六進位數字 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42033
- vbc42033
dev_langs:
- VB
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: bacb392b680bd236583ef6374f135678ed3304f3
ms.lasthandoff: 03/13/2017

---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a>錯誤的總和檢查碼值，非十六進位數字或奇數的十六進位數字
總和檢查碼值包含無效的十六進位數字，或是有奇數個數字。  
  
 當 ASP.NET 產生 Visual Basic 原始程式檔 (副檔名為 .vb) 時，它會計算總和檢查碼並將它放在 `#externalchecksum` 所識別的隱藏原始程式檔中。 使用者產生 .vb 檔案也可能這麼做，但這個流程最好留供內部使用。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼︰** BC42033  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  如果 ASP.NET 正在產生 Visual Basic 原始程式檔，請重新啟動專案建置。  
  
2.  如果這個警告在重新啟動之後持續發生，請重新安裝 ASP.NET 然後重試建置。  
  
3.  如果警告仍然持續發生，或您未使用 ASP.NET，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。  
  
## <a name="see-also"></a>另請參閱  
 [ASP.NET 概觀](https://msdn.microsoft.com/library/4w3ex9c2.aspx)   
 [告訴我們](https://docs.microsoft.com/visualstudio/ide/talk-to-us)
