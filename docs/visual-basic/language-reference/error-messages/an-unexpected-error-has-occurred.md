---
title: "已發生意外的錯誤，因為無法取得單一執行個體啟動時所需要的作業系統資源 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
dev_langs:
- VB
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
caps.latest.revision: 10
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
ms.openlocfilehash: 44432a2c393abb01141d09cf5f28c6fd29c5bc43
ms.lasthandoff: 03/13/2017

---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a>發生未預期的錯誤，因為無法取得單一執行個體啟動所需要的作業系統資源
應用程式無法取得必要的作業系統資源。 此問題的部分可能原因包括：  
  
-   應用程式沒有權限可建立具名的作業系統物件。  
  
-   通用語言執行平台沒有權限可建立記憶體對應檔案。  
  
-   應用程式需要存取作業系統物件，但另一個處理序正在使用它。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  檢查應用程式有足夠的權限可建立指名的作業系統物件。  
  
2.  檢查通用語言執行平台有足夠的權限可建立記憶體對應檔案。  
  
3.  重新啟動電腦，以清除可能正在使用連接到原始執行個體應用程式之所需資源的任何處理序。  
  
4.  記下錯誤發生時的情況，並致電 Microsoft 產品支援服務  
  
## <a name="see-also"></a>另請參閱  
 [專案設計工具、應用程式頁面 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)   
 [偵錯工具基本概念](https://docs.microsoft.com/visualstudio/debugger/debugger-basics)   
 [告訴我們](https://docs.microsoft.com/visualstudio/ide/talk-to-us)
