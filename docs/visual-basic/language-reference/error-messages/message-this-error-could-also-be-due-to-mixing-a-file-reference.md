---
title: <message> 此錯誤也可能是因為混用檔案參考與組件 '<assemblyname>' 的專案參考所致
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 263e30f992ef58b0053acb2fd749d0d9186ef6b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397255"
---
# <a name="message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a>\<message> 此錯誤也可能是因為混用檔案參考與組件 '\<assemblyname>' 的專案參考所致
\<message>此錯誤也可能是因為混用了檔案參考與元件 ' 的專案參考 \<assemblyname> 。 在此情況下，請嘗試將專案 ' ' 中 ' ' 的檔案參考取代為 \<assemblyfilename> \<projectname1> ' ' 的專案參考 \<projectname2> 。  
  
 專案中的程式碼會存取另一個專案的成員，但您的方案設定不允許 Visual Basic 編譯器解析參考。  
  
 若要存取另一個元件中所定義的類型，Visual Basic 編譯器必須有該元件的參考。 這必須是單一的明確參考，不會在專案之間造成循環參考。  
  
 **錯誤 ID︰** BC30971  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 決定哪些專案產生的最佳組件供專案參考。 這項決策可能會使用輕鬆存取檔案和更新頻率等準則。  
  
2. 在專案屬性中，加入包含組件之專案的參考，此組件定義所使用的類型。  
  
## <a name="see-also"></a>另請參閱

- [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)
- [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
- [針對中斷參考進行疑難排解](/visualstudio/ide/troubleshooting-broken-references)
