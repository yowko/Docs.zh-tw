---
title: 發生未預期的錯誤，因為無法取得單一執行個體啟動所需要的作業系統資源
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 8130eee93ab5c14043283c28f522da53f9047e85
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646898"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a>發生未預期的錯誤，因為無法取得單一執行個體啟動所需要的作業系統資源
應用程式無法取得必要的作業系統資源。 此問題的部分可能原因包括：  
  
- 應用程式沒有權限可建立具名的作業系統物件。  
  
- 通用語言執行平台沒有權限可建立記憶體對應檔案。  
  
- 應用程式需要存取作業系統物件，但另一個處理序正在使用它。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 檢查應用程式有足夠的權限可建立指名的作業系統物件。  
  
2. 檢查通用語言執行平台有足夠的權限可建立記憶體對應檔案。  
  
3. 重新啟動電腦，以清除可能正在使用連接到原始執行個體應用程式之所需資源的任何處理序。  
  
4. 記下錯誤發生時的情況，並致電 Microsoft 產品支援服務  
  
## <a name="see-also"></a>另請參閱

- [專案設計工具、應用程式頁面 (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [偵錯工具基礎](/visualstudio/debugger/debugger-basics)
- [告訴我們](/visualstudio/ide/talk-to-us)
