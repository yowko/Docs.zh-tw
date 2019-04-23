---
title: <message> 此錯誤也可能是因為混用了檔案參考和組件的專案參考 '<assemblyname>'
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 951f90a9209ff31896f4426ceb75f05b012897a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335143"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a>\<訊息 > 這個錯誤也可能是因為混用了檔案參考和組件的專案參考 '\<組件名稱 >'
\<訊息 > 這個錯誤也可能是因為混用了檔案參考和組件的專案參考 '\<組件名稱 >。 在此情況下，請嘗試更換的檔案參考 '\<assemblyfilename >' 在專案'\<projectname1 >' 的專案參考 '\<專案名稱 2> >'。  
  
 在您的專案中的程式碼存取的另一個專案，成員，但您的解決方案組態不允許 Visual Basic 編譯器解析參考。  
  
 若要存取另一個組件中定義的類型，Visual Basic 編譯器必須有該組件的參考。 這必須是單一的明確參考，不會在專案之間造成循環參考。  
  
 **錯誤 ID:** BC30971  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 決定哪些專案產生的最佳組件供專案參考。 這項決策可能會使用輕鬆存取檔案和更新頻率等準則。  
  
2. 在專案屬性中，加入包含組件之專案的參考，此組件定義所使用的類型。  
  
## <a name="see-also"></a>另請參閱

- [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)
- [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
- [針對中斷參考進行疑難排解](/visualstudio/ide/troubleshooting-broken-references)
