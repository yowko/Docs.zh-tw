---
title: <message> 此錯誤也可能是因為混用檔案參考與組件 '<assemblyname>' 的專案參考所致
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: 9340c5c58c0cdb70c517534a339f57eb9ec1f906
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162423"
---
# <a name="bc30971-message-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-assemblyname"></a>BC30971： \<message> 這個錯誤也可能是因為混用了檔案參考和元件 ' ' 的專案參考 \<assemblyname> 。

\<message> 這個錯誤也可能是因為混用了檔案參考和元件 ' 的專案參考 \<assemblyname> 。 在此情況下，請嘗試將專案 ' ' 中的 ' ' 檔案參考取代為 \<assemblyfilename> \<projectname1> ' ' 的專案參考 \<projectname2> 。

 您專案中的程式碼會存取另一個專案的成員，但是解決方案的設定不允許 Visual Basic 編譯器解析參考。

 若要存取在另一個元件中定義的類型，Visual Basic 編譯器必須有該元件的參考。 這必須是單一的明確參考，不會在專案之間造成循環參考。

 **錯誤 ID︰** BC30971

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 決定哪些專案產生的最佳組件供專案參考。 這項決策可能會使用輕鬆存取檔案和更新頻率等準則。

2. 在專案屬性中，加入包含組件之專案的參考，此組件定義所使用的類型。

## <a name="see-also"></a>另請參閱

- [管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)
- [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
- [針對中斷參考進行疑難排解](/visualstudio/ide/troubleshooting-broken-references)
